---
title: "コンパイラ エラー CS0819 | Microsoft Docs"
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
  - "CS0819"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0819"
ms.assetid: a5369e03-eb7d-4c88-b390-51304bd8d1ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0819
暗黙的に型指定されたローカルには複数の宣言子を指定できません。  
  
 複数の宣言子は、暗黙的に型指定された変数ではなく明示的な型宣言で使用できます。  
  
### このエラーを解決するには  
  
1.  値を宣言して、個別の行で暗黙的に型指定された各ローカル変数に値を代入します。  
  
## 使用例  
 次のコードでは CS0819 が生成されます。  
  
```  
// cs0819.cs class A { public static int Main() { var a = 3, b = 2; // CS0819 return -1; } }  
```  
  
## 参照  
 [暗黙的に型指定されるローカル変数](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)