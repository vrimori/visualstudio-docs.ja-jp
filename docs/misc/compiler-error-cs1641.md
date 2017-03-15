---
title: "コンパイラ エラー CS1641 | Microsoft Docs"
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
  - "CS1641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1641"
ms.assetid: ba6eab47-c28b-4531-b6a0-6d538b236d19
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1641
固定サイズ バッファー フィールドには、フィールド名の後に配列サイズの指定子が必要です。  
  
 通常の配列とは異なり、固定サイズ バッファーは宣言の時点で定数のサイズを指定する必要があります。 このエラーを解決するのには、正の整数リテラルか定数の正の整数を追加し、識別子の後に角かっこを配置します。  
  
 次の例では CS1641 が生成されます。  
  
```  
// CS1641.cs // compile with: /unsafe /target:library unsafe struct S { fixed int [] a;  // CS1641 // OK fixed int b [10]; const int c = 10; fixed int d [c]; }  
```