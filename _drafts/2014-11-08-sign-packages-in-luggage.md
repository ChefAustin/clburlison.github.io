---
layout: post
title: "Sign Packages in Luggage"
date: 2014-11-08
modified:
categories: 
excerpt:
comments: true
published: true
tags: []
image:
  feature:
---

Are you an Apple Developer? Most of the Apple Admin Community have developer accounts for the simply reason of having access to beta software releases earlier. This gives us more time to test software before it ends up in the hands of our users.

As of October 24th, commit [4d270a0](https://github.com/unixorn/luggage/commit/4d270a0dbc5f31bebbf9672d4a2970ad6316c8b4) of the Luggage project PKGBUILD=1 is the default for building packages. Before this change luggage created packages using an outdated packagemaker binary. 



#Pkgbuild vs PackageMaker

 makefiles using postflight scripts now must be changed to postinstall?

---

Articles:  
[Productsign](https://groups.google.com/forum/?fromgroups#!topic/the-luggage/9WeNMBcvKjA),  
[Luggage](https://github.com/unixorn/luggage),  
[Pkgbuild vs PackageMaker](https://groups.google.com/forum/?fromgroups#!topic/the-luggage/aCU9nNsMUaE)