---
title: "コンパイラ エラー CS0059 | Microsoft Docs"
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
  - "CS0059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0059"
ms.assetid: 25a8624b-7f7b-4487-ba80-413d57f9132b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0059
アクセシビリティに一貫性がありません。パラメーター型 'type' のアクセシビリティはデリゲート 'delegate' よりも低く設定されています  
  
 戻り値の型と、メソッドの仮パラメーター リストで参照されるそれぞれの型は、少なくともメソッド自体と同程度にアクセス可能である必要があります。 詳細については、「[アクセス修飾子](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)」を参照してください。  
  
## 使用例  
 次の例では CS0059 が生成されます。  
  
```  
// CS0059.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public delegate void MyClassDel( MyClass myClass);   // CS0059 public class Program { public static void Main() { } }  
```