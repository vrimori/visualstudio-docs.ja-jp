---
title: "コンパイラ エラー CS1014 | Microsoft Docs"
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
  - "CS1014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1014"
ms.assetid: 60c1e9af-5a0d-4ae0-a2e6-881b0d1535e9
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1014
get または set アクセサーが必要です。  
  
 プロパティの宣言でメソッドの宣言が見つかりました。 プロパティでは `get` メソッドおよび `set` メソッドのみを宣言できます。  
  
 プロパティについて詳しくは、「[プロパティの使用](/dotnet/csharp/programming-guide/classes-and-structs/using-properties)」をご覧ください。  
  
## 使用例  
 次の例では CS1014 が生成されます。  
  
```  
// CS1014.cs // compile with: /target:library class Sample { public int TestProperty { get { return 0; } int z;   // CS1014  not get or set } }  
```