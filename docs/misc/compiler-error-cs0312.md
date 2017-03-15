---
title: "コンパイラ エラー CS0312 | Microsoft Docs"
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
  - "CS0312"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0312"
ms.assetid: 552db0ae-2ecf-4beb-9606-bbe58e5708f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0312
型 'type1' をジェネリック型の型パラメーター 'name' またはメソッド 'name' として使用することはできません。 null 許容型 'type1' が 'type2' の制約を満たしていません。  
  
 null 許容型は、対応する null 非許容型とは異なります。両者の間には暗黙の参照変換または ID 変換は存在しません。 null 許容型のボックス化変換は、ジェネリック型の制約を満たしません。 次の例では、1 番目の型パラメーターが `Nullable<int>`、2 番目の型パラメーターは `System.Int32` です。  
  
### このエラーを解決するには  
  
1.  制約を削除します。  
  
2.  次の例では、2 番目の型引数を `int?` または `object` にします。  
  
## 使用例  
 次のコードでは CS0312 が生成されます。  
  
```  
// cs0312.cs class Program { static void MTyVar<T, U>() where T : U { } static int Main() { MTyVar<int?, int>(); // CS0312 return 1; } }  
```  
  
 null 許容型と null 非許容型は異なりますが、null 許容型値と null 非許容型値との間では、さまざまな種類の変換を実行できます。  
  
## 参照  
 [null 許容型](/dotnet/csharp/programming-guide/nullable-types/index)