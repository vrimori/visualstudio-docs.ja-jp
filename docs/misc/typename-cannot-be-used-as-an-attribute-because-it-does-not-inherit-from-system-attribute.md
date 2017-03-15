---
title: "&#39;&lt;typename&gt;&#39; は &#39;System.Attribute&#39; から継承していないため、属性として使用できません | Microsoft Docs"
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
  - "vbc31504"
  - "bc31504"
helpviewer_keywords: 
  - "BC31504"
ms.assetid: 37517623-5099-4db9-a461-f2f5daa4957b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; は &#39;System.Attribute&#39; から継承していないため、属性として使用できません
`System.Attribute` から派生していないクラスを使用しようとしました。  
  
 **エラー ID:** BC31504  
  
### このエラーを解決するには  
  
1.  クラスのコードの先頭行に `Imports` ステートメントを追加することによって、`System.Attribute` から派生するクラスとしてカスタム属性を定義します。  
  
## 参照  
 <xref:System.AttributeUsageAttribute>   
 [ビルド内にありません: Visual Basic におけるカスタム属性](http://msdn.microsoft.com/ja-jp/d72d8a5c-8f64-4614-b15b-cad66845d047)