---
title: "コンパイラの警告 (レベル 1) CS1692 | Microsoft Docs"
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
  - "CS1692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1692"
ms.assetid: 1a6d52e1-0ebb-4990-ac0b-36b05a884a19
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1692
無効な数値です。  
  
 `#pragma`、`#line` などの多数のプリプロセッサ ディレクティブでは、パラメーターとして数値が使用されます。 これらの数値のいずれかが正しくありません。大きすぎる、形式が正しくない、使用できない文字が含まれていることなどが原因です。 このエラーを解決するには、数値を修正します。  
  
## 使用例  
 次の例では CS1692 が生成されます。  
  
```  
// CS1692.cs #pragma warning disable a  // CS1692 // Try this instad: // #pragma warning disable 1691 class A { static void Main() { } }  
```