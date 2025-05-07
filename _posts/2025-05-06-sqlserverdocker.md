---
layout: post
title:  "SQL Server on Docker"
---
**SQL Server on Docker Via Ubuntu**

<h1>Pull Down the Docker Image and Run</h1>
<pre>
  <code>
   docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Justatest123' -p 1433:1433 --name sql-server -d mcr.microsoft.com/mssql/server:2022-latest
  </code>
</pre>
<h1>Get the Microsoft sqlcmd Tools</h1>
<pre>
  <code>
  curl https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc
  curl https://packages.microsoft.com/config/ubuntu/22.04/prod.list | sudo tee /etc/apt/sources.list.d/mssql-release.list
  sudo apt-get update
  sudo apt-get install mssql-tools18 unixodbc-dev
  echo 'export PATH="$PATH:/opt/mssql-tools18/bin"' >> ~/.bash_profile
  source ~/.bash_profile
  sqlcmd -S tcp:127.0.0.1,1433
  </code>
</pre>
<h1>Download the Azure Data Studio for Ubuntu</h1>
<pre>
  <code>
  https://learn.microsoft.com/en-us/azure-data-studio/
  sudo dpkg -i ./azuredata*.deb
  azuredatastudio
  </code>
</pre>
<h1>Create a table</h1>
<pre>
  <code>
  CREATE TABLE [dbo].[Butterflies] (
    [Id]                      INT            IDENTITY (1, 1) NOT NULL,
    [Common_Name]             NVARCHAR (50)  NOT NULL,
    [Scientific_Name]         NVARCHAR (MAX) NULL,
    [Family]                  NVARCHAR (50)  NULL,
    [Subfamily]               NVARCHAR (50)  NULL,
    [Genus]                   NVARCHAR (50)  NULL,
    [Species]                 NVARCHAR (50)  NULL,
    [Wingspan_mm]             INT            NULL,
    [Primary_color]           NVARCHAR (MAX) NULL,
    [Habitat]                 NVARCHAR (MAX) NULL,
    [Geographic_Distribution] NVARCHAR (MAX) NULL,
    [Conservation_Status]     NVARCHAR (50)  NULL,
    [Notes]                   NVARCHAR (MAX) NULL,
    CONSTRAINT [PK_Butterflies] PRIMARY KEY CLUSTERED ([Id] ASC)
  );
  </code>
</pre>
<img src="{{ site.url }}{{ site.baseurl }}/assets/image-5.png" alt="">