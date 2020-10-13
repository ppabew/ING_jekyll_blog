---
title: "[SQL]upsert 코드"
date: 2020-10-13 09:21:00
categories: jekyll update
---
upsert 
```
WITH info(
  ID,
  NAME,
  NUMBER,
  ADRESS) 
AS (
  SELECT
  #{id} as ID,
  #{name} as NAME,
  #{number} as NUMBER,
  #{adress} as ADRESS),
upsert AS(
  UPDATE
    user.USER_INFO
  SET
    ID = #{id},
    NAME = #{name},
    NUMBER = #{number},
    ADRESS = #{adress}
  WHERE
    ID = {id}
   RETURNING *)
INSERT INTO
  user.USER_INFO(
    ID,
    NAME,
    NUMBER,
    ADRESS)
  SELECT
    ID,
    NAME,
    NUMBER,
    ADRESS
  FROM
    info
  WHERE NOT EXISTS(
    SELECT
      ID,
      NAME,
      NUMBER,
      ADRESS
    FROM
      upsert)
```

