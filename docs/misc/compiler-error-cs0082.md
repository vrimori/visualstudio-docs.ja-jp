---
title: "コンパイラ エラー CS0082 | Microsoft Docs"
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
  - "CS0082"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0082"
ms.assetid: 7612976f-de2c-4f6b-87c9-43175821650c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0082
型 'type' は、'name' と呼ばれるメンバーを同じパラメーターの型で既に予約しています  
  
 コンパイル時に、プロパティは、識別子の前の `get_` と `set_`、またはそのいずれかでメソッドに変換されます。 メソッド名と競合する独自のメソッドを定義すると、エラーが生成されます。  
  
## 使用例  
 次の例では CS0082 が生成されます。  
  
```  
//cs0082.cs class MyClass { //property public int MyProp { get //CS0082 { return 1; } } //conflicting Get public int get_MyProp() { return 2; } public static int Main() { return 1; } }  
```  
  
## 参照  
 [プロパティ](/dotnet/csharp/programming-guide/classes-and-structs/properties)