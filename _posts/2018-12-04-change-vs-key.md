---
layout: post
title:  "Change Or Remove the License Key of Visual Studio 2017"
categories: VisualStudio
tags:  technology
author: Elijah
---

* content
{:toc}

## Change The Key

Setting new product key with StorePID.exe (MS Docs).
1、navigate to VS 2017 installation directory 
(C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE)
2、start cmd as admin
3、execute StorePID.exe <your_new_product_key> <MPC>
4、maybe a restart

```md
Possible Microsoft Product Codes (MPC) are:

* `08860` Visual Studio Enterprise 2017
* `08862` Visual Studio Professional 2017
* `08866` Visual Studio Test Professional 2017
```

## Remove The Key

1、open register editor
2、navigate to HKEY_CLASSES_ROOT\Licenses\5C505A59-E312-4B89-9508-E162F8150517 and delete it
3、exeute a repair installation of VS 2017 （Or restart your VS）
4、enter your new product key under Help > Register Product

BTW,For VS 2015, a key is
HKEY_CLASSES_ROOT\Licenses\4D8CFBCB-2F6A-4AD2-BABF-10E28F6F2C8F

## Note
Forward From [stackoverflow](https://stackoverflow.com/questions/46731291/how-to-change-visual-studio-2017-license-key)
