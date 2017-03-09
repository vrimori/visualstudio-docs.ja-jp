---
title: "コンパイラ エラー CS0835 | Microsoft Docs"
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
  - "CS0835"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0835"
ms.assetid: 593c26f6-6d82-49a6-8ace-4d29dd9f5fbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0835
ラムダ式を、型引数 'type' がデリゲート型ではない式ツリーに変換できません。  
  
 ラムダ式が式ツリーに変換される場合、式ツリーには、その引数のデリゲート型が必要です。 さらに、ラムダ式は、そのデリゲート型に変換できる必要があります。  
  
### このエラーを解決するには  
  
1.  型パラメーターを `int` からデリゲート型 \(たとえば、`Func<int,int>`\) に変更します。  
  
## 使用例  
 次の例では CS0835 が生成されます。  
  
```  
// cs0835.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<int> e = x => x + 1; // CS0835 // Try the following line instead. // Expression<Func<int,int>> e2 = x => x + 1; return 1; } }  
```