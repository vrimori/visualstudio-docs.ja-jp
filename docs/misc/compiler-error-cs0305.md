---
title: "コンパイラ エラー CS0305 | Microsoft Docs"
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
  - "CS0305"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0305"
ms.assetid: a862c484-01fe-4067-b0f4-15a618e7f8a1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0305
ジェネリック型 'generic type' を使用するには 'number' 型引数が必要です  
  
 このエラーは、必要な数の型引数が見つからなかった場合に発生します。 C0305 を解決するには、必要な数の型引数を使用します。  
  
## 使用例  
 次の例では CS0305 が生成されます。  
  
```  
// CS0305.cs public class MyList<T> {} public class MyClass<T> {} class MyClass { public static void Main() { MyList<MyClass, MyClass> list1 = new MyList<MyClass>();   // CS0305 MyList<MyClass> list2 = new MyList<MyClass>();   // OK } }  
```