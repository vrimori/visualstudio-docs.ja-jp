---
title: "コンパイラ エラー CS0158 | Microsoft Docs"
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
  - "CS0158"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0158"
ms.assetid: 88ac61a9-ce55-4272-9141-0873765a7034
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0158
スコープ内に、ラベル 'label' と同じ名前のラベルが存在しますが、無視されます。  
  
 内側のスコープ内のラベルでは、外側のスコープで同じ名前のラベルが非表示です。 詳細については、「[goto](/dotnet/csharp/language-reference/keywords/goto)」を参照してください。  
  
 次の例では CS0158 が生成されます。  
  
```  
// CS0158.cs namespace MyNamespace { public class MyClass { public static void Main() { goto lab1; lab1: { lab1: goto lab1;   // CS0158 } } } }  
```