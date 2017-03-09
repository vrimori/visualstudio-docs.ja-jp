---
title: "コンパイラ エラー CS1918 | Microsoft Docs"
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
  - "CS1918"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1918"
ms.assetid: 9ad2cbbd-3c10-4d56-b4cd-385103d005d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1918
型 'type' のプロパティ 'name' のメンバーは、値の型であるため、オブジェクト初期化子と共に割り当てることはできません。  
  
 このエラーは、それ自体が初期化されるクラスのプロパティである構造体型のプロパティを初期化するためにオブジェクト初期化子を使用しようとしたときに発生します。  
  
### このエラーを解決するには  
  
1.  オブジェクト初期化子でプロパティのフィールドを完全に初期化する必要がある場合は、構造体をクラス型に変更します。 それ以外の場合は、オブジェクト初期化子を使用してオブジェクトを作成した後に、別個のメソッド呼び出しで構造体メンバーを初期化します。  
  
## 使用例  
 次の例では、CS1918 が生成されます。  
  
```  
// cs1918.cs public struct MyStruct { public int i; } public class Test { private MyStruct str = new MyStruct(); public MyStruct Str { get { return str; } } public static int Main() { Test t = new Test { Str = { i = 1 } }; // CS1918 return 0; } }  
  
```  
  
## 参照  
 [オブジェクト初期化子とコレクション初期化子](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)