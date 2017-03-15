---
title: "CLS 準拠の警告 CLS04111 | Microsoft Docs"
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
  - "CLS04111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04111"
ms.assetid: 4b445ce7-d823-4cf3-b971-1c181be5fa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS04111
属性の型が 'System::Attribute' であるか、それから継承する必要がある  
  
 CLS に準拠するには、カスタム属性は System::Attribute から継承する必要があります。  System::Attribute から継承しなかった属性を型に適用しました。  
  
 \(MSIL アセンブリ言語を使用した\) 次の宣言では、CLS04111 の考えられる原因を示しています。  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 属性が System::Attribute から派生すると、警告が解決されます。  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```