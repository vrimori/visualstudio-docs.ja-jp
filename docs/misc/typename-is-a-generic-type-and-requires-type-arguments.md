---
title: "&#39;&lt;typename&gt;&#39; はジェネリック型であり、型引数を必要とします | Microsoft Docs"
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
  - "BC32076"
  - "vbc32076"
helpviewer_keywords: 
  - "BC32076"
ms.assetid: 57f63727-c544-4012-8f03-5d77fbdd1135
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; はジェネリック型であり、型引数を必要とします
ジェネリック クラスまたは構造体の型を持つように変数、プロシージャ パラメーター、または関数の戻り値が宣言されていますが、宣言に型引数が何も指定されていません。  
  
 すべてのジェネリックなクラスおよび構造体は、その性質上、少なくとも 1 つの型パラメーターを使って定義されます。 構成されるクラスまたは構造体をジェネリック型で宣言する場合、そのジェネリック型で定義されるすべての型パラメーターに対して型引数を指定する必要があります。  
  
 **エラー ID:** BC32076  
  
### このエラーを解決するには  
  
-   型リストをかっこで囲んで、先頭に `Of` キーワードを付けて、宣言に追加します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)