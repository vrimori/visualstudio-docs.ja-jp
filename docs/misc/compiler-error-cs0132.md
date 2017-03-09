---
title: "コンパイラ エラー CS0132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0132"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0132"
ms.assetid: e8ad1281-2912-4b6a-b2af-a319a23ddd16
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0132
'constructor' : 静的コンストラクターにパラメーターを指定することはできません  
  
 パラメーターを指定して、[静的](/dotnet/csharp/language-reference/keywords/static)コンストラクターを宣言することはできません。 詳細については、「[コンストラクター](/dotnet/csharp/programming-guide/classes-and-structs/constructors)」を参照してください。  
  
 次の例では CS0132 が生成されます。  
  
```  
// CS0132.cs namespace MyNamespace { public class MyClass { public MyClass(int i) { } } public class MyClass2 : MyClass { static MyClass2(int i)   // CS0132 { } } }  
```