---
title: "コンパイラ エラー CS1648 | Microsoft Docs"
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
  - "CS1648"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1648"
ms.assetid: 5cf1bc84-cd18-4df2-942f-1cc17eabacd6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1648
読み取り専用フィールド 'identifier' のメンバーは変更できません \(コンストラクターまたは変数初期化子では可\)。  
  
 このエラーは、変更を許可されていない場所で、読み取り専用フィールドのメンバーを変更しようとする場合に発生します。 このエラーを解決するには、読み取り専用フィールドへの割り当てをコンストラクターまたは変数初期化子に制限するか、フィールドの宣言から読み取り専用のキーワードを削除します。  
  
 次の例では CS1648 が生成されます。  
  
```  
// CS1648.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void Main() { Outer outer = new Outer(); outer.inner.i = 1;  // CS1648 } }  
```