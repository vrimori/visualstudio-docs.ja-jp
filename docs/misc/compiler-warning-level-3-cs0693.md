---
title: "コンパイラの警告 (レベル 3) CS0693 | Microsoft Docs"
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
  - "CS0693"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0693"
ms.assetid: a3902336-49db-4808-b41f-8f0936bff53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 3) CS0693
型パラメーター 'type parameter' は、外の型 'type' からの型パラメーターと同じ名前です  
  
 このエラーは、ジェネリック クラスにメソッドなどの汎用メンバーがある場合に発生します。 メソッドの型パラメーターは必ずしもクラスの型パラメーターと同じではないため、両方に同じ名前を付けることはできません。 詳細については、「[ジェネリック メソッド](/dotnet/csharp/programming-guide/generics/generic-methods)」を参照してください。  
  
 この状況を回避するには、型パラメーターのいずれかに別の名前を使用します。  
  
## 使用例  
 次の例では CS0693 が生成されます。  
  
```  
// CS0693.cs // compile with: /W:3 /target:library class Outer<T> { class Inner<T> {}   // CS0693 // try the following line instead // class Inner<U> {} }  
```