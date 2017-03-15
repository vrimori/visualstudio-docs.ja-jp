---
title: "属性に Public コンストラクターがないため、この属性を使用できません | Microsoft Docs"
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
  - "vbc30758"
  - "bc30758"
helpviewer_keywords: 
  - "BC30758"
ms.assetid: b72d1ff2-f6b2-4a89-9ac2-8765f77bcc97
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性に Public コンストラクターがないため、この属性を使用できません
使用されている属性のコンストラクターは `Private` で、使用することはできません。  
  
 **エラー ID:** BC30758  
  
### このエラーを解決するには  
  
1.  開発したカスタム属性でこのエラーが発生する場合は、`Sub``New` コンストラクターのアクセス修飾子を `Public` に変更します。  
  
## 参照  
 [ビルド内にありません: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)