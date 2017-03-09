---
title: "CLS 準拠の警告 CLS01202 | Microsoft Docs"
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
  - "CLS01202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01202"
ms.assetid: ab75e9c4-9d87-4bb4-ad8f-3e6ab5559de7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01202
型およびメンバーの可視性およびアクセシビリティについて、メンバーのシグネチャに指定されている型は、そのメンバーが可視でアクセス可能な場合、必ず可視でアクセス可能でなければいけない。 たとえば、アセンブリ外部から参照できるパブリックなイベントには、アセンブリ内部でだけ可視である型が引数として含まれていてはいけない。  
  
 イベント ハンドラーの型には、イベント ハンドラーのアクセシビリティ以上のアクセシビリティが必要です。  
  
 CLS 準拠の確認について詳しくは、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」をご覧ください。  
  
 次の例では CLS01202 が生成されます。  
  
```  
/* CLS01202.cpp */ // compile with: /clr /LD // CLS01202 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyPublicDelegate(); private delegate void MyAssemblyDelegate(); public ref class One { public: event MyAssemblyDelegate^ MyEvent { public: void add(MyAssemblyDelegate^ Addparameter) {}   //  not cls compliant void remove(MyAssemblyDelegate^ Removeparameter) {}   //  not cls compliant void raise() {} } };  
```