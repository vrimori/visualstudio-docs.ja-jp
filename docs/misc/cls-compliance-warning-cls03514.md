---
title: "CLS 準拠の警告 CLS03514 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS03514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03514"
ms.assetid: b2d326ce-8c1b-4351-80d1-ccd1818b1ea3
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS03514
CLS には、公開されている必須修飾子 \(modreq\) は使用できず、この修飾子では認識しないオプション修飾子 \(modopt\) は使用できます  
  
 CLS には、公開されている必須修飾子 \(modreq\) は使用できず、この修飾子では認識しないオプション修飾子 \(modopt\) は使用できます。  
  
 デリゲート シグネチャに、公開されている必須修飾子でマークされた型が含まれていないことを確認します。  
  
 共通言語サブセット \(CLS\) 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS03514 が生成されます。  
  
```  
// CLS03514.cpp // compile with: /clr /LD // CLS03514 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyDel(volatile Int32 param);   // CLS03514 public delegate void MyDel2(Int32 param);   // OK  
```