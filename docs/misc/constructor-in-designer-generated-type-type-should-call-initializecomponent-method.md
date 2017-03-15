---
title: "デザイナーで生成された型 &#39;&lt;type&gt;&#39; の &#39;&lt;constructor&gt;&#39; は、InitializeComponent メソッドを呼び出す必要があります | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40054"
  - "bc40054"
helpviewer_keywords: 
  - "BC40054"
ms.assetid: beac93b0-d427-4df6-9582-fd69c7a53673
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# デザイナーで生成された型 &#39;&lt;type&gt;&#39; の &#39;&lt;constructor&gt;&#39; は、InitializeComponent メソッドを呼び出す必要があります
デザイナーで生成される型のコンストラクターが、この型の `InitializeComponent` メソッドを呼び出しません。  
  
 デザイナーで生成される型の各コンストラクターは、その型の `InitializeComponent` メソッドを呼び出す必要があります。  
  
 **エラー ID:** BC40054  
  
### このエラーを解決するには  
  
-   コンストラクター内の `InitializeComponent` メソッドに呼び出しを追加します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute>   
 [ビルド内にありません: コンストラクタとデストラクタの使用方法](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)