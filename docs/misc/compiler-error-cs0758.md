---
title: "コンパイラ エラー CS0758 | Microsoft Docs"
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
  - "CS0758"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0758"
ms.assetid: 06ddd548-1311-40db-9078-8a18107b8346
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0758
部分メソッド宣言は、両方とも params パラメーターを使用するか、両方とも params パラメーターを使用しないかのいずれかである必要があります。  
  
 部分メソッドの一部が `params` パラメーターを指定する場合、その他の部分もこのパラメーターを指定する必要があります。  
  
### このエラーを解決するには  
  
1.  `params` 修飾子をメソッドの一部に追加するか、他の部分からこの修飾子を削除します。  
  
## 使用例  
 次のコードでは CS0758 が生成されます。  
  
```  
using System; public partial class C { partial void Part(int i, params char[] array); partial void Part(int i, char[] array) // CS0758 { } public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)