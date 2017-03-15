---
title: "ジェネリック メソッド内のローカル変数には &#39;Static&#39; を宣言できません | Microsoft Docs"
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
  - "vbc32068"
  - "bc32068"
helpviewer_keywords: 
  - "BC32068"
ms.assetid: cb5df484-76f9-4092-9d19-f26ddcf1c035
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ジェネリック メソッド内のローカル変数には &#39;Static&#39; を宣言できません
ジェネリック プロシージャ内のローカル変数の宣言で `Static` を指定してします。  
  
 Visual Basic と .NET Framework は、静的変数とジェネリック プロシージャの組み合わせを現在サポートしていません。  
  
 **エラー ID:** BC32068  
  
### このエラーを解決するには  
  
-   変数宣言から `Static` キーワードを削除します。  
  
## 参照  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)   
 [ビルド内にありません: 方法: 変数の有効期間を延長する](http://msdn.microsoft.com/ja-jp/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)