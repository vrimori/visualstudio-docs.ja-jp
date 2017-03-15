---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; は 0 より小さい値を予約するため、&#39;System.Runtime.InteropServices.DispIdAttribute&#39; 値を &#39;&lt;typename&gt;&#39; に適用できません | Microsoft Docs"
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
  - "bc32506"
  - "vbc32506"
helpviewer_keywords: 
  - "BC32506"
ms.assetid: c6f52e1d-45d8-45cb-9ecb-a2f23b3ca779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; は 0 より小さい値を予約するため、&#39;System.Runtime.InteropServices.DispIdAttribute&#39; 値を &#39;&lt;typename&gt;&#39; に適用できません
<xref:System.Runtime.InteropServices.DispIdAttribute> 属性ブロックで、DISPID 値が 0 未満に指定されていますが、この値は、適用先となるクラス専用の関数用に `COMClassAttribute` によって予約されています。  
  
 ディスパッチ識別子 \(DISPID\) は、COM オブジェクトによって公開されるプロパティやメソッドにアクセスする `IDispatch:Invoke` メソッドの引数として COM で使用されます。  
  
 **エラー ID:** BC32506  
  
### このエラーを解決するには  
  
-   `DispIdAttribute` で 0 より大きい DISPID 値を指定します。  
  
## 参照  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [ビルド内にありません: Visual Basic で使用される属性](http://msdn.microsoft.com/ja-jp/22231318-8a40-49af-9245-e0aab723563b)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute クラス](http://msdn.microsoft.com/ja-jp/5c2f0835-9210-47dc-bc59-5c1769953574)