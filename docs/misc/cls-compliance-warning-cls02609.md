---
title: "CLS 準拠の警告 CLS02609 | Microsoft Docs"
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
  - "CLS02609"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02609"
ms.assetid: ea1afa9a-03d2-4417-af14-68e3b03a858f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS02609
プロパティおよびそのアクセサーはすべて静的、すべて仮想、すべてインスタンスのいずれかになります  
  
 プロパティおよびそのアクセサーは静的、仮想、インスタンス修飾子が異なっていてはなりません。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS02609 が生成されます。  
  
```  
// CLS02609.cpp // compile with: /clr /LD // CLS02609 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { private: int InstanceMember; static int StaticMember; public: property int MyProperty1 {   // CLS02609 public: void set(int value) {} static int get() { return StaticMember; } } property int MyProperty2 {   // OK public: void set(int value) {} int get() { return StaticMember; } } };  
```