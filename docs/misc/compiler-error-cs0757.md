---
title: "コンパイラ エラー CS0757 | Microsoft Docs"
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
  - "CS0757"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0757"
ms.assetid: ba093570-306d-4b7b-aad5-1a3855ad6776
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0757
部分メソッドに複数の実装宣言を含めることはできません。  
  
 部分メソッドは、1 個だけの定義宣言 \(シグネチャ\) と、1 個か 0 個の実装宣言 \(本体\) で構成されます。 同一の定義宣言に対して複数の実装宣言を設定することはできません。 部分メソッドはオーバーロードすることができ、オーバーロードされたそれぞれのバージョンに 1 個か 0 個の実装宣言を設定できます。  
  
### このエラーを解決するには  
  
1.  部分メソッドの実装宣言を、1 つだけ残してその他はすべて削除します。  
  
## 使用例  
 次の例では CS0757 が生成されます。  
  
```  
// cs0757.cs using System; public partial class C { // Defining declaration. partial void Part(); // Implementing declaration. partial void Part() { //...Do something. } // Second implementing declaration. partial void Part() // CS0757 { //...Do something. } public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)