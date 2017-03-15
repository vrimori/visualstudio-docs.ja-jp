---
title: "CA1504: 紛らわしいフィールド名を確認します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1504: 紛らわしいフィールド名を確認します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|分類|Microsoft.Maintainability|  
|互換性に影響する変更点|なし|  
  
## 原因  
 インスタンス フィールドの名前が "s\_" で始まっているか、`static` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では `Shared`\) フィールドの名前が "m\_" で始まっています。  
  
## 規則の説明  
 多くのユーザーは、"s\_" で始まるフィールド名からは静的データを連想し、  "m\_" で始まるフィールド名からはインスタンス \(メンバー\) データを連想します。  コードの保守を容易にするために、一般的な規則に従って名前を付けてください。  
  
## 違反の修正方法  
 この規則違反を修正するには、フィールド名のプレフィックスを適切に変更します。  または、`static` 修飾子の追加または削除により、現在のサフィックスに合致するフィールドに変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。