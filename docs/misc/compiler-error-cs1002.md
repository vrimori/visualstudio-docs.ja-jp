---
title: "コンパイラ エラー CS1002 | Microsoft Docs"
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
  - "CS1002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1002"
ms.assetid: 659b7abf-9311-40c9-9594-5372464c6148
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1002
; が必要です。  
  
 コンパイラでセミコロンが不足していることが検出されました。 C\# のすべてのステートメントの末尾に、セミコロンが必要です。 ステートメントは、複数の行にまたがる可能性があります。  
  
 次の例では CS1002 が生成されます。  
  
```  
// CS1002.cs namespace x { abstract public class clx { int i   // CS1002, missing semicolon public static int Main() { return 0; } } }  
```  
  
## 参照  
 [ステートメント](/dotnet/csharp/programming-guide/statements-expressions-operators/statements)