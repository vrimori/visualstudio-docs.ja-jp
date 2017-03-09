---
title: "複数の基本インターフェイスで宣言されているメソッドのオーバーロードは、有効ではありません | Microsoft Docs"
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
  - "bc31410"
  - "vbc31410"
helpviewer_keywords: 
  - "BC31410"
ms.assetid: 7d1831c2-837c-4b02-8492-d0fc038fe184
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 複数の基本インターフェイスで宣言されているメソッドのオーバーロードは、有効ではありません
継承された複数のインターフェイスが、同じメソッドを暗黙的にオーバーロードしています。  
  
 **エラー ID:** BC31410  
  
### このエラーを解決するには  
  
-   `Overloads` 修飾子の代わりに `Shadows` 修飾子を使用します。  
  
## 参照  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)