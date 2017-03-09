---
title: "コンパイラの警告 (レベル 1) CS1957 | Microsoft Docs"
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
  - "CS1957"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1957"
ms.assetid: a4823211-52ce-4ffa-b19b-ee874069409f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1957
メンバー 'name' は、'method' をオーバーライドします。 実行時にオーバーライドされる可能性のある候補が複数あります。 どのメソッドが呼び出されるかは実装に依存します。  
  
 `ref` または `out` のいずれであるかによってのみ変化するメソッドのパラメーターを、実行時に区別することはできません。  
  
### この警告を回避するには  
  
1.  いずれかのメソッドに別の名前または異なる数のパラメーターを指定します。  
  
## 使用例  
 次のコードでは CS1957 が生成されます。  
  
```  
// cs1957.cs class Base<T, S> { public virtual string Test(out T x) // CS1957 { x = default(T); return "Base.Test"; } public virtual void Test(ref S x) { } } class Derived : Base<int, int> { public override string Test(out int x) { x = 0; return "Derived.Test"; } static int Main() { int x; if (new Derived().Test(out x) == "Derived.Test") return 0; return 1; } }  
```