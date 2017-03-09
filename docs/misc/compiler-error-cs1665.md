---
title: "コンパイラ エラー CS1665 | Microsoft Docs"
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
  - "CS1665"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1665"
ms.assetid: 93d4a4af-23c3-4730-a778-77852e41db4d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1665
固定サイズ バッファーには、0 よりも大きい値を指定しなければなりません。  
  
 このエラーは、固定サイズのバッファーが 0 または負のサイズで宣言されている場合に発生します。 固定サイズ バッファーの長さは、正の整数である必要があります。  
  
## 使用例  
 次の例では CS1665 が生成されます。  
  
```  
// CS1665.cs // compile with: /unsafe /target:library struct S { public unsafe fixed int A[0];   // CS1665 }  
```