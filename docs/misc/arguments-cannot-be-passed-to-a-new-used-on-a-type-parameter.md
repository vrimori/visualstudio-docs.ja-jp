---
title: "型パラメーターで使用される &#39;New&#39; に引数を渡すことはできません | Microsoft Docs"
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
  - "BC32085"
  - "vbc32085"
helpviewer_keywords: 
  - "BC32085"
ms.assetid: a60bf62d-2b2e-4621-b8db-e67720b918fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーターで使用される &#39;New&#39; に引数を渡すことはできません
宣言ステートメントまたは代入ステートメントはジェネリック型を呼び出し、[New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) 制約がある型パラメーターにコンストラクター引数を指定します。  
  
 型パラメーターの制約リストは、その型パラメーターに渡される型引数が、作成元のコードでアクセスできるパラメーターなしのコンストラクターを公開する必要があることを指定できます。 型パラメーターは、パラメーターを受け取るコンストラクターを要求することはできません。また、`New` 制約がある型パラメーターは、このようなコンストラクターを受け入れることができません。  
  
 **エラー ID:** BC32085  
  
### このエラーを解決するには  
  
-   ジェネリック型を呼び出すステートメントの型引数に続く引数リストを削除します。 コンストラクター引数を対応する型パラメーターに渡すことはできません。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)