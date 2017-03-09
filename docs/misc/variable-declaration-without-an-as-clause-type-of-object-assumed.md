---
title: "&#39;As&#39; 句のない変数宣言です。Object の型と見なされます | Microsoft Docs"
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
  - "BC42020"
  - "vbc42020"
helpviewer_keywords: 
  - "BC42020"
ms.assetid: 9422b16d-39b5-4d49-b697-608226ccafea
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;As&#39; 句のない変数宣言です。Object の型と見なされます
変数宣言は `As` 句を指定していません。  
  
 `As` 句は、プログラミング要素に関連付けられるデータ型を指定します。[Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement) で、変数 \(複数可\) のデータ型が指定されます。`Dim` ステートメントに `As` 句を含めない場合、変数のデータ型は既定で `Object` になります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42020  
  
### このエラーを解決するには  
  
-   `Dim` ステートメントに `As` 句を含めて、変数のデータ型を指定します。  
  
## 参照  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [変数宣言](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)