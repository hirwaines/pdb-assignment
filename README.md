# pdb-assignment
this was about creating pluggable databases those are the codes 

sqlplus sys/12345678@localhost:1521/xe AS SYSDBA

CREATE PLUGGABLE DATABASE plsql_class2024db
  2  FROM XEPDB1
  3  FILE_NAME_CONVERT =
  4  ('C:\app\USER\product\21c\oradata\XE\XEPDB1',
  5  'C:\app\USER\product\21c\oradata\XE\XEPDB1\ plsql_class2024db\');


show pdbs;

ALTER PLUGGABLE DATABASE plsql_class2024db OPEN;

ALTER PLUGGABLE DATABASE plsql_class2024db SAVE STATE;

ALTER SESSION SET CONTAINER=plsql_class2024db;

CREATE USER in_plsqlauca IDENTIFIED BY admin;

GRANT ALL PRIVILEGES TO in_plsqlauca;

Task 2


SQL> CREATE PLUGGABLE DATABASE in_to_delete_pdb
  2  FROM XEPDB1
  3  FILE_NAME_CONVERT =
  4  ('C:\app\USER\product\21c\oradata\XE\XEPDB1',
  5  'C:\app\USER\product\21c\oradata\XE\XEPDB1\ in_to_delete_pdb\');


SQL> SELECT name, open_mode FROM v$pdbs;

ALTER PLUGGABLE DATABASE in_to_delete_pdb UNPLUG INTO 'C:\app\
USER\product\21c\oradata\XE\in_to_delete_pdb.xml';

DROP PLUGGABLE DATABASE in_to_delete_pdb INCLUDING DATAFILES;


 SELECT name FROM v$pdbs;


