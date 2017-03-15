---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、そのコンテナー &#39;&lt;classname2&gt;&#39; が &#39;Public&#39; と宣言されていないため、&#39;&lt;classname1&gt;&#39; に適用できません | Microsoft Docs"
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
  - "vbc32504"
  - "bc32504"
helpviewer_keywords: 
  - "BC32504"
ms.assetid: 4138b639-88d6-4b51-afcd-c92a1be36f1c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、そのコンテナー &#39;&lt;classname2&gt;&#39; が &#39;Public&#39; と宣言されていないため、&#39;&lt;classname1&gt;&#39; に適用できません
`COMClassAttribute` 属性ブロックを使用するクラスが、`Public` ではないクラスの内部で宣言されています。 クラスを COM オブジェクトとして公開する場合は、そのコンテインメント階層全体を `Public` アクセスで宣言する必要があります。  
  
 **エラー ID:** BC32504  
  
### このエラーを解決するには  
  
-   クラスを含むすべてを `Public` として宣言するか、`COMClassAttribute` 属性ブロックを削除します。  
  
## 参照  
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute クラス](http://msdn.microsoft.com/ja-jp/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)