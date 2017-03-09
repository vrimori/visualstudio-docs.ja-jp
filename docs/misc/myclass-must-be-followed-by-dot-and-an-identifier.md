---
title: "&#39;MyClass&#39; の後には &#39;.&#39; および識別子を指定しなければなりません | Microsoft Docs"
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
  - "bc32028"
  - "vbc32028"
helpviewer_keywords: 
  - "BC32028"
ms.assetid: a7e92b54-32b8-4072-9576-632942f05e0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MyClass&#39; の後には &#39;.&#39; および識別子を指定しなければなりません
`MyClass` は真のオブジェクト変数ではないため、単独では使用できません。 現在のインスタンスのメンバーにアクセスする場合にのみ、基底クラスの `NotOverridable` のようにこれを使用します。  
  
 **エラー ID:** BC32028  
  
### このエラーを解決するには  
  
1.  クラス メンバーにアクセスする場合は、`MyClass` の後にメンバー アクセス演算子 \(`.`\) と現在のインスタンスのメンバーを指定します。  
  
2.  クラス メンバーにアクセスしない場合は、`Me` キーワードを使用します。  
  
## 参照  
 [MyClass \- 削除](http://msdn.microsoft.com/ja-jp/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Me](http://msdn.microsoft.com/ja-jp/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)