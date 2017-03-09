---
title: "&#39;Double&#39; から &#39;Date&#39; への変換には、&#39;Date.FromOADate&#39; の呼び出しが必要です。 | Microsoft Docs"
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
  - "vbc30533"
  - "bc30533"
helpviewer_keywords: 
  - "BC30533"
ms.assetid: afcfd115-4614-4b0b-ad09-76af8dba2ed5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Double&#39; から &#39;Date&#39; への変換には、&#39;Date.FromOADate&#39; の呼び出しが必要です。
`Date` 値を `Double` 値にキャストしようとしましたが、これは <xref:System.DateTime.FromOADate%2A?displayProperty=fullName> メソッドを使用せずに実行することはできません。  
  
 **エラー ID:** BC30533  
  
### このエラーを解決するには  
  
-   <xref:System.DateTime.FromOADate%2A> メソッドを使用して値を変換します。  
  
## 参照  
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)