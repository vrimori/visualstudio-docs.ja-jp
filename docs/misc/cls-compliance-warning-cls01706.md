---
title: "CLS 準拠の警告 CLS01706 | Microsoft Docs"
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
  - "CLS01706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01706"
ms.assetid: b89ccbf1-7256-4842-a0af-44a803f28340
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01706
アンマネージ ポインター型は CLS 準拠ではない  
  
 CLS 準拠の関数のシグネチャに、アンマネージ ポインター型を含めることはできません。  
  
 共通言語サブセット \(CLS\) 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS01706 が生成されます。  
  
```  
// CLS01706.cpp // compile with: /clr /LD // CLS01706 expected [assembly:System::CLSCompliant (true)]; [assembly:System::Reflection::AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: void Method1(int* parameter) {}   // CLS01706 void Method1(One ^ parameter) {}   // OK };  
```