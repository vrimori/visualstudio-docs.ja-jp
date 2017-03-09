---
title: "&#39;MyBase&#39; の後には &#39;.&#39; および識別子を指定する必要があります | Microsoft Docs"
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
  - "bc32027"
  - "vbc32027"
helpviewer_keywords: 
  - "BC32027"
ms.assetid: 39e5512c-ef1e-46a3-a96c-277ea24bfee2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MyBase&#39; の後には &#39;.&#39; および識別子を指定する必要があります
`MyBase` は真のオブジェクト変数ではないため、単独では使用できません。 現在のインスタンスの基底クラスのメンバーにアクセスする場合にのみこれを使用します。  
  
 **エラー ID:** BC32027  
  
### このエラーを解決するには  
  
-   メンバーにアクセスする場合は、メンバー アクセス演算子 \(.\) と  の後に基底クラスのメンバーを指定します。  
  
-   メンバーにアクセスしない場合は、基底クラスのインスタンスを宣言して初期化するか、`MyBase` への参照を削除します。  
  
## 参照  
 [MyBase \- delete](http://msdn.microsoft.com/ja-jp/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)