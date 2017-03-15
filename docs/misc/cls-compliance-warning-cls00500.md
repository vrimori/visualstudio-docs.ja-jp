---
title: "CLS 準拠の警告 CLS00500 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS00500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00500"
ms.assetid: faaf377e-3738-4c0d-9a51-09db4073564e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS00500
CLS 準拠のスコープ内のすべての名前は独立した種類である必要があります  
  
 CLS 準拠のスコープに導入されるすべての名前は、完全に独立した種類である必要があります。ただし、名前が同じでオーバーロードによって解決できる場合を除きます。 CLS のために、小文字マッピングが同じ場合、2 つの名前が同じです。 プロパティおよび関数のみオーバーロードできます。 オーバーロードされる場合、プロパティおよび関数は、パラメーターの数値と型にのみ基づいてオーバーロードされます。ただし、戻り値の型に基づいてオーバーロードできる変換演算子は例外です。詳細については、「[ユーザー定義変換](/visual-cpp/dotnet/user-defined-conversions-cpp-cli)」を参照してください。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS00500 が生成されます。  
  
```  
// CLS00500.cpp // compile with: /clr /LD // CLS00500 expected using namespace System; using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; [assembly:System::CLSCompliant(true)]; public ref class a {}; public ref class A {};   // CLS00500  
```