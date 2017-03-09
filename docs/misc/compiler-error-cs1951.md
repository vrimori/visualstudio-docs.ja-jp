---
title: "コンパイラ エラー CS1951 | Microsoft Docs"
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
  - "CS1951"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1951"
ms.assetid: 799ba212-a000-44d9-b7da-a8c00eae63fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1951
式ツリーのラムダに out パラメーターや ref パラメーターを含めることはできません。  
  
 式ツリーは、式をデータ構造としてのみ表します。 参照でパラメーターを渡すときに必要な特定のメモリ位置を表す方法はありません。  
  
### このエラーを解決するには  
  
1.  デリゲート定義の `ref` 修飾子を削除して、値でパラメーターを渡すことが唯一の方法です。  
  
## 使用例  
 次の例では、CS1951 が生成されます。  
  
```  
// cs1951.cs using System.Linq; public delegate int TestDelegate(ref int i); class Test { static void Main() { System.Linq.Expressions.Expression<TestDelegate> tree1 = (ref int x) => x; // CS1951 } }  
```  
  
## 参照  
 [式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)