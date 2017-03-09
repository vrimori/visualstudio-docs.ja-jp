---
title: "制約型 &#39;&lt;typename&gt;&#39; は、既にこの型パラメーターに指定しています | Microsoft Docs"
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
  - "BC32071"
  - "vbc32071"
helpviewer_keywords: 
  - "BC32071"
ms.assetid: 6b0e85e9-3ac8-4181-97de-ca690b95a63c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 制約型 &#39;&lt;typename&gt;&#39; は、既にこの型パラメーターに指定しています
制約リストにクラスまたはインターフェイス制約が 2 回以上含まれています。  
  
 制約リストでは、型パラメーターに渡される型引数の要件が適用されます。 次の要件を任意の組み合わせで指定できます。  
  
-   型引数はインターフェイスを実装する必要があります  
  
-   型引数は、最大で 1 つのクラスから継承する必要があります  
  
 1 つの型で同じ型を 2 回以上実装または継承することはできません。また、同じ制約リストに特定の型を 2 回以上指定することはできません。  
  
 **エラー ID:** BC32071  
  
### このエラーを解決するには  
  
-   同じクラスまたはインターフェイスの重複した指定を削除します。 制約リストで重複して指定することはできません。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)