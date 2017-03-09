---
title: "CLS 準拠の警告 CLS01106 | Microsoft Docs"
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
  - "CLS01106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01106"
ms.assetid: 0c964444-387d-4348-aed5-05f1ccc241c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01106
**シグネチャに出現するすべての型は CLS 準拠である必要があります。**  
  
 型が CLS 準拠である場合、この型のすべての関数には、CLS に準拠していないとしてマークされていない限り、CLS 準拠の型パラメーターが必要です。  
  
 CLS 準拠の確認の詳細については、「[CLS 準拠のアセンブリ](http://msdn.microsoft.com/ja-jp/3320b57e-ea55-4697-a17d-f509a36a3c93)」を参照してください。  
  
 次の例では CLS01106 が生成されます。  
  
```  
// CLS01106.cpp // compile with: /clr /LD // CLS01106 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; [CLSCompliant(true)] public ref class One { public: NotCompliantType^ Method1(NotCompliantType^ parameter) { return parameter; } CompliantType^ Method2(CompliantType^ parameter) {   // OK return parameter; } [CLSCompliant(false)] NotCompliantType^ Method3(NotCompliantType^ parameter) {   // OK return parameter; } };  
```