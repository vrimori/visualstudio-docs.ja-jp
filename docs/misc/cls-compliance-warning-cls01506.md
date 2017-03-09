---
title: "CLS 準拠の警告 CLS01506 | Microsoft Docs"
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
  - "CLS01506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01506"
ms.assetid: 030f1b81-1159-4057-9fee-8721a419a5d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01506
varargs 制約は CLS の一部ではありません  
  
 varargs 制約は、共通言語サブセット \(CLS\) の一部ではありません。  CLS でサポートされる呼び出し規約のみが、標準のマネージ呼び出し規約です。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 \(MSIL アセンブリ言語を使用した\) 次の関数宣言では、CLS01506 の考えられる原因を示しています。  
  
```  
.method public instance vararg void  Method1() cil managed  
```  
  
 **vararg** キーワードを削除することで、この警告を解決することができます。  
  
```  
.method public instance void  Method1() cil managed  
```