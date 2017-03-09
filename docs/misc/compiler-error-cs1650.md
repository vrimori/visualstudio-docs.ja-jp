---
title: "コンパイラ エラー CS1650 | Microsoft Docs"
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
  - "CS1650"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1650"
ms.assetid: 251a3a67-6e56-4795-874a-d54610c70595
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1650
静的読み取り専用フィールド 'identifier' のフィールドへの割り当てはできません \(静的コンストラクターまたは変数初期化子では可\)  
  
 このエラーは、変更を許可されていない場所で、読み取り専用および静的フィールドのメンバーを変更しようとする場合に発生します。 このエラーを解決するには、読み取り専用フィールドへの割り当てをコンストラクターまたは変数初期化子に制限するか、フィールドの宣言から `readonly` キーワードを削除します。  
  
```  
// CS1650.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void Main() { Outer.inner.i = 1;  // CS1650 } }  
```