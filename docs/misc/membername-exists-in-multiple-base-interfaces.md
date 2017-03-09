---
title: "複数の基底インターフェイスに &#39;&lt;membername&gt;&#39; が存在します | Microsoft Docs"
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
  - "vbc31040"
  - "bc31040"
helpviewer_keywords: 
  - "BC31040"
ms.assetid: c1a80d64-3986-417f-af92-412183e490ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 複数の基底インターフェイスに &#39;&lt;membername&gt;&#39; が存在します
複数の基底インターフェイスに '\<membername\>' が存在します。 派生インターフェイスの名前ではなく、'Implements' 句で '\<membername\>' を宣言するインターフェイスの名前を使用します。  
  
 このインターフェイスが複数のインターフェイスから同じ名前を持つメンバーを継承していることが、あいまいさの原因になっています。  
  
 **エラー ID:** BC31040  
  
### このエラーを解決するには  
  
-   派生インターフェイスの名前ではなく、`Implements` 句でインターフェイスを定義している名前を使用します。  
  
## 参照  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)