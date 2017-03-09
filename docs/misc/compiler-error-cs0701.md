---
title: "コンパイラ エラー CS0701 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0701"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0701"
ms.assetid: eb844e31-00bd-468d-9f77-11d10a4ef120
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0701
'identifier' は有効な制約ではありません。 制約として使用された型はインターフェイス、非シール クラス、または型パラメーターでなければなりません。  
  
 このエラーは、sealed 型を制約として使用した場合に発生します。 このエラーを解決するには、sealed 型は制約に使わないようにします。  
  
## 使用例  
 次の例では CS0701 が生成されます。  
  
```  
// CS0701.cs // compile with: /target:library class C<T> where T : System.String {}   // CS0701 class D<T> where T : System.Attribute {}   // OK  
```