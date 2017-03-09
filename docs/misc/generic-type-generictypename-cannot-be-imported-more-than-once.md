---
title: "ジェネリック型 &#39;&lt;generictypename&gt;&#39; を複数回インポートすることはできません | Microsoft Docs"
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
  - "BC32086"
  - "vbc32086"
helpviewer_keywords: 
  - "BC32086"
ms.assetid: d93bae4b-3224-4a6e-a072-8ce231084519
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ジェネリック型 &#39;&lt;generictypename&gt;&#39; を複数回インポートすることはできません
[Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) では、既にインポートされているジェネリック型を異なる型パラメーターで指定しています。  
  
 構築された型を宣言することでジェネリック型を再定義していないため、ジェネリック型から複数の構築された型を宣言できます。 ただし、ジェネリック型を複数回インポートした場合は、複数の定義が存在することになります。  
  
 **エラー ID:** BC32086  
  
### このエラーを解決するには  
  
1.  この `Imports` ステートメントが含まれているソース ファイルに、同じジェネリック型を指定する別の `Imports` ステートメントも含まれている場合は、それらの 1 つを削除します。  
  
2.  同じジェネリック型を別の型パラメーターでインポートする必要がある場合は、複数のソース ファイルを使用してください。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)