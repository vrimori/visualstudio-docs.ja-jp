---
title: "CLS 準拠の警告 CLS01512 | Microsoft Docs"
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
  - "CLS01512"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01512"
ms.assetid: 15822eb3-43b1-4d58-a22d-9532e5820008
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01512
varargs 制約は CLS の一部ではありません  
  
 varargs 制約は、共通言語サブセット \(CLS\) の一部ではありません。  CLS でサポートされる呼び出し規則のみが、標準のマネージ呼び出し規則です。  
  
 CLS 準拠の確認について詳しくは、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」をご覧ください。  
  
 \(MSIL アセンブリ言語を使用した\) 次の関数の宣言では、CLS01512 の考えられる原因を示しています。  
  
```  
.method public specialname rtspecialname static vararg void  .cctor() cil managed  
```  
  
 **vararg** キーワードを削除することで、この警告を解決できます。  
  
```  
.method public specialname rtspecialname static void  .cctor() cil managed  
```