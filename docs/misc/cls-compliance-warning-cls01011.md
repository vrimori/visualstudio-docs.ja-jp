---
title: "CLS 準拠の警告 CLS01011 | Microsoft Docs"
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
  - "CLS01011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01011"
ms.assetid: e4141e15-14fd-491c-9639-f3f3a47d7865
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01011
継承されたメソッドをオーバーライドする場合、アクセシビリティを変更することはできません  
  
 オーバーライドするメソッドの可視性がオーバーライドされる側のメソッドの可視性と同じであることをご確認ください。  継承されたメソッドをオーバーライドする場合、アクセシビリティは変更できません。ただし、別のアセンブリから継承されたメソッドをアクセシビリティ ファミリまたはアセンブリでオーバーライドする場合は例外です。 その場合、オーバーライドのアクセシビリティはファミリにしてください。  
  
 CLS 準拠の確認について詳しくは、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」をご覧ください。  
  
 次の例では CLS01011 が生成されます。  
  
```  
// CLS01011.cpp // compile with: /clr /LD // CLS01011 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class BaseType { public protected: virtual void BaseTypeMethod() {} }; public ref class One : public BaseType { public: void BaseTypeMethod() {}   // CLS01011 // OK // public protected: //    void BaseTypeMethod() {} };  
```