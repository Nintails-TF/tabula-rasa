---
title: Who Am I
date modified: Friday, May 17th 2024, 7:11:25 pm
---

We have a Word file placed on one of our machines by a cyber attacker. Who is the author of the document?

Flag format - `byuctf{Author Name}`
***
We can extract the word document into chunks by converting it into a zip, then extracting it:
```
cp Who-Am-I.docx Who-am-I.zip
unzip Who-am-I.zip
```

The first thing we can do is to grep and look for any occurrences of name:

```
grep -r "name" Who-Am-I
```
No dice.

But we can look inside the **docProps** directory, since it often contains the meta-data of the document. We can grep this for anything relating to a creator:

```
grep -r "creator" docProps
...SNIP...
<dc:creator>Ryan Sketchy</dc:creator>
```

Thanks to this [stackoverflow question.](https://stackoverflow.com/questions/40239129/readout-properties-of-a-ms-word-document-on-a-linux-system) As it told me the syntax for who the document writer/creator/author is.

