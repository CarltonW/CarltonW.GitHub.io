---
layout: post
title: "How to export SSL Wildcard Certificate from IIS and import to Tomcat"
excerpt: "This is how I was able to export my IIS wildcard certificate and use it on Tomcat."
tags: [howto,IIS,export,tomcat,wildcard,certificate,import]
comments : true
date: 2020-02-08 19:32:20 +0300
categories: [Tomcat]
---

If you've exported your IIS certificate to use on another Windows server no big deal, right? Have you ever tried to use that same exported wildcard certification on a Tomcat server? Not as easy, was it? In this post I will try to piece together the steps I used to get my exported certificate working on Tomcat. 

### Exporting the SSL Certificate from IIS

Open the search window or open powershell and type in "mmc" and <return>
From the Microsoft Management Console (MMC), click File then Add/Remove Snap-in
