---
title: "型引数 &#39;&lt;typeargumentname&gt;&#39; は型パラメーター &#39;&lt;typeparametername&gt;&#39; の &#39;Class&#39; 制約を満たしていません | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32106"
  - "bc32106"
helpviewer_keywords: 
  - "BC32106"
ms.assetid: 1bac1dd6-f86b-4e98-ba2d-57d1936e3658
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型引数 &#39;&lt;typeargumentname&gt;&#39; は型パラメーター &#39;&lt;typeparametername&gt;&#39; の &#39;Class&#39; 制約を満たしていません
ジェネリック型に指定された型引数は、対応する型パラメーターの参照型の制約を満たしていません。  
  
 制約リストでは、型パラメーターに渡される型引数の要件が適用されます。 制約リストに特定のクラスまたはインターフェイスを何も含めない場合は、次のいずれかを指定することによって一般的な要件を設定できます。  
  
-   型引数は値型 \([構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) 制約を含む\) にする必要があります  
  
-   型引数は参照型 \([クラス \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 制約を含む\) にする必要があります  
  
 同じ型パラメーターに `Structure` と `Class` の両方を指定することはできません。また、どちらも複数回指定することはできません。  
  
 **エラー ID:** BC32106  
  
### このエラーを解決するには  
  
-   任意の参照型の型引数を選択します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [方法 : ジェネリック クラスを使用する](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)