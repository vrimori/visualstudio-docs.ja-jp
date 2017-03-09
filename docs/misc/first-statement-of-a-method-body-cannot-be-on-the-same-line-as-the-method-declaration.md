---
title: "メソッド本体の最初のステートメントをメソッド宣言と同じ行に記述することはできません | Microsoft Docs"
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
  - "vbc30040"
  - "bc30040"
helpviewer_keywords: 
  - "BC30040"
ms.assetid: 27df3488-de77-499d-b9a6-08037d540cb0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド本体の最初のステートメントをメソッド宣言と同じ行に記述することはできません
`Function`、`Sub`、`Get`、`Set`、または `Property` ステートメントは、ソース コード行に単独で記述する必要があります。  
  
 **エラー ID:** BC30040  
  
### このエラーを解決するには  
  
1.  プロシージャ宣言の前にある行ラベルを削除します。  
  
2.  プロシージャ宣言の前にあるステートメントを前のソース コード行に移動します。  
  
3.  プロシージャ宣言の後に続くステートメントを後のソース コード行に移動します。  
  
## 参照  
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)   
 [How to: Label Statements](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)