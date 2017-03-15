---
title: "コンパイラ エラー CS1642 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1642"
ms.assetid: 2efeedf1-1839-485d-8b8c-9045df1951f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1642
固定サイズ バッファー フィールドは、構造体のメンバーにしかなれません。  
  
 固定サイズ バッファー フィールドを `struct` ではなく `class` で使用すると、このエラーが発生します。 このエラーを解決するには、`class` を `struct` に変更するか、このフィールドを通常の配列として宣言します。  
  
## 使用例  
 次の例では CS1642 が生成されます。  
  
```  
// CS1642.cs // compile with: /unsafe /target:library unsafe class C { fixed int a[10];   // CS1642 } unsafe struct D { fixed int a[10]; } unsafe class E { public int[] a = null; }  
```