---
title: "型パラメーター &#39;&lt;typeparametername&gt;&#39; には、クラスの制約を 1 つだけ指定できます。 | Microsoft Docs"
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
  - "bc32047"
  - "vbc32047"
helpviewer_keywords: 
  - "BC32047"
ms.assetid: ac7ab76b-5300-4c79-b519-5a1287ed5fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーター &#39;&lt;typeparametername&gt;&#39; には、クラスの制約を 1 つだけ指定できます。
制約リストに複数のクラスが含まれています。  
  
 型パラメーターの制約リストは、任意の数のインターフェイスを受け付けることができます。ただし、クラスは最大 1 つです。 その型パラメーターに指定された型引数は、そのクラスから継承する必要があります。また、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は複数の継承をサポートしません。  
  
 **エラー ID:** BC32047  
  
### このエラーを解決するには  
  
-   1 つのクラスを選び、制約リストにそのクラスのみを含めます。  
  
-   この制約リストに含めることができなかった 1 つまたは複数のクラスに対応する追加の型パラメーターを定義することができます。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)