---
title: "&#39;System.Nullable&#39; は、型パラメーター &#39;&lt;typeparametername&gt;&#39; の &#39;Structure&#39; 制約を満たしていません。 | Microsoft Docs"
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
  - "bc32115"
  - "vbc32115"
helpviewer_keywords: 
  - "BC32115"
ms.assetid: 98053645-fa76-4826-a7c1-f1bdf3511863
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Nullable&#39; は、型パラメーター &#39;&lt;typeparametername&gt;&#39; の &#39;Structure&#39; 制約を満たしていません。
`Structure` 制約が指定された型パラメーターに型引数 <xref:System.Nullable%601> を渡すジェネリック型が呼び出されました。  
  
 共通言語ランタイム \(CLR\) では、明確に、<xref:System.Nullable%601> 構造体をそれ自体への型引数として使用することを許可していません。 これは構造体であり、それ以前に `Structure` 制約を満たしていますが、この構造体を再帰的に使用すると、`Nullable(Of Nullable(Of Nullable))` のような適切でない構築となる可能性があります。  
  
 **エラー ID:** BC32115  
  
### このエラーを解決するには  
  
-   `Structure` 制約を型パラメーターから削除するか、または型引数を <xref:System.Nullable%601> 以外の何らかの値型に変更します。  
  
## 参照  
 <xref:System.Nullable%601>   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)