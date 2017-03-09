---
title: "コンパイラ エラー CS0412 | Microsoft Docs"
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
  - "CS0412"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0412"
ms.assetid: eeb2afbc-9416-4bcf-b116-d6adc5cfd4ca
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0412
'generic': パラメーターまたはローカル変数に、メソッド型パラメーターと同じ名前を指定することはできません  
  
 ジェネリック メソッドの型パラメーターとメソッドのローカル変数 \(またはメソッドのいずれかのパラメーター\) で、名前の競合が生じています。 このエラーを回避するには、競合しているパラメータまたはローカル変数の名前を変更します。  
  
## 使用例  
 次の例では CS0412 が生成されます。  
  
```  
// CS0412.cs using System; class C { // Parameter name is the same as method type parameter name public void G<T>(int T)  // CS0412 { } public void F<T>() { // Method local variable name is the same as method type // parameter name double T = 0.0;  // CS0412 Console.WriteLine(T); } public static void Main() { } }  
```