---
title: "変換演算子によってインターフェイス型に変換することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33025"
  - "bc33025"
helpviewer_keywords: 
  - "BC33025"
ms.assetid: 7e13dfa3-2b70-4ca6-a8ec-159131fd2c4c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変換演算子によってインターフェイス型に変換することはできません
インターフェイス型を戻り値型として変換演算子が宣言されています。  
  
 コンパイル時に、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では参照型から任意のインターフェイスへの変換が事前に定義されているものと見なします。 このような変換は実行時に失敗する可能性がありますが、コンパイラは実行結果を予測できないため、これらの変換のコンパイルはすべて許可されます。  
  
 コンパイラでは、この変換が既に定義されていると見なされるため、この変換を再定義することはできません。  
  
 **エラー ID:** BC33025  
  
### このエラーを解決するには  
  
-   この演算子の定義を完全に削除します。 これは既に定義されています。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)