---
title: "コンパイラ エラー CS0449 | Microsoft Docs"
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
  - "CS0449"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0449"
ms.assetid: 32c07a2c-4c48-4d07-b643-72422a6b9fac
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0449
'class' または 'struct' 制約は、他の制約の前に指定されなければなりません。  
  
 ジェネリック型またはメソッドの型パラメーターの制約は、特定の順序で行う必要があります。`class` または `struct` を最初に指定し \(存在する場合\)、次にインターフェイスの制約、最後にコンストラクターの制約を指定する必要があります。 このエラーは、`class` または `struct` 制約が最初にないことが原因で発生します。 このエラーを解決するには、制約句の順序を変更します。  
  
## 使用例  
 次の例では CS0449 が生成されます。  
  
```  
// CS0449.cs // compile with: /target:library interface I {} public class C4 { public void F1<T>() where T : class, struct, I {}   // CS0449 public void F2<T>() where T : I, struct {}   // CS0449 public void F3<T>() where T : I, class {}   // CS0449 // OK public void F4<T>() where T : class {} public void F5<T>() where T : struct {} public void F6<T>() where T : I {} }  
```