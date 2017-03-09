---
title: "CLS 準拠の警告 CLS01911 | Microsoft Docs"
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
  - "CLS01911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01911"
ms.assetid: 673a701a-166b-4782-bff4-a198f70becd5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01911
CLS 準拠インターフェイスでは、静的メソッドを定義してはいけない。また、フィールドも定義してはいけない。  
  
 CLS 準拠のインターフェイスには、静的メソッドまたはフィールドを含めることはできません。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS01911 が生成されます。  
  
```  
// CLS01911.cpp // compile with: /clr /LD // CLS01911 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public interface class IOne { static void Method1() {}   // interface static method not cls compliant };  
```