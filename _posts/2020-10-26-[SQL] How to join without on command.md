---
title: "[SQL] How to join without on command"
date: 2020-10-26 17:29:00
categories: jekyll update
---
How to join without on command?<br>
You can do it like below.<br>
We can't join without on command so, we should find other query<br>
So I did like below. Let you watch that steps.
```
alter table itsm.itsm_eqpm_info drop seq
alter table itsm.itsm_eqpm_info add seq integer default nextval('itsm.seq_eqpm') -- first step add seq column 

insert into itsm.itsm_eqpm_info(hostid) -- second step insert column
select hostid from itsm.ift_hosts

alter table itsm.itsm_svc_info drop seq -- do third step like first step
alter table itsm.itsm_svc_info add seq integer default nextval('itsm.seq_svc')
```

Let you update like that below
```
update itsm.itsm_eqpm_info as eqpm -- you should use table alias
set std_cd = svc_temp.std_cd, -- don't use table alias
ustd_cd = svc_temp.ustd_cd
from
(select eqpm.hostid, svc.std_cd, svc.ustd_cd
from itsm.itsm_eqpm_info eqpm
inner join itsm.itsm_svc_info svc
on eqpm.seq = svc.seq) as svc_temp
where eqpm.hostid = svc_temp.hostid -- use table alias because, column name is ambigous
```