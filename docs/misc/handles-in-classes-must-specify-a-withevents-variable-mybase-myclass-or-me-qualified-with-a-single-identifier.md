---
title: "クラスの &#39;Handles&#39; は、単一の識別子で限定された &#39;WithEvents&#39; 変数、&#39;MyBase&#39;、&#39;MyClass&#39; または &#39;Me&#39; を指定しなければなりません。 | Microsoft Docs"
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
  - "bc31412"
  - "vbc31412"
helpviewer_keywords: 
  - "BC31412"
ms.assetid: acbefc38-448a-4afa-90c2-77389415d618
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# クラスの &#39;Handles&#39; は、単一の識別子で限定された &#39;WithEvents&#39; 変数、&#39;MyBase&#39;、&#39;MyClass&#39; または &#39;Me&#39; を指定しなければなりません。
イベント ハンドラーを指定するためには、`Handles` ステートメントに、`WithEvents` キーワードで宣言されたオブジェクト変数、または `MyBase` キーワードで限定されたメンバーを指定する必要があります。  
  
 **エラー ID:** BC31412  
  
### このエラーを解決するには  
  
1.  `Handles` ステートメントで使用する変数を、`WithEvents` 修飾子を使用して宣言します。  
  
2.  基底クラスの現在のクラスのイベントの名前を指定します。  
  
## 参照  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)