---
title: "コンパイラ エラー CS0555 | Microsoft Docs"
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
  - "CS0555"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0555"
ms.assetid: e4b2f890-98b4-4578-b1de-ebaafc8b3da2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0555
ユーザー定義の演算子は、それを囲む型のオブジェクトの取得、およびそれを囲む型のオブジェクトへの変換を行えません。  
  
 外側のクラスの値へのユーザー定義の変換は許可されません。このような演算子は不要です。  
  
 次の例では CS0555 が生成されます。  
  
```  
// CS0555.cs public class MyClass { // delete the following operator to resolve this CS0555 public static implicit operator MyClass(MyClass aa)   // CS0555 { return new MyClass(); } public static void Main() { } }  
```