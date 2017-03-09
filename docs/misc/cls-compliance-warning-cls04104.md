---
title: "CLS 準拠の警告 CLS04104 | Microsoft Docs"
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
  - "CLS04104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04104"
ms.assetid: 89a5c080-c7f3-48b5-b2ff-90aa2236c90e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS04104
属性の型は 'System::Attribute' であるか、それから継承する必要があります  
  
 CLS に準拠するには、カスタム属性は System::Attribute から継承する必要があります。  System::Attribute から継承しなかった属性は、メンバー関数に適用されました。  
  
 \(MSIL アセンブリ言語を使用した\) 次の宣言では、CLS04111 の原因となり得るものを示しています。  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 さらに、以下の属性を使用したメンバー関数により、  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 00 00 00 00 00 00 )  
```  
  
 System::Attribute から属性が派生して、警告が解決されます。  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```