---
title: "CLS 準拠の警告 CLS00711 | Microsoft Docs"
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
  - "CLS00711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00711"
ms.assetid: 76481641-bda1-4128-8da8-ccba577b7ba1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS00711
列挙型の基になる型は組み込みの CLS 整数型でなくてはならない  
  
 列挙型の基になる型を指定して、CLS 準拠のアセンブリを作成する場合は、列挙型の基になる型は共通言語サブセット \(CLS\) 準拠の整数型である必要があります。  
  
 CLR 列挙型の詳細については、「[enum class](/visual-cpp/windows/enum-class-cpp-component-extensions)」を参照してください。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS00711 が生成されます。  
  
```  
// CLS00711.cpp // compile with: /clr /LD // CLS00711 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: enum class MyEnum_cls_bad : Char { bad_one = 1, bad_two = 2, bad_three = 3 }; enum class MyEnum_cls_good : Int32 { good_one = 1, good_two = 2, good_three = 3 }; };  
```