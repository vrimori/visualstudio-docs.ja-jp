---
title: "コンパイラ エラー CS1657 | Microsoft Docs"
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
  - "CS1657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1657"
ms.assetid: 6f0aeebe-5c90-4d5b-981c-1795d2e8fbb9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1657
'reason' であるため、'parameter' を ref または out 引数として渡せません  
  
 このエラーは、変数が読み取り専用であるコンテキストでその変数が [ref](/dotnet/csharp/language-reference/keywords/ref) または [out](/dotnet/csharp/language-reference/keywords/out) 引数として渡される場合に発生します。 読み取り専用コンテキストには、[foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 繰り返し変数、[using](/dotnet/csharp/language-reference/keywords/using-statement) 変数、`fixed` 変数などがあります。 このエラーを解決するには、`using` ブロック、`foreach` ステートメント、および `fixed` ステートメントで `ref` または `out` パラメーターとして `foreach`、`using`、または `fixed` 変数を受け取る関数を呼び出さないでください。  
  
## 使用例  
 次の例では CS1657 が生成されます。  
  
```  
// CS1657.cs using System; class C : IDisposable { public int i; public void Dispose() {} } class CMain { static void f(ref C c) { } static void Main() { using (C c = new C()) { f(ref c);  // CS1657 } } }  
```  
  
## 使用例  
 次のコードは、`fixed` ステートメントで発生する同じ問題を示しています。  
  
```  
// CS1657b.cs // compile with: /unsafe unsafe class C { static void F(ref int* p) { } static void Main() { int[] a = new int[5]; fixed(int* p = a) F(ref p); // CS1657 } }  
```