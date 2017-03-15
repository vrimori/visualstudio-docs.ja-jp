---
title: "コンパイラ エラー CS0508 | Microsoft Docs"
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
  - "CS0508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0508"
ms.assetid: 28403573-6e64-4496-918d-fb50c8851e51
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0508
'Type 1': オーバーライドされたメンバー 'Member Name' に対応するために、戻り値の型は 'Type 2' でなければなりません  
  
 メソッド オーバーライドで、戻り値の型を変更しようとしています。 このエラーを解決するには、両方のメソッドが同じ戻り値の型を宣言することを確認します。  
  
## 使用例  
 次の例では CS0508 が生成されます。  
  
```  
// CS0508.cs // compile with: /target:library abstract public class Clx { public int i = 0; // Return type is int. abstract public int F(); } public class Cly : Clx { public override double F() { return 0.0;   // CS0508 } }  
```