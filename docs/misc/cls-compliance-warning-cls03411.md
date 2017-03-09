---
title: "CLS 準拠の警告 CLS03411 | Microsoft Docs"
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
  - "CLS03411"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03411"
ms.assetid: 79b0955a-5a86-46a8-90e9-4419c9068bbe
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS03411
CLS ではカスタム属性のエンコーディングのサブセットのみ使用できます  
  
 CLS では、カスタム属性のコンストラクターのパラメーターとして、またはカスタム属性のデータ メンバーの型としてのみ、型のサブセットを使用できます。 使用できる型は次のとおりです。  
  
-   System.Type  
  
-   System.String  
  
-   System.Char  
  
-   System.Boolean  
  
-   System.Byte  
  
-   System.Int16  
  
-   System.Int32  
  
-   System.Int64  
  
-   System.Single  
  
-   System.Double  
  
-   CLS 準拠の基底の整数型に基づく列挙型。  
  
 共通言語サブセット \(CLS\) 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS03411 が生成されます。  
  
```  
// CLS03411.cpp // compile with: /clr /LD // CLS03411 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; // CLS03411 [AttributeUsage(AttributeTargets::All, AllowMultiple=true)] public ref class MyAttribute1 : public Attribute { public: MyAttribute1(Object^ parameter) {} }; // OK [AttributeUsage(AttributeTargets::All, AllowMultiple=true)] public ref class MyAttribute3 : public Attribute { public: MyAttribute3(Char parameter) {} };  
```