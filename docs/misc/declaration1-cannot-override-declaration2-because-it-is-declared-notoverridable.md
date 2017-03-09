---
title: "&#39;NotOverridable&#39; に宣言されているので、&#39;&lt;declaration1&gt;&#39; は &#39;&lt;declaration2&gt;&#39; をオーバーライドすることができません | Microsoft Docs"
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
  - "bc30267"
  - "vbc30267"
helpviewer_keywords: 
  - "BC30267"
ms.assetid: fb1f6797-4e49-442e-a660-59d602132631
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;NotOverridable&#39; に宣言されているので、&#39;&lt;declaration1&gt;&#39; は &#39;&lt;declaration2&gt;&#39; をオーバーライドすることができません
プロシージャまたはプロパティの宣言は同じ名前の継承された要素をオーバーライドしようとしていますが、継承された要素は `NotOverridable` として指定されています。  
  
 **エラー ID:** BC30267  
  
### このエラーを解決するには  
  
-   継承された要素の宣言から `NotOverridable` キーワードを削除するか、またはオーバーライドする宣言を削除します。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)