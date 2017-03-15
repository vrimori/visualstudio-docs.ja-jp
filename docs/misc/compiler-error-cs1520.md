---
title: "コンパイラ エラー CS1520 | Microsoft Docs"
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
  - "CS1520"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1520"
ms.assetid: 1aeeee83-52a6-45dc-b197-a9a6de3a220c
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1520
メソッドは戻り値の型を持たなければなりません。  
  
 クラス、構造体、インターフェイスで宣言されているメソッドには、明示的な戻り値の型が必要です。 次の例では、Square メソッドの戻り値の型は [string](/dotnet/csharp/language-reference/keywords/string) です。  
  
```  
class Test { string IntToString(int i) { return i.ToString(); } }  
```  
  
 次の例では CS1520 が生成されます。  
  
```  
// CS1520a.cs public class x { // Method declaration missing a return type MyMethod()   // CS1520 {} // Add the desired return type: // void MyMethod2() // { } public static void Main() { } }  
```  
  
 または、次の例に示すように、コンストラクターの名前の大文字と小文字がクラスまたは構造体の宣言と異なる場合にこのエラーが発生する可能性があります。 名前がクラス名と厳密に同じではないため、コンパイラはこれをコンストラクターではなく通常のメソッドとして解釈し、エラーを生成します。  
  
```  
// CS1520b.cs public class Class1 { // Should be Class1, not class1 public class1()   // CS1520 { } static void Main() { } }  
```  
  
## 参照  
 [メソッド](/dotnet/csharp/programming-guide/classes-and-structs/methods)   
 [コンストラクター](/dotnet/csharp/programming-guide/classes-and-structs/constructors)