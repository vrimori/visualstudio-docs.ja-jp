---
title: "戻り値の型が異なるため、&#39;&lt;method1&gt;&#39; で &#39;&lt;method2&gt;&#39; をオーバーライドすることはできません。 | Microsoft Docs"
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
  - "bc30437"
  - "vbc30437"
helpviewer_keywords: 
  - "BC30437"
ms.assetid: e566ae72-c597-4b33-b70d-5d4ea879d644
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 戻り値の型が異なるため、&#39;&lt;method1&gt;&#39; で &#39;&lt;method2&gt;&#39; をオーバーライドすることはできません。
戻り値の型が異なる別のメソッドを使用してメソッドをオーバーライドしようとしました。 型は、同じ名前とシグネチャを持つメソッドを宣言し、`Overrides` 修飾子でその宣言をマークして、継承したオーバーライド可能なメソッドをオーバーライドできます。 2 つのメソッドのシグネチャが一致する必要があります。  
  
 **エラー ID:** BC30437  
  
### このエラーを解決するには  
  
-   2 つのメソッドの戻り値の型を確認し、必要があれば一致するように変更します。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)