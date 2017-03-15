---
title: "CLS 準拠の警告 CLS01114 | Microsoft Docs"
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
  - "CLS01114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01114"
ms.assetid: f3382da6-d3d0-4209-a229-400701c53ede
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01114
シグネチャに出現するすべての型は CLS 準拠でなければなりません  
  
 デリゲートが CLS 準拠である場合は、デリゲートのシグネチャのすべての型を CLS 準拠にする必要があります。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS01114 が生成されます。  
  
```  
// CLS01114.cpp // compile with: /clr /LD // CLS01114 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; // Public delegate public delegate CompliantType ^ PublicDelegate1(NotCompliantType^ param);   // CLS01114 public delegate CompliantType ^ PublicDelegate2(CompliantType^ param);   // OK  
```