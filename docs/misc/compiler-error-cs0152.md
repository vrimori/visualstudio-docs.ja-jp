---
title: "コンパイラ エラー CS0152 | Microsoft Docs"
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
  - "CS0152"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0152"
ms.assetid: 4915ca16-6485-4e1f-ace0-c71a7b339ba4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0152
ラベル 'label' は既にこの switch ステートメントで使用されています  
  
 [switch](/dotnet/csharp/language-reference/keywords/switch) ステートメントでラベルを繰り返しました。 詳細については、「[switch](/dotnet/csharp/language-reference/keywords/switch)」を参照してください。  
  
 次の例では CS0152 が生成されます。  
  
```  
// CS0152.cs namespace MyNamespace { public class MyClass { public static void Main() { int i = 0; switch (i) { case 1: i++; return; case 1:   // CS0152, two case 1 statements i++; return; } } } }  
```