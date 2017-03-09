---
title: "キャスト演算子の構文エラーです。コンマで区切られた 2 つの引数が必要です | Microsoft Docs"
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
  - "vbc30944"
  - "bc30944"
helpviewer_keywords: 
  - "BC30944"
ms.assetid: 1f7ed4a1-6ff5-4836-8424-21618c68ff45
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# キャスト演算子の構文エラーです。コンマで区切られた 2 つの引数が必要です
式は `CType` 変換関数か `DirectCast` または `TryCast` 変換キーワードを使用しますが、引数は 1 つのみ指定されています。  
  
 `CType`、`DirectCast`、および `TryCast` はすべて 2 つの引数を必要とします。 1 つ目は変換される式で、2 つ目は変換先のデータ型またはクラス型です。  
  
 **エラー ID:** BC30944  
  
### このエラーを解決するには  
  
-   変換に必要な引数を両方とも指定します。  
  
-   `CString` などの特定の [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions) の 1 つを使用する場合、`CType` の代わりにその関数名を使用する必要があります。 次に、ただ 1 つの引数が必要です。  
  
## 参照  
 [CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)