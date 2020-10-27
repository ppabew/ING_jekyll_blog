---
title: "[SQL] How to extract number data from character data"
date: 2020-10-27 00:00:00
categories: jekyll update
---
How to extract number data from character data?<br>
Let you see below code<br>
```
select (((regexp_matches(std_cd,'[0-9]+'))[1])::integer)%2 from itsm.itsm_svc_Info
```
We can extract as regexp_matches and regular expression what to extract number data from character data<br>
And this code divides number data that we extracted from character data.<br>
Let's see ::integer. that code casts text to number so, if you divide number, you sould cast that text data.