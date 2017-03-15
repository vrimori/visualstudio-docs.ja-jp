---
title: "コンパイラ エラー CS0753 | Microsoft Docs"
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
  - "CS0753"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0753"
ms.assetid: 287dd9da-da74-4290-9fa1-21ef1a8150fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0753
メソッド、クラス、構造体、またはインターフェイスのみが partial を宣言できます。  
  
 [partial](/dotnet/csharp/language-reference/keywords/partial-type) 修飾子は、クラス、構造体、インターフェイス、およびメソッドでのみ使用できます。  
  
### このエラーを解決するには  
  
1.  変数または言語コンストラクトから `partial` 修飾子を削除します。  
  
## 使用例  
 次のコードでは CS0753 が生成されます。  
  
```  
// cs0753.cs using System; public partial class C { partial int num; // CS0753 public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)