---
title: "配列を &#39;New&#39; で宣言することはできません | Microsoft Docs"
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
  - "vbc30053"
  - "bc30053"
helpviewer_keywords: 
  - "BC30053"
ms.assetid: aa55f3b7-2045-497b-9543-5ec6e2b74fe2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列を &#39;New&#39; で宣言することはできません
`New` キーワードは、配列の宣言の初期化の部分にのみ指定できます。 つまり、`New` は等号 \(`=`\) の右側に配置しなければなりません。このようにして、配列変数に割り当てる新しい配列型を作成できます。  
  
 配列にはクラスの初期化のショートカットがありません。 次の 2 つのコード行はどちらも正しく、同等です。両方とも同じクラスに基づいてオブジェクトを初期化するためです。  
  
```  
Dim formA as Form = New Form Dim formA as New Form  
```  
  
 ただし、配列の初期化では、クラスの初期化と同じショートカットを使用することはできません。  
  
 配列の `New` 句には、かっこ `()` と中かっこ `{}` の両方を含める必要があります。 かっこは新しい型が配列であることを指定し、中かっこは初期化値を提供します。 コンパイラでは、中が空でも \(つまり、配列値を初期化しない場合でも\) 中かっこが必要です。  
  
 **エラー ID:** BC30053  
  
### このエラーを解決するには  
  
-   `Dim myDates() As New Date` などのステートメントを、`Dim myDates() As Date = New Date() {}` などのステートメントに置き換えます。  
  
## 参照  
 [配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)