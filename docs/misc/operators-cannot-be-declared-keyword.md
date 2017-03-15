---
title: "演算子は &#39;&lt;keyword&gt;&#39; として宣言できません | Microsoft Docs"
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
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演算子は &#39;&lt;keyword&gt;&#39; として宣言できません
演算子が、演算子の定義に使用できないキーワードを使用して宣言されています。  
  
 すべての演算子は、[Public](/dotnet/visual-basic/language-reference/modifiers/public) と [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) の両方として宣言する必要があります。 さらに、変換演算子は [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) か [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) のいずれかを使用して宣言する必要があり、両方を使用することはできません。 演算子の定義には、必要に応じて、[Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) または [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) のキーワードを含めることができます。 その他のキーワードは [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) では許可されません。  
  
 **エラー ID:** BC33013  
  
### このエラーを解決するには  
  
-   使用できないキーワードを演算子の定義から削除します。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)