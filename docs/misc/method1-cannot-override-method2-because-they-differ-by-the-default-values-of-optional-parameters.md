---
title: "省略可能なパラメーターの既定値のみが異なるため、&#39;&lt;method1&gt;&#39; で &#39;&lt;method2&gt;&#39; をオーバーライドすることはできません | Microsoft Docs"
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
  - "vbc30307"
  - "bc30307"
helpviewer_keywords: 
  - "BC30307"
ms.assetid: c4cf6040-41c3-4650-8eb9-bff063756599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 省略可能なパラメーターの既定値のみが異なるため、&#39;&lt;method1&gt;&#39; で &#39;&lt;method2&gt;&#39; をオーバーライドすることはできません
元のメソッドとは省略可能なパラメーターの既定値が異なる \(つまり、シグネチャが異なる\) 別のメソッドを使用してメソッドをオーバーライドしようとしました。 型は、同じ名前とシグネチャを持つメソッドを宣言して、`Overrides` 修飾子でその宣言をマークすることによって、継承したオーバーライド可能なメソッドをオーバーライドすることがあります。  
  
 **エラー ID:** BC30307  
  
### このエラーを解決するには  
  
-   2 つのメソッドのシグネチャが同じであることを確認します。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [ビルド内にありません: オーバーライド修飾子](http://msdn.microsoft.com/ja-jp/18e8ef02-e79b-470e-837a-46a8f4163d32)