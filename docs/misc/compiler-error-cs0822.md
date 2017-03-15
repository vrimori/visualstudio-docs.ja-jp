---
title: "コンパイラ エラー CS0822 | Microsoft Docs"
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
  - "CS0822"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0822"
ms.assetid: 519091be-2332-4df4-acd9-e3b633966b3d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0822
暗黙的に型指定されたローカル変数には const を指定できません  
  
 暗黙的に型指定されたローカル変数は、匿名型を格納する場合にのみ必要になります。 それ以外の場合は、便宜上あるだけのもので不要です。 変数の値を決して変更しない場合は、その変数に明示的に型を指定します。 暗黙的に型指定されたローカル変数に `readonly` 修飾子を使用すると、CS0106 が生成されます。  
  
### このエラーを解決するには  
  
1.  変数を定数または `readonly` にする必要がある場合は、その変数に明示的な型を指定します。  
  
## 使用例  
 次のコードでは CS0822 が生成されます。  
  
```  
// cs0822.cs class A { public static int Main() { const var x = 0; // CS0822.cs return -1; } }  
```  
  
## 参照  
 [暗黙的に型指定されるローカル変数](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)