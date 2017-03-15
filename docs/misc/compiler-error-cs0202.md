---
title: "コンパイラ エラー CS0202 | Microsoft Docs"
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
  - "CS0202"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0202"
ms.assetid: 7088850f-c206-4b95-9586-a0fa3d876c0c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0202
foreach では、'type.GetEnumerator\(\)' の戻り値の型 'type' に適切なパブリック MoveNext メソッドおよびパブリック Current プロパティが含まれている必要があります  
  
 foreach ステートメントを使用できるようにするために使用される <xref:System.Collections.IEnumerable.GetEnumerator%2A> 関数は、ポインターまたは配列を返すことはできません。列挙子として機能できるクラスのインスタンスを返す必要があります。 列挙子として機能するための適切な要件には、パブリック Current プロパティおよびパブリック MoveNext メソッドが含まれます。  
  
> [!NOTE]
>  C\# 2.0 では、コンパイラによって Current および MoveNext が自動的に生成されます。 詳細については、「[ジェネリック インターフェイス](/dotnet/csharp/programming-guide/generics/generic-interfaces)」のコード例を参照してください。  
  
 次の例では CS0202 が生成されます。  
  
```  
// CS0202.cs public class C1 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public static implicit operator C1 (int c1) { return 0; } } public class C2 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public C1[] GetEnumerator () // try the following line instead // public C1 GetEnumerator () { return null; } } public class MainClass { public static void Main () { C2 c2 = new C2(); foreach (C1 x in c2)   // CS0202 { System.Console.WriteLine(x.Current); } } }  
```