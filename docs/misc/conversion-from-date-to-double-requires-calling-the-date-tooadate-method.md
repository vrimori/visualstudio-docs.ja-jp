---
title: "&#39;Date&#39; から &#39;Double&#39; への変換には、&#39;Date.ToOADate&#39; メソッドの呼び出しが必要です | Microsoft Docs"
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
  - "bc30532"
  - "vbc30532"
helpviewer_keywords: 
  - "BC30532"
ms.assetid: 8171ce21-e4f6-4e75-b7e8-32baf78a40eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Date&#39; から &#39;Double&#39; への変換には、&#39;Date.ToOADate&#39; メソッドの呼び出しが必要です
`Date` 値を `Double` 値にキャストしようとしましたが、これは <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> メソッドを使用せずに実行することはできません。  
  
 **エラー ID:** BC30532  
  
### このエラーを解決するには  
  
-   <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> メソッドを使用して値を変換します。  
  
## 参照  
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)