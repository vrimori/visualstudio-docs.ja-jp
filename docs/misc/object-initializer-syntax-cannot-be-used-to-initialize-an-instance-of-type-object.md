---
title: "オブジェクト初期化子の構文は、&#39;Object&#39; 型のインスタンスを初期化するためには使用できません | Microsoft Docs"
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
  - "bc30994"
  - "vbc30994"
helpviewer_keywords: 
  - "BC30994"
ms.assetid: 2ef65965-f014-4fc1-8c7d-c603f0a764df
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# オブジェクト初期化子の構文は、&#39;Object&#39; 型のインスタンスを初期化するためには使用できません
オブジェクト初期化子の構文を使用して、`Object` のインスタンスを初期化することはできません。`Object` のインスタンスには値を割り当てられるプロパティやフィールドが含まれていません。オブジェクト初期化子の構文には、このようなプロパティかフィールドが少なくとも 1 つ必要です。  
  
```  
' Not valid. ' Dim obj1 = New Object With {} ' Dim obj2 = New Object With {.ToString = <some value>}  
```  
  
 **エラー ID:** BC30994  
  
### このエラーを解決するには  
  
1.  `Object` 型のインスタンスを、初期化子リストを使用せずに宣言します。  
  
    ```  
    Dim obj3 as Object Dim obj4 as New Object()  
    ```  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type)