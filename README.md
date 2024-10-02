# pdb-assignment
this was about creating pluggable databases those are the codes 


## we first log in like that so we can be having all the privileges that will permit us to create the PDB efficiently and smoothly

sqlplus sys/12345678@localhost:1521/xe AS SYSDBA

## Run the following command to create a new pluggable database named as specified below: 

CREATE PLUGGABLE DATABASE plsql_class2024db
  2  FROM XEPDB1
  3  FILE_NAME_CONVERT =
  4  ('C:\app\USER\product\21c\oradata\XE\XEPDB1',
  5  'C:\app\USER\product\21c\oradata\XE\XEPDB1\ plsql_class2024db\');
## nb: you use the location that you own on your computer!

## this code help us to ensure that the PDB  was created and stored in our container

show pdbs;

## this code helps us to ensure that the PDB is open hence making it easy to instore users 

ALTER PLUGGABLE DATABASE plsql_class2024db OPEN;

## this code helps us to maintain the opened state so we can add users 

ALTER PLUGGABLE DATABASE plsql_class2024db SAVE STATE;
 

ALTER SESSION SET CONTAINER=plsql_class2024db;

## this code helps us to set up(create) a user having the password identiied below "admin"

CREATE USER in_plsqlauca IDENTIFIED BY admin;

## this code hlps us to grant privileges to the user we just created above so to help him/her to access some services 

GRANT ALL PRIVILEGES TO in_plsqlauca;

## Task 2
 this was pretty the same as above creating a PDB with the speciied name

SQL> CREATE PLUGGABLE DATABASE in_to_delete_pdb
  2  FROM XEPDB1
  3  FILE_NAME_CONVERT =
  4  ('C:\app\USER\product\21c\oradata\XE\XEPDB1',
  5  'C:\app\USER\product\21c\oradata\XE\XEPDB1\ in_to_delete_pdb\');

  
## After creating the PDB, you need to open it and this will show you if it was created (pdb)

SQL> SELECT name, open_mode FROM v$pdbs;


## Next, unplug the PDB. This operation will create an XML file that stores metadata about the PDB.

ALTER PLUGGABLE DATABASE in_to_delete_pdb UNPLUG INTO 'C:\app\
USER\product\21c\oradata\XE\in_to_delete_pdb.xml';


## Now that the PDB is unplugged, you can drop it. By default, this command will only drop the PDB's metadata. To remove all the associated data files, use the INCLUDING DATAFILES option.

DROP PLUGGABLE DATABASE in_to_delete_pdb INCLUDING DATAFILES;

## You can verify that the PDB has been successfully deleted by running:

 SELECT name FROM v$pdbs;


