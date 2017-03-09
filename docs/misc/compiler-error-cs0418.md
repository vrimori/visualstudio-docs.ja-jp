---
title: "コンパイラ エラー CS0418 | Microsoft Docs"
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
  - "CS0418"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0418"
ms.assetid: b78fafde-428b-4fa2-a933-c4614760bb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0418
'class name': 抽象クラスを sealed または static に指定することはできません。  
  
 抽象クラスは、派生したものでない限りオブジェクトの作成に使用できないので、sealed に指定しても意味がありません。 抽象クラスを static に指定することにも意味がありません。抽象クラスは、その抽象クラスをベースとして使用するオブジェクト階層をサポートするために設計されています。  
  
## 使用例  
 次の例では CS0418 が生成されます。  
  
```  
// CS0418.cs public abstract sealed class C  // CS0418 { } sealed static class S  // CS0418 { } public class MyClass { public static void Main() { } }  
```