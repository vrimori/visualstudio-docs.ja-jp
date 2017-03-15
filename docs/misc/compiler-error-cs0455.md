---
title: "コンパイラ エラー CS0455 | Microsoft Docs"
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
  - "CS0455"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0455"
ms.assetid: a09840ac-ad8c-4c9c-868e-b83d937c7047
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0455
型パラメーター 'Type Parameter Name' は、競合する制約 'Constraint Name 1' と 'Constraint Name 2' を継承します  
  
 このエラーを発生させる 2 つの一般的な方法は、型パラメーターが 2 つの関連しないクラスから派生するように制約を設定することと、クラス型または参照型の制約および `struct` 型または値型の制約から派生するように制約を設定することです。 このエラーを解決するには、継承階層から競合を削除します。  
  
## 使用例  
 次のコードではエラー CS0455 が生成されます。  
  
```  
// CS0455.cs using System; public class GenericsErrors { public class B { } public class B2 { } public class G6<T> where T : B { public class N<U> where U : B2, T { } } // CS0455 }  
```