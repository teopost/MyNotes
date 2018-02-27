Comma separated values
---

```sql
SET COLSEP ','
SET PAGESIZE 50000
SET TRIMSPOOL ON
SET ECHO OFF
SET LINESIZE 5000
SET FEEDBACK OFF
SET SQLPROMPT ''
SET HEADING OFF
SET HEADSEP OFF
set underline off --remove the dashes/underlines under the col headers
SET NEWPAGE NONE
SET VERIFY OFF

--- Compose  header
SELECT
'ORDER_ID',
'PROMO_CODE',
......
FROM DUAL;

<<paste query here>>>

```

html output
---

```sql
set pages 1200
SET PAGESIZE 50000
set lines 1000
set feed off markup html on spool on
spool RAY-BAN_Weekly_Return_Report_CH.html
<<paste query here>>>
...
```sql



Installare cx_Oracle su RHEL 6.9
---
1. Verify python version, oracle versione and architecture (x86/amd64)
2. Download rpm from: https://pypi.python.org/pypi/cx_Oracle/5.3
3. Install rpm -ivh cx_Oracle-5.3-12c-py26-2.x86_64.rpm

