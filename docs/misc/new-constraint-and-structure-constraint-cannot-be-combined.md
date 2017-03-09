---
title: "&#39;New&#39; 制約と &#39;Structure&#39; 制約は、組み合わせて使用できません | Microsoft Docs"
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
  - "bc32103"
  - "vbc32103"
helpviewer_keywords: 
  - "BC32103"
ms.assetid: 5418b420-a014-4006-84aa-20ddac6739e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; 制約と &#39;Structure&#39; 制約は、組み合わせて使用できません
制約リストに [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator) 制約と [Structure \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) 制約の両方が含まれています。  
  
 型パラメーターの制約リストには、その型パラメーターに渡される型引数が値型でなければならない \(`Structure` 制約を使用\)、または参照型でなければならない \([Class \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 制約を使用\) ことを指定できます。 同じ型パラメーターに両方の制約を指定することはできません。また、どちらも複数回指定することはできません。  
  
 `New` 制約では、型引数は作成元のコードがアクセスできるパラメーターなしのコンストラクターを公開する必要があることを指定します。 ただし、構造体は非共有のパラメーターなしコンストラクターを持つことができません。 このため、`New` 制約と `Structure` 制約を同時に使用すると衝突します。  
  
 **エラー ID:** BC32103  
  
### このエラーを解決するには  
  
1.  型引数に値型と参照型のどちらを使用するかを判断します。  
  
2.  型引数を値型にする場合は、制約リストから `New` キーワードを削除します。  
  
3.  型引数を参照型にする場合は、制約リストから `Structure` キーワードを削除します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)