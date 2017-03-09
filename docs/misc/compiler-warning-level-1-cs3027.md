---
title: "コンパイラの警告 (レベル 1) CS3027 | Microsoft Docs"
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
  - "CS3027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3027"
ms.assetid: c515e623-3f5a-49fa-a878-f1d8e90fdc24
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3027
基底インターフェイス 'type\_2' が CLS に準拠していないため、'type\_1' は CLS に準拠していません  
  
 CLS 非準拠の型を CLS 準拠の型の基本型にすることはできません。  
  
## 使用例  
 次の例には、シグニチャに CLS 非準拠の型を使用するメソッドを持ち、型が CLS 非準拠になるインターフェイスが含まれています。  
  
```  
// CS3027.cs // compile with: /target:library public interface IBase { void IMethod(uint i); }  
```  
  
## 使用例  
 次の例では CS3027 が生成されます。  
  
```  
// CS3027_b.cs // compile with: /reference:CS3027.dll /target:library /W:1 [assembly:System.CLSCompliant(true)] public interface IDerived : IBase {}  
```