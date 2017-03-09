---
title: "コンパイラ エラー CS0055 | Microsoft Docs"
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
  - "CS0055"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0055"
ms.assetid: 4d98abf3-2690-4418-8fd0-50c0e67d0a4a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0055
アクセシビリティに一貫性がありません。パラメーター型 'type' のアクセシビリティはインデクサー 'indexer' よりも低く設定されています  
  
 パブリック コンストラクトは、パブリックにアクセスできるオブジェクトを返す必要があります。 詳細については、「[アクセス修飾子](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)」を参照してください。  
  
 次の例では CS0055 が生成されます。  
  
```  
// CS0055.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public class MyClass2 { public int this[MyClass myClass]   // CS0055 { get { return 0; } } } public class MyClass3 { public static void Main() { } }  
```