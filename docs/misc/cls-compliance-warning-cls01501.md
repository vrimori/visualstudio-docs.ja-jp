---
title: "CLS 準拠の警告 CLS01501 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01501"
ms.assetid: 74361331-3773-48d5-8508-0113f5464a75
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01501
**varargs 制約は CLS の一部ではありません**  
  
 varargs 制約は、共通言語サブセット \(CLS\) の一部ではありません。  CLS でサポートされる呼び出し規約のみが、標準のマネージ呼び出し規約です。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 \(MSIL アセンブリ言語を使用した\) 次の関数の宣言では、CLS01501 の考えられる原因を示しています。  
  
```  
.method public specialname rtspecialname instance vararg void  .ctor() cil managed  
```  
  
 パラメーター配列を使用して CLS01501 を解決できます。  詳細については、「[Variable Argument Lists \(...\) \(C\+\+\/CLI\)](/visual-cpp/windows/variable-argument-lists-dot-dot-dot-cpp-cli)」を参照してください。