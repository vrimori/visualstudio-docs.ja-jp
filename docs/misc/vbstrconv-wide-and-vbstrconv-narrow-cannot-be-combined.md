---
title: "VbStrConv.Wide と VbStrConv.Narrow を組み合わせることはできません | Microsoft Docs"
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
  - "vbrArgument_IllegalWideNarrow"
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# VbStrConv.Wide と VbStrConv.Narrow を組み合わせることはできません
アプリケーションが `VbStrConv` 列挙型メンバー `Wide` と `Narrow` を結合しようとしていますが、これらは相互に排他的です。  
  
### このエラーを解決するには  
  
1.  `VbStrConv.Wide` または `VbStrConv.Narrow` のいずれかを削除します。  
  
## 参照  
 <xref:System.Globalization>   
 [ビルド内にありません: VbStrConv 列挙型](http://msdn.microsoft.com/ja-jp/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [.NET Framework ベースの国際対応アプリケーションの概要](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)