---
title: "コンパイラ エラー CS1670 | Microsoft Docs"
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
  - "CS1670"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1670"
ms.assetid: ee2507e5-b509-4af3-a15e-2c1f2da7159c
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1670
params はこのコンテキストでは有効ではありません。  
  
 C\# のいくつかの機能は、可変個引数リストと互換性がありません。次のような `params``` キーワードの使い方はできません。  
  
-   匿名メソッドのパラメーター リスト  
  
-   オーバーロードされた演算子  
  
## 使用例  
 次の例では CS1670 が生成されます。  
  
```  
// CS1670.cs public class C { public bool operator +(params int[] paramsList)  // CS1670 { return false; } static void Main() { } }  
```