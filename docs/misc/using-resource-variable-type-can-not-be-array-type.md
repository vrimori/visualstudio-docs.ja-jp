---
title: "&#39;Using&#39; リソース変数の型を配列型にすることはできません | Microsoft Docs"
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
  - "vbc36012"
  - "bc36012"
helpviewer_keywords: 
  - "BC36012"
ms.assetid: f98c54b0-6ede-48b6-aa31-438664c219f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Using&#39; リソース変数の型を配列型にすることはできません
`Using` ステートメントは、リソースの配列変数を指定します。  
  
 <xref:System.Array> クラスは <xref:System.IDisposable> インターフェイスを実装しないため、`Using` ブロックは配列リソース上の <xref:System.IDisposable.Dispose%2A> メソッドを呼び出すことはできません。  
  
 **エラー ID:** BC36012  
  
### このエラーを解決するには  
  
-   `Using` ブロック内で、システム リソースの別の型を使用します。  
  
## 参照  
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)   
 [ビルド内にありません: Visual Basic での配列の概要](http://msdn.microsoft.com/ja-jp/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)