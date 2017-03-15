---
title: "コンパイラ エラー CS0764 | Microsoft Docs"
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
  - "CS0764"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0764"
ms.assetid: 76a64149-49d8-40ea-a976-03835d8fb7eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0764
部分メソッド宣言は、両方とも unsafe であるか、両方とも unsafe でないかのいずれかである必要があります  
  
 部分メソッドは、定義宣言 \(シグネチャ\) と省略可能な実装宣言 \(本体\) で構成されます。 定義宣言に `unsafe` 修飾子がある場合は、実装宣言にもこの修飾子が必要です。 この逆も同様で、実装宣言に `unsafe` 修飾子がある場合は、定義宣言にもこの修飾子が必要です。  
  
### このエラーを解決するには  
  
1.  定義宣言が正しい場合、定義宣言に一致するように実装宣言に対して `unsafe` 修飾子を追加または削除します。  
  
## 使用例  
  
```  
// cs0764.cs //  Compile with: /target:library /unsafe public partial class C { partial void Part(); unsafe partial void Part() //CS0764 { } public static int Main() { return 1; } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)