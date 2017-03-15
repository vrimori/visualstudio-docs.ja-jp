---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、既定のプロパティに対して 0 を予約するため、&#39;System.Runtime.InteropServices.DispIdAttribute&#39; 値を &#39;&lt;typename&gt;&#39; に適用することはできません | Microsoft Docs"
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
  - "vbc32505"
  - "bc32505"
helpviewer_keywords: 
  - "BC32505"
ms.assetid: a7d5b948-2d72-48b1-8baf-bfaae36b0128
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; は、既定のプロパティに対して 0 を予約するため、&#39;System.Runtime.InteropServices.DispIdAttribute&#39; 値を &#39;&lt;typename&gt;&#39; に適用することはできません
<xref:System.Runtime.InteropServices.DispIdAttribute> 属性ブロックで、DISPID 値に 0 が指定されています。これは、適用されるクラスの既定のプロパティを表すために `COMClassAttribute` によって予約されています。  
  
 ディスパッチ識別子 \(DISPID\) は、COM オブジェクトによって公開されるプロパティやメソッドにアクセスする `IDispatch:Invoke` メソッドの引数として COM で使用されます。  
  
 **エラー ID:** BC32505  
  
### このエラーを解決するには  
  
-   <xref:System.Runtime.InteropServices.DispIdAttribute> で 0 より大きい DISPID 値を指定します。  
  
## 参照  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute クラス](http://msdn.microsoft.com/ja-jp/5c2f0835-9210-47dc-bc59-5c1769953574)