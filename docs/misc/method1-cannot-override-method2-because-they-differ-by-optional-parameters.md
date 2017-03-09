---
title: "省略可能なパラメーターのみが異なるため、&#39;&lt;method1&gt;&#39; で &#39;&lt;method2&gt;&#39; をオーバーライドすることはできません | Microsoft Docs"
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
  - "vbc30308"
  - "bc30308"
helpviewer_keywords: 
  - "BC30308"
ms.assetid: 591dc351-4b87-4e92-81e1-2c1ff51da295
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 省略可能なパラメーターのみが異なるため、&#39;&lt;method1&gt;&#39; で &#39;&lt;method2&gt;&#39; をオーバーライドすることはできません
元のメソッドとは省略可能なパラメーターの値が異なる \(つまり、シグネチャが異なる\) 別のメソッドを使用してメソッドをオーバーライドしようとしました。 型は、継承されたオーバーライド可能なメソッドをオーバーライドできますが、その場合は、名前とシグネチャが同じメソッドを宣言し、宣言に `Overrides` 修飾子でマークを付けます。  
  
 **エラー ID:** BC30308  
  
### このエラーを解決するには  
  
-   2 つのメソッドのシグネチャが同じであることを確認します。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)