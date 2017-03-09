---
title: "コンパイラ エラー CS0694 | Microsoft Docs"
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
  - "CS0694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0694"
ms.assetid: 048615e4-4599-4726-b5db-55322ccc936f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0694
型パラメーター 'identifier' には含んでいる型またはメソッドと同じ名前が付いています  
  
 型パラメーターの名前は、その型パラメーターを含む型またはメソッドの名前と同じにすることはできないため、型パラメーターに別の名前を使用する必要があります。  
  
## 使用例  
 次の例では CS0694 が生成されます。  
  
```  
// CS0694.cs // compile with: /target:library class C<C> {}   // CS0694  
```  
  
## 使用例  
 ジェネリック クラスを含む上記のケースに加えて、次のメソッドでも、このエラーが発生する可能性があります。  
  
```  
// CS0694_2.cs // compile with: /target:library class A { public void F<F>(F arg);   // CS0694 }  
```