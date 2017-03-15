---
title: "&#39;System.&lt;classname&gt;&#39; からの継承は、有効ではありません | Microsoft Docs"
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
  - "vbc30015"
  - "bc30015"
helpviewer_keywords: 
  - "BC30015"
ms.assetid: b4c005df-a510-47c7-b5cc-27f4514d32b6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.&lt;classname&gt;&#39; からの継承は、有効ではありません
クラスは `System.Array`、`System.Delegate`、`System.Enum`、または `System.ValueType` から継承できません。  
  
 **エラー ID:** BC30015  
  
### このエラーを解決するには  
  
-   `Inherits` ステートメントを削除するか、または有効な基底クラスから継承するように変更します。  
  
## 参照  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Object Variable Declaration](/dotnet/visual-basic/programming-guide/language-features/variables/object-variable-declaration)