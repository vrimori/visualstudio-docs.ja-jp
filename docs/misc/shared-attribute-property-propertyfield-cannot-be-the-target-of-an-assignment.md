---
title: "&#39;Shared&#39; 属性プロパティ &#39;&lt;propertyfield&gt;&#39; を代入式のターゲットにすることはできません | Microsoft Docs"
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
  - "bc31500"
  - "vbc31500"
helpviewer_keywords: 
  - "BC31500"
ms.assetid: dffa2b07-9609-4aa3-ae58-c0804d8a05d6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Shared&#39; 属性プロパティ &#39;&lt;propertyfield&gt;&#39; を代入式のターゲットにすることはできません
属性の `ReadOnly` または `Shared` プロパティに値を代入しようとしました。  
  
 **エラー ID:** BC31500  
  
### このエラーを解決するには  
  
1.  プロパティの代入ステートメントを削除します。  
  
2.  独自に作成したプロパティを使用している場合は、属性プロパティから `ReadOnly` 修飾子または `Shared` 修飾子を削除します。  
  
## 参照  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NOT IN BUILD: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)