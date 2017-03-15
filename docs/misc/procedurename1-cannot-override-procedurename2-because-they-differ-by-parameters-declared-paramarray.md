---
title: "&#39;ParamArray&#39; として宣言されたパラメーターが異なるため、&lt;procedurename1&gt; は &lt;procedurename2&gt; をオーバーライドできません | Microsoft Docs"
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
  - "bc30906"
  - "vbc30906"
helpviewer_keywords: 
  - "BC30906"
ms.assetid: 12939030-732e-4c6d-8fe9-707b7532174b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ParamArray&#39; として宣言されたパラメーターが異なるため、&lt;procedurename1&gt; は &lt;procedurename2&gt; をオーバーライドできません
派生クラス内のプロシージャは、基底クラスで同じ名前を持つプロシージャをオーバーライドしますが、パラメーター リストが異なります。  
  
 継承クラスでプロシージャをオーバーライドするには、オーバーライド元のプロシージャがパラメーター リスト、アクセス レベル、および戻り値の型 \(存在する場合\) と一致する必要があります。 特に、[Optional](/dotnet/visual-basic/language-reference/modifiers/optional) または [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray) 宣言と一致する必要があります。  
  
 **エラー ID:** BC30906  
  
### このエラーを解決するには  
  
-   プロシージャをオーバーライドする場合は、パラメーター リストを基底クラスのプロシージャのパラメーター リストとまったく同じものにします。 最後のパラメーターを基底クラスのプロシージャで `ParamArray` を指定して宣言している場合は、そのパラメーターをオーバーライド元のプロシージャで `ParamArray` を指定して宣言します。  
  
-   基底クラスのバージョンとは異なるパラメーター リストが必要である場合は、オーバーライドできません。 代わりにオーバーロードすることを検討してください。 詳細については、「[Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)」を参照してください。  
  
## 参照  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [ビルド内にありません: プロパティとメソッドのオーバーライド](http://msdn.microsoft.com/ja-jp/2167e8f5-1225-4b13-9ebd-02591ba90213)