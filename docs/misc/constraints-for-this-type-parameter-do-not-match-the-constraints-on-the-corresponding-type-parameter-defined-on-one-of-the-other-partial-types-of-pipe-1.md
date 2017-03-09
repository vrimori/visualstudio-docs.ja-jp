---
title: "この型パラメーターの制約は、&#39;|1&#39; のその他の部分型の 1 つで定義された、対応する型パラメーター上の制約と一致しません | Microsoft Docs"
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
  - "vbc30932"
  - "bc30932"
helpviewer_keywords: 
  - "BC30932"
ms.assetid: a38ca4ad-6bbf-421e-a0d7-c5e0a9029160
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# この型パラメーターの制約は、&#39;|1&#39; のその他の部分型の 1 つで定義された、対応する型パラメーター上の制約と一致しません
クラスまたは構造体の定義を複数の宣言間で分割する際、コンパイラは、そのすべての部分宣言の和集合としてこのクラスまたは構造体を処理します。 このため、さまざまな部分宣言で競合する修飾子または型パラメーター リストを定義できません。  
  
 **エラー ID:** BC30932  
  
### このエラーを解決するには  
  
1.  クラスまたは構造体に必要なパラメーター リストを特定します。 これには、パラメーター、その順序、および制約リストが含まれます。  
  
2.  すべての部分定義で同じ型パラメーター リストを使用していることを確認します。  
  
## 参照  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)