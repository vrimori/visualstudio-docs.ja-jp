---
title: "省略可能なパラメータを、型 &#39;&lt;type&gt;&#39; として宣言することはできません。 | Microsoft Docs"
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
  - "bc30423"
  - "vbc30423"
helpviewer_keywords: 
  - "BC30423"
ms.assetid: 972dab8b-d91e-4a89-b822-2b8e4aadd25f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 省略可能なパラメータを、型 &#39;&lt;type&gt;&#39; として宣言することはできません。
省略可能なパラメーターを、構造体のデータ型にすることはできません。  
  
 **エラー ID:** BC30423  
  
### このエラーを解決するには  
  
1.  構造体を省略可能なパラメーターに渡すには、パラメーターを `Object` として宣言します。  
  
2.  `CType` を使用して、プロシージャ内でその構造体型にパラメーターをキャストします。  
  
## 参照  
 [Structures and Classes](/dotnet/visual-basic/programming-guide/language-features/data-types/structures-and-classes)   
 [CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function)