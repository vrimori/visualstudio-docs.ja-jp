---
title: "コンパイラ エラー CS0765 | Microsoft Docs"
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
  - "CS0765"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0765"
ms.assetid: adfb1f95-f7b1-4e43-83c2-42e8531eb980
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0765
定義宣言だけを含む部分メソッドまたは削除された条件付きメソッドは、式ツリーで使用できません  
  
 削除された部分メソッドの呼び出しは式ですが、式のツリーには使用できない式です。  
  
### このエラーを解決するには  
  
1.  部分メソッドの実装宣言を追加するか、条件付きメソッドをコンパイルから除去する原因のコードを削除します。  
  
## 使用例  
 次のコードでは 2 つの場所で CS0765 が生成されます。  
  
```  
// cs0765.cs using System; using System.Collections; using System.Collections.Generic; using System.Diagnostics; using System.Linq; using System.Linq.Expressions; public delegate void dele(); public class ConClass { [Conditional("CONDITION")] public static void TestMethod() { } } public partial class PartClass : IEnumerable { List<object> list = new List<object>(); partial void Add(int x); public IEnumerator GetEnumerator() { for (int i = 0; i < list.Count; i++) yield return list[i]; } static void Main() { Expression<Func<PartClass>> testExpr1 = () => new PartClass { 1, 2 }; // CS0765 Expression<dele> testExpr2 = () => ConClass.TestMethod(); // CS0765 } }  
```  
  
## 参照  
 [部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)