---
title: "コンパイラ エラー CS0759 | Microsoft Docs"
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
  - "CS0759"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0759"
ms.assetid: 96f0e178-adbf-4327-8934-ac282c428184
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0759
部分メソッド 'method' の実装宣言に対する定義宣言が見つかりませんでした。  
  
 部分メソッドには、メソッドのシグネチャ \(名前、戻り値の型、およびパラメーター\) を定義する定義宣言が必要です。 実装またはメソッド本体は省略可能です。  
  
### このエラーを解決するには  
  
1.  部分クラスまたは構造体の別の部分にある部分メソッドに、定義宣言を指定します。  
  
## 使用例  
 次の例では、CS0759 が生成されます。  
  
```  
// cs0759.cs using System; public partial class C { partial void Part() // CS0759 { } public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)