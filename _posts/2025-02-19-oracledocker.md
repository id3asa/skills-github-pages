---
layout: post
title:  "Oracle Express on Docker"
---
**Oracle Express on Docker**

<img src="/assets/circuit-board-6522555_1280.png" alt="circuit logo" style="height: 50px;"/>&nbsp;The following docker command can be used to run Oracle Express in Docker:

<pre>
  <code>
    docker run -d --name oracledb --hostname oracledbhost --network=oracledb-network -p 1522:1521 container-registry.oracle.com/database/express:latest
  </code>
</pre>