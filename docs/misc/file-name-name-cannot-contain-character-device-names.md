---
title: "File name &lt;name&gt; cannot contain character device names. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0077"
  - "vs.message.VB_E_TERRFILECHARDEVINVALID"
ms.assetid: bb6e2e7a-1387-49be-927e-1dbbcafb65b1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# File name &lt;name&gt; cannot contain character device names.
このエラーが発生するのは一般的に、入力したファイル名が実際にキャラクター デバイス名である場合です。  キャラクター デバイス名には、CON、PRN、AUX、CLOCK$、NUL、LPT1、LPT2、COM1、COM2、COM3、COM4 などがありますが、これ以外にもあります。  
  
### このエラーを解決するには  
  
1.  別のファイル名を入力します。  
  
## 参照  
 [NIB: Save File As Dialog Box](http://msdn.microsoft.com/ja-jp/22380a20-2858-4391-b2f2-80c6bce64f14)   
 [ソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)