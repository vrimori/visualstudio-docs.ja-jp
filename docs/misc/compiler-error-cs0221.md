---
title: "コンパイラ エラー CS0221 | Microsoft Docs"
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
  - "CS0221"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0221"
ms.assetid: 97170b49-54f1-4dac-a865-2f9cc6bf55b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0221
定数値 'value' は 'type' に変換できません \(unchecked 構文を使ってオーバーライドしてください\)。  
  
 データが失われる可能性のある代入演算が、既定でオンになっている [checked](/dotnet/csharp/language-reference/keywords/checked) によって検出されました。 このエラーを解決するには、代入を修正するか、または [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) を使用します。 詳細については、「[Checked と Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)」を参照してください。  
  
 次の例では CS0221 が生成されます。  
  
```  
// CS0221.cs public class MyClass { public static void Main() { // unchecked // { int a = (int)0xFFFFFFFF;   // CS0221 a++; // } } }  
```