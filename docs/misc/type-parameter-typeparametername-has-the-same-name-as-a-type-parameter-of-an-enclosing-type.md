---
title: "型パラメーター &#39;&lt;typeparametername&gt;&#39; には、それを囲む型の型パラメーターと同じ名前が付けられています | Microsoft Docs"
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
  - "vbc40048"
  - "bc40048"
helpviewer_keywords: 
  - "BC40048"
ms.assetid: d5428b36-88d3-42c4-a096-cbc7bb9571f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーター &#39;&lt;typeparametername&gt;&#39; には、それを囲む型の型パラメーターと同じ名前が付けられています
ジェネリック型の型パラメーターが、それを含むジェネリック型の型パラメーターと同じ名前で宣言されています。  
  
 ジェネリック型の型パラメーター リストでは、各型パラメーターに、次のすべての名前と異なる名前を付ける必要があります。  
  
-   同じ型パラメーター リスト内のその他すべての型パラメーター  
  
-   格納先となるジェネリック型すべての型パラメーター リスト内のすべての型パラメーター  
  
-   ジェネリック型パラメーター自体の名前  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40048  
  
### このエラーを解決するには  
  
-   このヘルプ ページの一覧に示されているすべての名前と異なる名前になるように、型パラメーターの名前を変更します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)