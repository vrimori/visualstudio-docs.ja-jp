---
title: "CLS 準拠の警告 CLS00211 | Microsoft Docs"
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
  - "CLS00211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00211"
ms.assetid: 3a103f6f-bfb7-42ed-83ab-1c0f34fb9672
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS00211
CLS 非準拠型のメンバーを CLS 準拠と指定しません  
  
 型が CLS 非準拠とマークされている場合、型のメンバーを CLS 準拠とマークすることはできません。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS00211 が生成されます。  
  
```  
// CLS00211.cpp // compile with: /clr /LD // CLS00211 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(false)] public ref class One { public: [CLSCompliant(true)]   // CLS00211 void X() {} };  
```