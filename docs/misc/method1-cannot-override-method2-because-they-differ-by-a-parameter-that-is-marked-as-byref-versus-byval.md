---
title: "&#39;ByRef&#39; と &#39;ByVal&#39; としてマークされているパラメーターが異なるため、&#39;&lt;method1&gt;&#39; で &#39;&lt;method2&gt;&#39; をオーバーライドすることはできません | Microsoft Docs"
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
  - "vbc30398"
  - "bc30398"
helpviewer_keywords: 
  - "BC30398"
ms.assetid: 78d62276-4ad9-4876-8c35-a30c9c195638
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ByRef&#39; と &#39;ByVal&#39; としてマークされているパラメーターが異なるため、&#39;&lt;method1&gt;&#39; で &#39;&lt;method2&gt;&#39; をオーバーライドすることはできません
`ByVal` ではなく `ByRef` でマークされたパラメーターが異なる別のメソッドを使用してメソッドをオーバーライドしようとしました。 オーバーライドされたメンバーには、基底クラスから継承されたメンバーと同じ引数が必要です。  
  
 **エラー ID:** BC30398  
  
### このエラーを解決するには  
  
-   パラメーターを両方とも `ByRef` または `ByVal` にします。  
  
## 参照  
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)