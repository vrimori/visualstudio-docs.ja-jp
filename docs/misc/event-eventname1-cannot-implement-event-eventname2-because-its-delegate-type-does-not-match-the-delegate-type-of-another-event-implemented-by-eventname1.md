---
title: "デリゲート型が、&#39;&lt;eventname1&gt;&#39; によって実装されている別のイベントのデリゲート型と一致しないため、イベント &#39;&lt;eventname1&gt;&#39; でイベント &#39;&lt;eventname2&gt;&#39; を実装することはできません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31407"
  - "vbc31407"
helpviewer_keywords: 
  - "BC31407"
ms.assetid: 0b9ffddb-4759-438b-b569-beac7062e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# デリゲート型が、&#39;&lt;eventname1&gt;&#39; によって実装されている別のイベントのデリゲート型と一致しないため、イベント &#39;&lt;eventname1&gt;&#39; でイベント &#39;&lt;eventname2&gt;&#39; を実装することはできません。
イベントのデリゲート型が、別のイベントのデリゲート型と一致しないため、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] でイベントを実装することはできません。 このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。 実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは 2 つ以上のイベントを実装することができます。  
  
 **エラー ID:** BC31407  
  
### このエラーを解決するには  
  
-   イベントを個別に実装します。  
  
## 参照  
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)