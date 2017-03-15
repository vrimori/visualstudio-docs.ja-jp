---
title: "&#39;WithEvents&#39; 変数は、クラス、インターフェイスまたはクラスの制約がある型パラメーターとしてのみ型指定することができます | Microsoft Docs"
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
  - "vbc30413"
  - "bc30413"
helpviewer_keywords: 
  - "BC30413"
ms.assetid: 11ddf207-2760-425f-b4c2-bb9fe6da36ea
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;WithEvents&#39; 変数は、クラス、インターフェイスまたはクラスの制約がある型パラメーターとしてのみ型指定することができます
`WithEvents` と組み合わせて構造体として型指定される変数を宣言しましたが、`WithEvents` 修飾子の有効な使い方ではありません。  
  
 **エラー ID:** BC30413  
  
### このエラーを解決するには  
  
1.  `AddHandler` を使用して、構造体に定義されているイベントを処理します。  
  
## 参照  
 [ビルド内にありません: WithEvents と Handles 句](http://msdn.microsoft.com/ja-jp/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)