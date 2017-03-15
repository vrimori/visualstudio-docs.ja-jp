---
title: "&lt;type1&gt; &#39;&lt;typename&gt;&#39; は、基底 &lt;type2&gt; で &lt;type1&gt; をオーバーライドしていないため、&#39;Overrides&#39; として宣言できません | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30284"
  - "bc30284"
helpviewer_keywords: 
  - "BC30284"
ms.assetid: 8166bd09-dad3-495d-8cf7-66f90824a288
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;typename&gt;&#39; は、基底 &lt;type2&gt; で &lt;type1&gt; をオーバーライドしていないため、&#39;Overrides&#39; として宣言できません
`Sub`、`Function`、`Property` のいずれかのステートメントに `Overrides` を指定していますが、同じ名前の型が基底クラスに存在しません。  
  
 **エラー ID:** BC30284  
  
### このエラーを解決するには  
  
1.  型名のスペルが正しいことを確認します。  
  
2.  余分な `Overrides` キーワードを削除します。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)