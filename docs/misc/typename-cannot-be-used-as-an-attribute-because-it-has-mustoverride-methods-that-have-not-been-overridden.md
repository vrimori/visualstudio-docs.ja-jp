---
title: "&#39;&lt;typename&gt;&#39; にはオーバーライドされていない &#39;MustOverride&#39; メソッドが含まれているため、属性として使用できません | Microsoft Docs"
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
  - "bc31507"
  - "vbc31507"
helpviewer_keywords: 
  - "BC31507"
ms.assetid: 843643d3-3e81-4ce3-b4df-278882f3954d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; にはオーバーライドされていない &#39;MustOverride&#39; メソッドが含まれているため、属性として使用できません
`MustOverride` メソッドのあるクラスは、属性として使用できません。  
  
 属性クラスの `MustOverride` メンバーを使用できるのは、それらのメンバーをオーバーライドする派生クラスからだけです。  
  
 **エラー ID:** BC31507  
  
### このエラーを解決するには  
  
1.  属性クラスのメンバーから `MustOverride` 修飾子を削除します。  
  
2.  派生クラスで `MustOverride` メンバーを実装し、そのクラスを属性として使用します。  
  
## 参照  
 <xref:System.AttributeUsageAttribute>   
 [NOT IN BUILD: Visual Basic におけるカスタム属性](http://msdn.microsoft.com/ja-jp/d72d8a5c-8f64-4614-b15b-cad66845d047)