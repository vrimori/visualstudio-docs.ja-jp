---
title: "コンパイラ エラー CS0314 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0314"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0314"
ms.assetid: 12f68f51-0568-4e80-b0fd-15899807477d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0314
型 'type1' をジェネリック型の型パラメーター 'name' またはメソッド 'name' として使用することはできません 'type1' から 'type2' へのボックス化変換や型パラメーター変換はありません。  
  
 ジェネリック型で使用している型パラメーターに制約がある場合は、新しいクラスもその同じ制約を満たす必要があります。  
  
### このエラーを解決するには  
  
1.  次の例では、`where T : ClassConstraint` をクラス `B` に追加しています。  
  
## 使用例  
 次のコードでは CS0314 が生成されます。  
  
```  
// cs0314.cs // Compile with: /target:library public class ClassConstraint { } public class A<T> where T : ClassConstraint { } public class B<T> : A<T> //CS0314 { } // Try using this instead. public class C<T> : A<T> where T : ClassConstraint { }  
```  
  
## 参照  
 [型パラメーターの制約](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)