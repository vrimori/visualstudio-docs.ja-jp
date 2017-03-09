---
title: "構造体のメソッド内にあるローカル変数を &#39;Static&#39; と宣言することはできません | Microsoft Docs"
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
  - "vbc31400"
  - "bc31400"
helpviewer_keywords: 
  - "BC31400"
ms.assetid: 38b8adee-3593-40fb-b0a4-e2a47599567f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 構造体のメソッド内にあるローカル変数を &#39;Static&#39; と宣言することはできません
構造体内のローカル変数には `Static` 修飾子を使用できません。  
  
 **エラー ID:** BC31400  
  
### このエラーを解決するには  
  
1.  ローカル変数から `Static` 修飾子を削除します。  
  
2.  より広いスコープを持つ静的変数として変数を宣言します。  
  
## 参照  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)