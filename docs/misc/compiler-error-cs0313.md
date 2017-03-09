---
title: "コンパイラ エラー CS0313 | Microsoft Docs"
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
  - "CS0313"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0313"
ms.assetid: a0b0f2fb-e742-4df8-98bd-3bc068f0c71c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0313
型 'type1' をジェネリック型またはメソッド 'type2' で型パラメーター 'parameter name' として使用できません。 Null 許容型 'type1' が 'type2' の制約を満たしていません。 Null 許容型では、インターフェイス制約を満たすことはできません。  
  
 Null 許容型は、Null 非許容の対応する型と同じではありません。 次の例では、`ImplStruct` は `BaseInterface` 制約を満たしていますが、`ImplStruct?` は `Nullable<ImplStruct>` によって `BaseInterface` が実装されていないため満たしていません。  
  
### このエラーを解決するには  
  
1.  次の例のコードを使用する場合、1 つの解決方法は、`TestMethod` の呼び出しの最初の型引数として通常の `ImplStruct` を指定することです。 次に、`TestMethod` を変更して、その return ステートメントで `Implstruct` の Null 許容バージョンを作成します。  
  
    ```  
    return new Nullable<T>(t);  
    ```  
  
## 使用例  
 次のコードでは CS0313 が生成されます。  
  
```  
// cs0313.cs public interface BaseInterface { } public struct ImplStruct : BaseInterface { } public class TestClass { public T? TestMethod<T, U>(T t) where T : struct, U { return t; } } public class NullableTest { public static void Run() { TestClass tc = new TestClass(); tc.TestMethod<ImplStruct?, BaseInterface>(new ImplStruct?()); // CS0313 } public static void Main() { } }  
```  
  
## 参照  
 [null 許容型](/dotnet/csharp/programming-guide/nullable-types/index)