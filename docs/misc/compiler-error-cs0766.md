---
title: "コンパイラ エラー CS0766 | Microsoft Docs"
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
  - "CS0766"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0766"
ms.assetid: 4574e30b-3e76-42cd-90e8-31c72126a08c
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0766
部分メソッドには、void である戻り値の型が含まれている必要があります  
  
 部分メソッドは値を返すことができません。 戻り値の型を void にする必要があります。  
  
### このエラーを解決するには  
  
1.  部分メソッドに戻り値の型として void を指定するか、メソッドを \(部分メソッドではない\) 通常のメソッドに変換します。  
  
## 使用例  
 次の例では CS0766 が生成されます。  
  
```  
// cs0766.cs using System; public partial class C { partial int Part(); // CS0766 // Typically the implementing declaration // is contained in a separate file. partial int Part() //CS0766 { } public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)