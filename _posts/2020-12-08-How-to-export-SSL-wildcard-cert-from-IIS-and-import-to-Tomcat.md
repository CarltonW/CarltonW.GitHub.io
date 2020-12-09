---
layout: post
title: "How to export SSL Wildcard Certificate from IIS and import to Tomcat"
excerpt: "This is how I was able to export my IIS wildcard certificate and use it on Tomcat."
tags: [howto,IIS,export,tomcat,wildcard,certificate,import]
comments : true
date: 2020-12-08 19:32:20 +0300
categories: [Tomcat]
---

If you've exported your IIS certificate to use on another Windows server no big deal, right? Have you ever tried to use that same exported wildcard certification on a Tomcat server? In this post I will try to piece together the steps I used to get my exported certificate working on Tomcat. 


>### Exporting the SSL Certificate from IIS <i>(you can skip these steps if you've already created the .pfx)</i>
>
>#### First we need to export the SSL Cert from IIS into pfx format<br>
>Open the search window or open powershell and type in <b>mmc</b> and hit <b>enter</b><br>
>From the <b>Microsoft Management Console (MMC)</b>, click <b>File</b> then <b>Add/Remove Snap-in</b><br>
>Choose <b>Certificates</b> and click <b>Add</b><br>
>Choose <b>Computer Account</b> then <b>Next</b><br>
>Leave Computer as <b>Local computer</b> and choose <b>Finish</b><br>
>Now hit <b>OK</b>
>
>Now that we have the console setup for viewing certificates let's open the cert we need to export.<br>
>Under our Certificates (Local Computer) open Personal then Certificates<br>
>Find the wildcard ssl certificate you want to export and Right mouse-click it<br>
>Choose All Tasks then Export...<br>
>Next<br>
>Choose "Yes, export the private key"<br>
>Next<br>
>Leave default "Personal Information Exchange - PKCS #12 (.PFX) <br>
>Also make sure "Include all certificates in the certification path if possible"<br>
>Next<br>
>The Security screen allows you to specify the password for the key.<br>
>Choose the Password checkbox and type in a password and confirm (make sure you don't forget this password. You'll need it later)<br>
>Next<br>
>Specify a filename for the exported key and leave the format .pfx<br>
>Save<br>
>Next<br>
>Finish<br>

You just completed the hardest part. Now all we have to do is include the new key in one of Tomcat's xml files.

