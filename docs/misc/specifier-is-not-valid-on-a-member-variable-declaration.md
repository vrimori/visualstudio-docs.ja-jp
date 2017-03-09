---
title: "&#39;&lt;specifier&gt;&#39; は、メンバー変数宣言では有効ではありません | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30235"
  - "bc30235"
helpviewer_keywords: 
  - "BC30235"
ms.assetid: 8c5764e4-0096-4ca0-8656-05341a39833a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;specifier&gt;&#39; は、メンバー変数宣言では有効ではありません
`Dim` ステートメントに正しくないキーワードが含まれています。`Dim` ステートメントに含めることができるキーワードは、`Friend`、`Private`、`Protected`、`Public`、`ReadOnly`、`Shadows`、`Shared`、`Static` のみです。  
  
 このメッセージは、プロシージャ外で `Static` 変数を宣言する場合にも表示されることがあります。`Static` はプロシージャ レベルでのみ使用できます。  
  
 `Dim` ステートメントに正しいキーワードを含めた場合、`Dim` キーワードは省略できます。  
  
 **エラー ID:** BC30235  
  
### このエラーを解決するには  
  
1.  `Dim` ステートメントから正しくないキーワードを削除します。  
  
2.  プロシージャ外で `Static` 変数を宣言した場合には、宣言をプロシージャ内に移動するか、`Static` キーワードを削除します。  
  
## 参照  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)