---
title: "コンパイラ エラー CS0756 | Microsoft Docs"
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
  - "CS0756"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0756"
ms.assetid: 847b20b0-bbf0-43a2-8728-4b54cb3d9cd6
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0756
部分メソッドには、複数の定義宣言を指定することはできません。  
  
 部分メソッドの定義宣言は、メソッドのシグネチャを指定する部分であり、実装 \(メソッド本体\) を指定する部分ではありません。 部分メソッドには、一意のシグネチャごとに 1 つの定義宣言が必要です。 部分メソッドのオーバーロードされた各バージョンには、固有の定義宣言が必要です。  
  
### このエラーを解決するには  
  
1.  部分メソッドの定義制限を 1 つのみにして、他をすべて削除します。  
  
## 使用例  
  
```  
// cs0756.cs using System; public partial class C { partial void Part(); partial void Part(); // CS0756 public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)