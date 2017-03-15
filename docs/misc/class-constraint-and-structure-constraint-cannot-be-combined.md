---
title: "&#39;Class&#39; 制約と &#39;Structure&#39; 制約は、組み合わせて使用できません | Microsoft Docs"
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
  - "vbc32104"
  - "bc32104"
helpviewer_keywords: 
  - "BC32104"
ms.assetid: f41a581b-afca-4173-bc82-b35ed49caba0
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Class&#39; 制約と &#39;Structure&#39; 制約は、組み合わせて使用できません
制約リストに、[クラス \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 制約と[構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) 制約の両方が含まれています。  
  
 型パラメーターの制約リストでは、その型パラメーターに渡される型引数が値型である必要があるか \(`Structure` 制約による\)、参照型である必要があるか \(`Class` 制約による\) を指定できます。 同じ型パラメーターに両方の制約を指定することはできません。また、どちらも複数回指定することはできません。  
  
 **エラー ID:** BC32104  
  
### このエラーを解決するには  
  
1.  型引数に値型または参照型のどちらを必要とするかを決定します。  
  
    -   型引数を値型にする場合は、制約リストから `Class` キーワードを削除します。  
  
    -   型引数を参照型にする場合は、制約リストから `Structure` キーワードを削除します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)