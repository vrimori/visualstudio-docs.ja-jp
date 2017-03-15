---
title: "&#39;Class&#39; 制約は、同じ型パラメーターに対して複数回指定できません | Microsoft Docs"
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
  - "bc32101"
  - "vbc32101"
helpviewer_keywords: 
  - "BC32101"
ms.assetid: fac2330a-e397-4bd9-8166-934407575f9e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Class&#39; 制約は、同じ型パラメーターに対して複数回指定できません
制約リストに[クラス \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 制約が 2 回以上含まれています。  
  
 型パラメーターの制約リストでは、その型パラメーターに渡される型引数が値型である必要があるか \([構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) 制約による\)、参照型である必要があるか \(`Class` 制約による\) を指定できます。 同じ型パラメーターに両方の制約を指定することはできません。また、どちらも複数回指定することはできません。  
  
 エラー ID: BC32101  
  
### このエラーを解決するには  
  
-   冗長な `Class` キーワードがある場合は削除します。 制約リストには 1 つだけ含める必要があります。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)