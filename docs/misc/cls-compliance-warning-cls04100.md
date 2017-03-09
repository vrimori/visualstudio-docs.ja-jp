---
title: "CLS 準拠の警告 CLS04100 | Microsoft Docs"
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
  - "CLS04100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04100"
ms.assetid: a77cb26c-2546-473b-90da-41775289fc04
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS04100
属性の型が 'System::Attribute' であるか、それから継承する必要がある  
  
 CLS に準拠するには、カスタム属性は System::Attribute から継承する必要があります。  
  
 共通言語サブセット \(CLS\) 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 \(MSIL アセンブリ言語を使用した\) 次の宣言では、CLS04100 の考えられる原因を示しています。  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 属性が System::Attribute から派生すると、警告が解決されます。  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```