---
title: "コンパイラ エラー CS0231 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0231"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0231"
ms.assetid: e5e6a8e1-6c9f-4a88-8935-7bedfba88f8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0231
params パラメーターは、仮パラメーター リストの最後のパラメーターでなければなりません。  
  
 [params](/dotnet/csharp/language-reference/keywords/params) パラメーターは引数の数を可変にすることができますが、他のすべてのパラメーターの後に指定する必要があります。 詳細については、「[メソッド](/dotnet/csharp/programming-guide/classes-and-structs/methods)」を参照してください。  
  
 次の例では CS0231 が生成されます。  
  
```  
// CS0231.cs class Test { public void TestMethod(params int[] p, int i) {} // CS0231 // To resolve the error, use the following line instead: // public void TestMethod(int i, params int[] p) {} static void Main() { } }  
```