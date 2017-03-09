---
title: "型パラメーターは名前 &#39;&lt;typeparametername&gt;&#39; で既に宣言されています。 | Microsoft Docs"
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
  - "vbc32049"
  - "bc32049"
helpviewer_keywords: 
  - "BC32049"
ms.assetid: d7affad0-0c3d-4fce-a1c2-a17f65514471
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーターは名前 &#39;&lt;typeparametername&gt;&#39; で既に宣言されています。
ジェネリック型の型パラメーターが、その同じジェネリック型の別の型パラメーターと同じ名前で宣言されています。  
  
 ジェネリック型の型パラメーター リストでは、各型パラメーターに、次のすべての名前と異なる名前を付ける必要があります。  
  
-   同じ型パラメーター リスト内のその他すべての型パラメーター  
  
-   格納先となるジェネリック型すべての型パラメーター リスト内のすべての型パラメーター  
  
-   ジェネリック型パラメーター自体の名前  
  
 **エラー ID:** BC32049  
  
### このエラーを解決するには  
  
-   このヘルプ ページの一覧に示されているすべての名前と異なる名前になるように、型パラメーターの名前を変更します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)