---
title: "コンパイラ エラー CS1953 | Microsoft Docs"
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
  - "CS1953"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1953"
ms.assetid: b8af5eed-0f3b-4258-b4e2-f5d184288239
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1953
式ツリーのラムダには、メソッド グループを含めることはできません  
  
 メソッド呼び出しには `()` 演算子が必要です。 その演算子を持たないメソッド名が、そのメソッド名のオーバーロードされたメソッドすべてのセットからなるメソッド グループを参照しています。  
  
### このエラーを解決するには  
  
1.  メソッドを呼び出す場合は、`()` 演算子を追加します。  
  
## 使用例  
 次の例では CS1953 が生成されます。  
  
```  
// cs1953.cs using System; using System.Linq.Expressions; class CS1953 { public static void Main() { double num = 10; Expression<Func<bool>> testExpr = () => num.GetType is int; // CS1953 } }  
```