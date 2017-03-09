---
title: "CLS 準拠の警告 CLS01109 | Microsoft Docs"
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
  - "CLS01109"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01109"
ms.assetid: 5bfd6fcf-95bb-4f13-8090-5303eebb3c06
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 準拠の警告 CLS01109
シグネチャに使用する型は、すべて CLS 準拠でなければなりません  
  
 メンバー関数のシグネチャに使用されているすべての型が CLS 準拠であることを確認します。  
  
 次の例では CLS01109 が生成されます。  
  
```  
// CLS01109.cpp // compile with: /clr /c [assembly:System::CLSCompliant(true)]; [System::CLSCompliant(false)] public ref class NotCompliantType {}; public ref class MyClass { public: property array< NotCompliantType^ >^ SomeProperty {   // CLS01109 array< NotCompliantType^ >^ get() { return nullptr; } void set(array< NotCompliantType^ >^ v ) { } } };  
```  
  
 考えられる解決策:  
  
```  
// CLS01109b.cpp // compile with: /clr /LD [assembly:System::CLSCompliant(true)]; public ref class CompliantType {}; public ref class MyClass { public: property array< CompliantType^ >^ SomeProperty { array< CompliantType^ >^ get() { return nullptr; } void set(array< CompliantType^ >^ v ) { } } };  
```