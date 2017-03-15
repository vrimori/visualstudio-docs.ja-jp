---
title: "コンパイラ エラー CS0153 | Microsoft Docs"
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
  - "CS0153"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0153"
ms.assetid: 3a0791e9-0ab9-4eaa-a230-d39aabaa9d5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0153
goto は switch ステートメント内でのみ有効です。  
  
 **switch**ステートメントの外側で [switch](/dotnet/csharp/language-reference/keywords/switch) 構文を使用しようとしました。 詳細については、「[switch](/dotnet/csharp/language-reference/keywords/switch)」を参照してください。  
  
 次の例では CS0153 が生成されます。  
  
```  
// CS0153.cs public class a { public static void Main() { goto case 5;   // CS0153 } }  
```