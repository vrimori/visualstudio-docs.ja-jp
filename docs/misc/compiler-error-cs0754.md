---
title: "コンパイラ エラー CS0754 | Microsoft Docs"
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
  - "CS0754"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0754"
ms.assetid: c83e04b5-6ab5-45c2-805e-0ba4f041d506
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0754
部分メソッドは、インターフェイス メソッドを明示的に実装できないことがあります。  
  
 部分メソッドは、インターフェイス内で定義されているメソッドの明示的な実装として宣言することはできません。  
  
### このエラーを解決するには  
  
1.  明示的なインターフェイス修飾をメソッド宣言から削除します。  
  
## 使用例  
 次のコードでは CS0754 が生成されます。  
  
```  
// cs0754.cs using System; public interface IF { void Part(); } public partial class C : IF { partial void IF.Part(); //CS0754 public static int Main() { return 1; } }  
```  
  
## 参照  
 [明示的なインターフェイスの実装](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)   
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)