---
title: "&#39;New&#39; 制約は、同じ型パラメーターに対して複数回指定できません | Microsoft Docs"
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
  - "vbc32081"
  - "BC32081"
helpviewer_keywords: 
  - "BC32081"
ms.assetid: afcb30da-3973-4452-9cf3-c027f9866589
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; 制約は、同じ型パラメーターに対して複数回指定できません
制約リストに [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) 制約が 2 回以上含まれています。  
  
 型パラメーターの制約リストは、その型パラメーターに渡される型引数が、作成元のコードからアクセスできるパラメーターなしのコンストラクターを公開する必要があることを指定できます。 型はパラメーターなしのコンストラクターを複数持つことはできないため、この要件を複数回指定することはできません。  
  
 **エラー ID:** BC32081  
  
### このエラーを解決するには  
  
-   冗長な `New` キーワードがある場合は削除します。 制約リストにはこれを 1 つだけ含める必要があります。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)