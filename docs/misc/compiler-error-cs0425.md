---
title: "コンパイラ エラー CS0425 | Microsoft Docs"
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
  - "CS0425"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0425"
ms.assetid: cec0391c-a641-43bc-8557-92b23f6ca685
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0425
メソッド 'method' の型パラメーター 'type parameter' に対する制約は、インターフェイス メソッド 'method' の型パラメーター 'type parameter' に対する制約と一致しなければなりません。 明示的なインターフェイスの実装を使用することをお勧めします。  
  
 このエラーは、仮想ジェネリック メソッドが派生クラスでオーバーライドされ、派生クラスのメソッドの制約が基底クラスのメソッドの制約と一致しない場合に発生します。 このエラーを回避するには、`where` 句が両方の宣言で同じであることを確認するか、またはインターフェイスを明示的に実装します。  
  
## 使用例  
 次の例では、CS0425 が生成されます。  
  
```  
// CS0425.cs class C1 { } class C2 { } interface IBase { void F<ItemType>(ItemType item) where ItemType : C1; } class Derived : IBase { public void F<ItemType>(ItemType item) where ItemType : C2  // CS0425 { } } class CMain { public static void Main() { } }  
```  
  
## 使用例  
 一連の制約の意味が同じであれば、制約が文字どおり一致している必要はありません。 たとえば、次は問題ありません。  
  
```  
// CS0425b.cs interface J<Z> { } interface I<S> { void F<T>(S s, T t) where T: J<S>, J<int>; } class C : I<int> { public void F<X>(int s, X x) where X : J<int> { } public static void Main() { } }  
```