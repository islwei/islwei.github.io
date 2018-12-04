---
layout: post
title:  "修改或者移除Visual Studio 2017的激活序列号"
categories: VisualStudio
tags:  technology
author: Elijah
---

* content
{:toc}

网上随便找了一个VS2017的激活key，成功的激活了VS2017，但是由于公司的要求，只允许使用正版激活序列号，所以尝遍各种方式去移除或者更换序列号：




- Repair
- Uninstall 然后 Install
- InstallCleanup之后 再次Uninstall 然后 Install

打开VS之后还是显示已经激活。。。。。
已经打算重做OS，看到了修改注册表的帖子，试了一下。的确好用。
记录、分享出来！

## Change The Key

Setting new product key with StorePID.exe (MS Docs).
* navigate to VS 2017 installation directory 
(C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE)
* start cmd as admin
* execute StorePID.exe <your_new_product_key> <MPC>
* maybe a restart

Possible Microsoft Product Codes (MPC) are:
* `08860` Visual Studio Enterprise 2017
* `08862` Visual Studio Professional 2017
* `08866` Visual Studio Test Professional 2017


## Remove The Key

* open register editor
* navigate to HKEY_CLASSES_ROOT\Licenses\5C505A59-E312-4B89-9508-E162F8150517 and delete it
* exeute a repair installation of VS 2017 （Or restart your VS）
* enter your new product key under Help > Register Product

BTW,For VS 2015, the key of register is
HKEY_CLASSES_ROOT\Licenses\4D8CFBCB-2F6A-4AD2-BABF-10E28F6F2C8F

## Note
Forward From [stackoverflow](https://stackoverflow.com/questions/46731291/how-to-change-visual-studio-2017-license-key)
