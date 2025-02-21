---
layout: post
title:  "Oracle Express on Docker"
---
**Oracle Express on Docker**

{% include image.html post=page.path file="circuit-board-6522555_1280.png" %}&nbsp;The following docker command can be used to run Oracle Express in Docker:

<pre>
  <code>
    docker run -d --name oracledb --hostname oracledbhost --network=oracledb-network -p 1522:1521 container-registry.oracle.com/database/express:latest
  </code>
</pre>

After running this command, you will need to do a hard reset on the password.

<pre>
  <code>
    docker exec oracledb ./setPassword.sh augmented5
  </code>
</pre>

Then login with sqlplus (or sqlplus64) and do your stuff.

<pre>
  <code>
    sqlplus64 sys/augmented5@//localhost:1522/XE as sysdba
  <code>
<pre>

From within SQL*Plus, create a user (schema) to hold come demo data.

<pre>
  <code>
    alter session set container=XEPDB1;
    create user JWICK identified by blueSpruce88;
    grant dba, resource, connect to JWICK;
    ALTER USER JWICK DEFAULT ROLE CONNECT;
  <code>
<pre>

Exit SQL*Plus...The connect string to attach to the running Oracle database based upon the user above is as follows (change to your oracledb ip):

<pre>
  <code>
    export CONN_STRING=JWICK/blueSpruce88@172.18.0.2:1521/XEPDB1
  <code>
<pre>

Check this: 

<pre>
  <code>
    sqlplus64 JWICK/blueSpruce88@172.18.0.2:1521/XEPDB1
  <code>
<pre>

Now create your tables and demo data.
    

