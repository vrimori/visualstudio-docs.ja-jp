---
title: "コンパイラ エラー CS0748 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0748"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0748"
ms.assetid: da1935af-a5ea-41f4-84ae-58559b750566
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0748
ラムダ パラメーターの使用方法に一貫性がありません。パラメーター型はすべて明示的であるか、またはすべて暗黙的である必要があります  
  
 ラムダ式に複数の入力パラメーターがある場合、暗黙の型指定を使用できないパラメーターもあれば、明示的な型指定を使用するパラメーターもあります。  
  
### このエラーを解決するには  
  
1.  すべての入力パラメーターに暗黙の型を指定するか、またはすべての入力パラメーターに明示的な型を指定します。  
  
## 使用例  
 ラムダ式で `alpha` のみに明示的な型が指定されているため、次のコードでは CS0748 が生成されます。  
  
```  
// cs0748.cs class CS0748 { delegate double D(int x, int y); D d = (int alpha, beta) => { return beta / alpha; }; // CS0748 }  
```  
  
## 参照  
 [ラムダ式](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)