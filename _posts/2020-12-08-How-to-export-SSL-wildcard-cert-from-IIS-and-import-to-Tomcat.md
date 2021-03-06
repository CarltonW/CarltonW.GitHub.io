---
layout: post
title: "How to export SSL Wildcard Certificate from IIS and import to Tomcat"
excerpt: "This is how I was able to export my IIS wildcard certificate and use it on Tomcat."
tags: [howto,IIS,export,tomcat,wildcard,certificate,import,keytool,pks]
comments : true
modified: 2020-12-10 08:39:00 -0600
categories: [Tomcat]
---

##### If you've exported your IIS certificate to use on another Windows server no big deal, right? Have you ever tried to use that same exported wildcard certification on a Tomcat server? In this post I will try to piece together the steps I used to get my exported certificate working on Tomcat. 


>### Exporting the SSL Certificate from IIS _(you can skip these steps if you've already created the .pfx)_
>
>#### First we need to export the SSL Cert from IIS into pfx format<br>
>Open the search window or open powershell and type in <b>mmc</b> and hit <b>enter</b><br>
>From the <b>Microsoft Management Console (MMC)</b>, click <b>File</b> then <b>Add/Remove Snap-in</b><br>
>Choose <b>Certificates</b> and click <b>Add</b><br>
>Choose <b>Computer Account</b> then <b>Next</b><br>
>Leave Computer as <b>Local computer</b> and choose <b>Finish</b><br>
>Now hit <b>OK</b>
>
>#### Now that we have the console setup for viewing certificates let's open the cert we need to export.<br>
>Under our <b>Certificates (Local Computer)</b> open <b>Personal</b> then <b>Certificates</b><br>
>Find the wildcard ssl certificate you want to export and Right mouse-click the certificate<br>
>Choose <b>All Tasks</b> then <b>Export...</b><br>
><b>Next</b><br>
>Choose <b>Yes, export the private key</b><br>
><b>Next</b><br>
>Leave default <b>Personal Information Exchange - PKCS #12 (.PFX)</b><br>
>Also make sure <b>Include all certificates in the certification path if possible</b> is checked<br>
><b>Next</b><br>
>The Security screen allows you to specify the password for the key.<br>
>Choose the <b>Password checkbox</b> and type in a password and confirm _(make sure you don't forget this password. You'll need it later)_<br>
><b>Next</b><br>
>Specify a filename for the exported key and leave the format .pfx<br>
><b>Save</b><br>
><b>Next</b><br>
><b>Finish</b><br>

##### You've just completed the hardest part. Now all we have to do is include the new key in one of Tomcat's xml files. From here we'll need to copy the newly created pfx file to the server where we have tomcat running then modify the server.xml file under the tomcat folder.

>### Using new pfx certificate with Tomcat
>
>Copy newly created pfx key to a place we have access on the Tomcat server, but isn't publicly accessible.<br>
>example: _c:\mycerts\myexportedcert.pfx_<br>
>Find the server.xml file for your webserver. _(Mine is located under c:\Program Files\Apache Software Foundation\Tomcat9\conf)_<br>
>Make a copy of Server.xml before you edit the original _(just in case!)_<br>
>Open Server.xml in notepad or another editing program<br>

Look for the section that looks like this:
```
<Connector  port="8080" protocol="HTTP/1.1"
connectionTimeout="20000" />
```

Change it to look like this:
```
<Connector port="443" protocol="HTTP/1.1" SSLEnabled="true"  
maxThreads="150" scheme="https" secure="true"  
clientAuth="false" sslProtocol="TLS"  
keystoreFile="c:\mycerts\yourcertname.pfx"  
keystoreType="PKCS12"  
keystorePass="your_password" />
```

>#### If you have a requirement to use a jks key you can convert the pfx key _(optional)_
>
>In order to convert the exported pfx key to jks format we need to use the java keytool command.<br>
>Locate keytool.exe _(mine was located in c:\program files\Java\jre\bin)_ <br>


Run the following command:
```
"c:\program files\java\jre\bin\keytool.exe" -importkeystore -srckeystore c:\mycerts\yourcertname.pfx -destkeystore c:\mycerts\newkeyname.jks
```

>You'll be prompted for a new keystore password for the jks file.<br>
>After you've entered the new keystore password you'll be required to enter the password for the existing pfx file _(hope you remembered it!)_

Now you can replace the pfx file with your new jks in the Connector section of the Server.xml file:<br>
```
<Connector port="443" protocol="HTTP/1.1" SSLEnabled="true"  
maxThreads="150" scheme="https" secure="true"  
clientAuth="false" sslProtocol="TLS"  
keystoreFile="c:\mycerts\yourcertname.jks"  
keystoreType="PKCS12"  
keystorePass="your_password" />
```
<br>
<br>
#### In this post we exported the existing wildcard SSL certification, copied it over to our Tomcat server and used it in our Server.xml config file. We also went through the steps to convert our pfx to a jks in the event your config does not allow pfx format.

Good luck and let me know if this helped.
 





