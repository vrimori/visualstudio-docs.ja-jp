---
title: "CA1308: 文字列を大文字に標準化します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1308: 文字列を大文字に標準化します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 演算で文字列が小文字に正規化されます。  
  
## 規則の説明  
 文字列は大文字に正規化する必要があります。  小文字への変換時に 1 つの小さい文字グループをラウンド トリップさせることができません。  ラウンド トリップとは、あるロケールから、他の方法で文字データを表す別のロケールに文字を変換し、変換された文字から元の文字を正確に取得することを示します。  
  
## 違反の修正方法  
 文字列を小文字に変換する演算を変更して、文字列が大文字に変換されるようにします。  たとえば、`String.ToLower(CultureInfo.InvariantCulture)` を `String.ToUpper(CultureInfo.InvariantCulture)` に変更します。  
  
## 警告を抑制する状況  
 結果に基づいてセキュリティ上の決定を行わない場合 \(UI に警告メッセージを表示するときなど\) は、警告メッセージを抑制しても安全です。  
  
## 参照  
 [グローバリゼーションの警告](../code-quality/globalization-warnings.md)