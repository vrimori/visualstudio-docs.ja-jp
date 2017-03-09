---
title: "型引数 &#39;&lt;typeargumentname&gt;&#39; が制約型 &#39;&lt;typeparametername&gt;&#39; を継承していないか、実装していません。 | Microsoft Docs"
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
  - "bc32044"
  - "vbc32044"
helpviewer_keywords: 
  - "BC32044"
ms.assetid: be91f648-c07d-4991-8ed1-28b1327619c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型引数 &#39;&lt;typeargumentname&gt;&#39; が制約型 &#39;&lt;typeparametername&gt;&#39; を継承していないか、実装していません。
ジェネリック型に指定された型引数が、対応する型パラメーターの継承または実装の制約を満たしていません。  
  
 制約リストでは、型パラメーターに渡される型引数の要件が適用されます。 考えられる要件を以下に示します。  
  
-   型引数はインターフェイスを実装する必要があります  
  
-   型引数は、最大で 1 つのクラスから継承する必要があります  
  
 1 つの型パラメーターに上記の要件を組み合わせることができます。 コードがジェネリック型で定義されているすべての型パラメーターの制約を満たす型引数を指定しない限り、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は型を構築できません。  
  
 **エラー ID:** BC32044  
  
### このエラーを解決するには  
  
-   型パラメーターに指定されたすべてのインターフェイスを実装し、指定したクラスがある場合にはその 1 つを継承する型の型引数を選択します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [方法 : ジェネリック クラスを使用する](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)