---
title: "[SQL]How to make zerofill in postgresql."
date: 2020-10-26 15:14:00
categories: jekyll update
---
How to make zerofill data in postgresql
You can make it like below
```
do $$
begin
for r in 1..146 loop
insert into itsm.itsm_svc_info(ustd_cd)
values('AG'||lpad((r*100)::text,5,'0'));
end loop;
end;
$$;
```
Let you Focus to the lpad function
that function can be maden as zerofill data so, if you wanna make zerofill data, use like that.