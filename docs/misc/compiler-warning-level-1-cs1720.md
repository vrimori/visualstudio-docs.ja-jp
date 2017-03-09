---
title: "コンパイラの警告 (レベル 1) CS1720 | Microsoft Docs"
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
  - "CS1720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1720"
ms.assetid: 97adc294-3a4c-4418-a4ed-ccff43125b62
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1720
'generic type' の既定値が Null であるため、式は常に System.NullReferenceException になります  
  
 このエラーは、参照型 \(クラスなど\) であるジェネリック型変数の既定値を含む式を記述すると、発生します。 次のような式があるとします。  
  
```  
default(T).ToString()  
```  
  
 `T` は参照型であるため、その既定値は null となり、<xref:System.Object.ToString%2A> メソッドを適用しようとすると、<xref:System.NullReferenceException> がスローされます。  
  
## 使用例  
 型 `T` についてのクラス参照制約により、`T` は確実に参照型となります。  
  
 次の例では CS1720 が生成されます。  
  
```  
// CS1720.cs using System; public class Tester { public static void GenericClass<T>(T t1) where T : class { Console.WriteLine(default(T).ToString());  // CS1720 } public static void Main() {} }  
```