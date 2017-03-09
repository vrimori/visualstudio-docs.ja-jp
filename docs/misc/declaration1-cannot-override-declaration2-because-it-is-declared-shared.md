---
title: "&#39;Shared&#39; として宣言されているため、&#39;&lt;declaration1&gt;&#39; で &#39;&lt;declaration2&gt;&#39; をオーバーライドすることはできません。 | Microsoft Docs"
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
  - "vbc30268"
  - "bc30268"
helpviewer_keywords: 
  - "BC30268"
ms.assetid: d011fb26-6236-462e-9173-622f8bbeb536
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Shared&#39; として宣言されているため、&#39;&lt;declaration1&gt;&#39; で &#39;&lt;declaration2&gt;&#39; をオーバーライドすることはできません。
プロシージャまたはプロパティの宣言は同じ名前の継承された要素をオーバーライドしようとしていますが、継承された要素は `Shared` として指定されています。 共有要素がクラスのインスタンスに関連付けられていないため、共有要素をオーバーライドすることができません。  
  
 **エラー ID:** BC30268  
  
### このエラーを解決するには  
  
-   継承された要素から `Shared` キーワードを削除するか、またはオーバーライドする宣言を削除します。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)