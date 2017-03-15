---
title: "&#39;As&#39; 句のない関数です。戻り値の型には Object が想定されます。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC42021"
  - "vbc42021"
helpviewer_keywords: 
  - "BC42021"
ms.assetid: c1efadf1-fba3-437b-a311-240c4d07d894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;As&#39; 句のない関数です。戻り値の型には Object が想定されます。
`Function` プロシージャは `As` 句を指定しません。  
  
 `As` 句は、プログラミング要素に関連付けられるデータ型を指定します。[Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) で、この句は `Function` プロシージャが呼び出し元のコードに返す値のデータ型を指定します。`Function` ステートメントに `As` 句を含めない場合、戻り値のデータ型は既定で `Object` になります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」をご覧ください。  
  
 **エラー ID:** BC42021  
  
### このエラーを解決するには  
  
-   `Function` ステートメントに `As` 句を含めて、戻り値のデータ型を指定します。  
  
## 参照  
 [Function プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)