---
title: "コンパイラ エラー CS0763 | Microsoft Docs"
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
  - "CS0763"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0763"
ms.assetid: 940870ba-1250-4365-acaa-7f968ee96c5b
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0763
部分メソッド宣言は、両方とも static であるか、両方とも static でないかのいずれかである必要があります。  
  
 部分メソッドの宣言は、静的な 1 つの部分と静的でない他方の部分にはできません。  
  
### このエラーを解決するには  
  
1.  必ず両方の部分を静的か非静的のどちらかにします。  
  
## 使用例  
 次のコードでは CS0763 が生成されます。  
  
```  
// cs0763.cs using System; public partial class C { static partial void Part(); partial void Part() // CS0763 { } public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [static](/dotnet/csharp/language-reference/keywords/static)