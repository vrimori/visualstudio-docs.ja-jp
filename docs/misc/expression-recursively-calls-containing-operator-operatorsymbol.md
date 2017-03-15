---
title: "式は、包含する演算子 &#39;&lt;operatorsymbol&gt;&#39; を再帰的に呼び出しています | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC42004"
  - "vbc42004"
helpviewer_keywords: 
  - "BC42004"
ms.assetid: a874c44a-3aec-447d-90f7-5659f1b2f5f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 式は、包含する演算子 &#39;&lt;operatorsymbol&gt;&#39; を再帰的に呼び出しています
演算子プロシージャ内の式では、定義されている演算子を使用します。 つまり、使用するデータ型が原因で、演算子プロシージャはそれ自体を呼び出すことになります。  
  
 次のいずれかを指定して同じ演算子を使用する場合は、定義している演算子プロシージャはそれ自体を呼び出します。  
  
-   演算子を定義しているのと同じオペランド。  
  
-   演算子を定義しているのと同じデータ型のオペランド。  
  
-   演算子を定義しているデータ型に拡大変換するデータ型のオペランド。  
  
 *再帰呼び出し*とは、プロシージャがそれ自体を呼び出すことを指します。 再帰呼び出しにより、*無限ループ*が発生する可能性があります。この場合、アプリケーションが外部から終了されるまで、同じ一連のステートメントを制御が繰り返し通過します。 コードに再帰の終了に使用できる 1 つ以上のテストが含まれていない場合は、無限ループが発生する危険性があります。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42004  
  
### このエラーを解決するには  
  
-   ロジックで、演算子プロシージャにそれ自体を呼び出すよう要求する場合は、ある時点で確実に発生する少なくとも 1 つの条件に対して必ずテストを行うようにして、このテストを使用して再帰呼び出しを終了します。  
  
-   ロジックで、演算子プロシージャにそれ自体を呼び出すよう要求しない場合は、再帰呼び出しを削除するか、独自のプロシージャを呼び出さないステートメントに置き換えます。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)