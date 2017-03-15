---
title: "CLS 準拠の警告 CLS01206 | Microsoft Docs"
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
  - "CLS01206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01206"
ms.assetid: e72f2293-874b-406c-9f22-92aeb64ac732
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01206
型およびメンバーの可視性およびアクセシビリティについて、メンバーのシグネチャに指定されている型は、そのメンバーが可視でアクセス可能な場合、必ず可視でアクセス可能でなければいけない。 たとえば、アセンブリ外部から参照できるパブリックなメンバー関数には、アセンブリ内部でだけ可視である型が引数として含まれていてはいけない。  
  
 メソッド シグネチャ内の型については、メソッドのアクセシビリティ以上のアクセシビリティが含まれていなければならない。  たとえば、アセンブリ外部から参照できるパブリックなメソッドには、アセンブリ内部でだけ可視である型が引数として含まれていてはいけない。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS01206 が生成されます。  
  
```  
/* CLS01206.cpp */ // compile with: /clr /LD // CLS01206 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Method1() { return gcnew AssemblyLevelType(); } };  
```