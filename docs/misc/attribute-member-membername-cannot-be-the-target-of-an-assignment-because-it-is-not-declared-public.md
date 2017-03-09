---
title: "属性メンバー &#39;&lt;membername&gt;&#39; は &#39;Public&#39; と宣言されていないため、代入式のターゲットにすることはできません。 | Microsoft Docs"
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
  - "vbc31511"
  - "bc31511"
helpviewer_keywords: 
  - "BC31511"
ms.assetid: f8c958f6-58a4-4aff-b8c3-f2e9481e8132
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性メンバー &#39;&lt;membername&gt;&#39; は &#39;Public&#39; と宣言されていないため、代入式のターゲットにすることはできません。
属性のプライベート メンバーに値を代入しようとしました。  
  
 **エラー ID:** BC31511  
  
### このエラーを解決するには  
  
1.  代入を削除します。  
  
2.  開発したカスタム属性を使用する場合は、属性メンバーのアクセス修飾子を `Public` に変更します。  
  
## 参照  
 [ビルド内にありません: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)