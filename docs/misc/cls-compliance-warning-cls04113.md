---
title: "CLS 準拠の警告 CLS04113 | Microsoft Docs"
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
  - "CLS04113"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04113"
ms.assetid: 628f56bf-5f2f-4245-b4fd-02d4605a901c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS04113
**属性の型は 'System::Attribute' であるか、それから継承する必要があります**  
  
 CLS に準拠するには、カスタム属性は System::Attribute から継承する必要があります。  
  
 共通言語サブセット \(CLS\) 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」をご覧ください。  
  
 MSIL アセンブリ言語を使用した次の宣言で、CLS04100 の考えられる原因を示します。  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 警告を解決するには、属性が System::Attribute から派生するようにします。  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```