---
title: "&#39;Assembly&#39; または &#39;Module&#39; が必要です | Microsoft Docs"
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
  - "vbc32015"
  - "bc32015"
helpviewer_keywords: 
  - "BC32015"
ms.assetid: 6e62fe8d-a875-4995-b6b2-443e75c65e85
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Assembly&#39; または &#39;Module&#39; が必要です
グローバル属性が指定されていますが、アセンブリ全体に適用するか、または現在のモジュールにのみ適用するかが指定されていません。 グローバル属性では、`Assembly` または `Module` のいずれかを指定する必要があります。  
  
 グローバル属性は、特定のプログラミング要素の宣言に適用されるのではなく、単独でソース行に出現する属性です。  
  
 **エラー ID:** BC32015  
  
### このエラーを解決するには  
  
1.  属性をグローバルにする場合は、`Assembly` または `Module` キーワードを属性ブロックの先頭に追加し、その後にコロン \(:\) を入力します。  
  
2.  属性をグローバルにしない場合は、属性ブロックを削除するか、プログラミング要素の宣言に移動します。  
  
## 参照  
 [Assembly](/dotnet/visual-basic/language-reference/modifiers/assembly)   
 [Module \<keyword\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ビルド内にありません: Visual Basic におけるグローバル属性](http://msdn.microsoft.com/ja-jp/253a32d8-1531-4504-b687-088554ab71d2)