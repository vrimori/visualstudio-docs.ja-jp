---
title: "コンパイラ エラー CS0180 | Microsoft Docs"
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
  - "CS0180"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0180"
ms.assetid: a21bf0a2-ed5a-4ddd-88d3-240babc5888a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0180
'member' に extern と abstract の両方を指定することはできません  
  
 [abstract](/dotnet/csharp/language-reference/keywords/abstract) キーワードと [extern](/dotnet/csharp/language-reference/keywords/extern) キーワードは、同時に指定できません。`extern` キーワードは、メンバーがファイルの外部で定義されていることを意味し、**abstract** は、派生クラスで実装が提供されることを意味します。 詳細については、「[メソッド](/dotnet/csharp/programming-guide/classes-and-structs/methods)」を参照してください。  
  
 次の例では CS0180 が生成されます。  
  
```  
// CS0180.cs namespace MyNamespace { public class MyClass { public extern abstract int Foo(int a);   // CS0180 public static void Main() { } } }  
```