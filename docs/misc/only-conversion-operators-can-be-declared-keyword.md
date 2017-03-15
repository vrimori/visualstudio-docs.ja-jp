---
title: "変換演算子のみが &#39;&lt;keyword&gt;&#39; として宣言できます。 | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変換演算子のみが &#39;&lt;keyword&gt;&#39; として宣言できます。
演算子が変換演算子でない場合に、[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) が [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) または [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) を指定しています。  
  
 すべての演算子は、[Public](/dotnet/visual-basic/language-reference/modifiers/public) と [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) の両方として宣言する必要があります。 ただし、変換演算子だけは [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) または [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) で宣言できますが、両方で宣言することはできません。  
  
 演算子の定義には、必要に応じて、[Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) と [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) のキーワードを含めることができます。 その他のキーワードは [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) では許可されません。  
  
 **エラー ID:** BC33019  
  
### このエラーを解決するには  
  
1.  演算子の定義から `Widening` または `Narrowing` キーワードを削除します。 型変換が行われていないため、これらは適用されません。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)