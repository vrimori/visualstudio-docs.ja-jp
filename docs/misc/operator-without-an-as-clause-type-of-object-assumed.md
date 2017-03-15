---
title: "&#39;As&#39; 句のない演算子です。Object の型と見なされます | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc41005"
  - "bc41005"
helpviewer_keywords: 
  - "BC41005"
ms.assetid: 42be84ed-7aa6-4ac0-9dd4-663e90f13e09
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;As&#39; 句のない演算子です。Object の型と見なされます
演算子プロシージャは `As` 句を指定しません。  
  
 `As` 句は、プログラミング要素に関連するデータ型を指定します。[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) で、この句は演算子プロシージャが呼び出しコードに返す値のデータ型を指定します。`Operator` ステートメントに `As` 句を含めない場合、戻り値のデータ型は既定で `Object` になります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC41005  
  
### このエラーを解決するには  
  
-   `Operator` ステートメントに `As` 句を含めて、戻り値のデータ型を指定します。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)