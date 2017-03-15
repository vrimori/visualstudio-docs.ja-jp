---
title: "CLS 準拠の警告 CLS01606 | Microsoft Docs"
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
  - "CLS01606"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01606"
ms.assetid: 24291af4-d2b1-4a91-b50f-fb61d8ff1687
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01606
配列は、要素が CLS 準拠型で、すべての次元でインデックス番号が 0 から始まらなければなりません  
  
 配列は、要素が CLS 準拠型で、すべての次元でインデックス番号が 0 から始まらなければなりません。 項目が配列の場合、オーバーロードどうしを区別するには配列要素の型を必要とする。 オーバーロードが 2 つ以上の配列型に基づく場合、要素型は名前付きの型でなければいけない。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS01606 が生成されます。  
  
```  
// CLS01606.cpp // compile with: /clr /LD // CLS01606 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; public ref class One { public: // CLS01606 array<NotCompliantType^>^ Method1() { return gcnew array<NotCompliantType^>(10); } // OK array<CompliantType^>^ Method2() { return gcnew array<CompliantType^>(10); } };  
```