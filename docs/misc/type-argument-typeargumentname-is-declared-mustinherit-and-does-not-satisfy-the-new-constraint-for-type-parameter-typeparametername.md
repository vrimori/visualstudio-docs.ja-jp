---
title: "型引数 &#39;&lt;typeargumentname&gt;&#39; は &#39;MustInherit&#39; として宣言され、型パラメーター &#39;&lt;typeparametername&gt;&#39; の &#39;New&#39; 制約を満たしていません | Microsoft Docs"
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
  - "vbc32082"
  - "BC32082"
helpviewer_keywords: 
  - "BC32082"
ms.assetid: 597e5944-a61b-4858-ada5-efb80b27f26b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型引数 &#39;&lt;typeargumentname&gt;&#39; は &#39;MustInherit&#39; として宣言され、型パラメーター &#39;&lt;typeparametername&gt;&#39; の &#39;New&#39; 制約を満たしていません
ジェネリック型が `MustInherit` クラスで型引数として呼び出されているのに対して、対応する型パラメーターは `New` 制約で宣言されています。  
  
 `New` 制約では、対応する型引数に渡される型がオブジェクトの作成をサポートする必要があります。 ただし、*抽象*クラス、つまり `MustInherit` として宣言されたクラスは、オブジェクトの作成元にはできないので、コンストラクターを公開しません。  
  
 **エラー ID:** BC32082  
  
### このエラーを解決するには  
  
1.  型引数で使用されるクラスが抽象クラスである必要がない場合は、`MustInherit` キーワードを宣言から削除します。  
  
2.  型引数で使用されるクラスが抽象クラスである必要があるものの、ジェネリック型の構築に使用する必要はない場合は、型引数に別のクラスを渡します。  
  
3.  対応する型パラメーターが渡された型からオブジェクトを作成する必要がない場合は、`New` 制約を宣言から削除します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)