---
title: "コンパイラ エラー CS1948 | Microsoft Docs"
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
  - "CS1948"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1948"
ms.assetid: 3dac3abe-0edd-4ee1-8fb1-bc597ea63e1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1948
範囲変数 'name' に、メソッド型パラメーターと同じ名前を指定することはできません  
  
 同じ宣言領域に、同じ識別子の宣言を 2 つ含めることはできません。  
  
### このエラーを解決するには  
  
1.  範囲変数または型パラメーターの名前を変更します。  
  
## 使用例  
 次の例では、識別子 `T` がメソッド `TestMethod` の範囲変数と型パラメーターに使用されているため、CS1948 が生成されます。  
  
```  
// cs1948.cs using System.Linq; class Test { public void TestMethod<T>(T t) { var x = from T in Enumerable.Range(1, 100) // CS1948 select T; } }  
```