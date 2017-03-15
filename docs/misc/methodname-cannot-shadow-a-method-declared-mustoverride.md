---
title: "&#39;&lt;methodname&gt;&#39; で、&#39;MustOverride&#39; と宣言されたメソッドに &#39;Shadows&#39; を実行することはできません。 | Microsoft Docs"
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
  - "vbc31404"
  - "bc31404"
helpviewer_keywords: 
  - "BC31404"
ms.assetid: 3e7bb4a0-14af-46ba-bc62-2234c16f1827
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;methodname&gt;&#39; で、&#39;MustOverride&#39; と宣言されたメソッドに &#39;Shadows&#39; を実行することはできません。
`MustOverride` 修飾子と同じ名前を持つプロパティまたはメソッドが、派生クラスで宣言されています。  
  
 **エラー ID:** BC31404  
  
### このエラーを解決するには  
  
1.  派生クラス内のオーバーライドするプロパティまたはメソッドに `Overrides` 修飾子を追加します。  
  
2.  基底クラスのプロパティまたはメソッドから `MustOverride` 修飾子を削除します。  
  
## 参照  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)