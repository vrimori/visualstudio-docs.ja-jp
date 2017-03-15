---
title: "コンパイラ エラー CS0176 | Microsoft Docs"
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
  - "CS0176"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0176"
ms.assetid: 783c13d8-5ac3-4aeb-bd63-0468cb05550d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0176
インスタンス参照で静的メンバー 'member' にアクセスできません。型名を代わりに使用してください  
  
 [static](/dotnet/csharp/language-reference/keywords/static) 変数の修飾に使用できるのはクラス名のみです。インスタンス名を修飾子にすることはできません。 詳細については、「[静的クラスと静的クラス メンバー](/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members)」を参照してください。  
  
 次の例では CS0176 が生成されます。  
  
```  
// CS0176.cs public class MyClass2 { public static int num; } public class Test { public static void Main() { MyClass2 mc2 = new MyClass2(); int i = mc2.num;   // CS0176 // try the following line instead // int i = MyClass2.num; } }  
  
```