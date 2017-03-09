---
title: "型 &#39;&lt;typename&gt;&#39; の式は、&#39;Object&#39; または &#39;ValueType&#39; に変換できません | Microsoft Docs"
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
  - "bc31394"
  - "vbc31394"
helpviewer_keywords: 
  - "BC31394"
ms.assetid: e6f76257-65bb-4954-99f9-90f282648354
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename&gt;&#39; の式は、&#39;Object&#39; または &#39;ValueType&#39; に変換できません
式の評価結果が、共通言語ランタイム \(CLR\) でボックス化できない型になります。  
  
 *ボックス化*とは、型を `Object` \(場合によっては <xref:System.ValueType>\) に変換するために不可欠な処理です。 共通言語ランタイムは、<xref:System.ArgIterator> や <xref:System.TypedReference> などの特定の型をボックス化できません。  
  
 この式が含まれるステートメントで `CType` や `CObj` を使用していない場合は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] がこのエラーの原因となる暗黙的な変換を試行しました。  
  
 **エラー ID:** BC31394  
  
### このエラーを解決するには  
  
1.  問題の型に評価される式を探します。  
  
2.  問題の型のボックス化を試行するステートメントの部分を探します。  
  
3.  ステートメントを書き直して、ボックス化の変換が行われないようにします。  
  
## 参照  
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)