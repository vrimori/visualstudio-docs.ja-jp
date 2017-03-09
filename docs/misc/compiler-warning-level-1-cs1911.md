---
title: "コンパイラの警告 (レベル 1) CS1911 | Microsoft Docs"
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
  - "CS1911"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1911"
ms.assetid: 95e8a7a0-1c19-4930-a7e9-3ae4060e97d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1911
匿名メソッド、ラムダ式、クエリ式、または反復子から、'base' キーワードを使用してメンバー ’name’ にアクセスすると、検証できないコードになります。 包含型のヘルパー メソッドへのアクセスの移行を検討してください。  
  
 反復子または匿名メソッドのメソッド本体内で、`base` キーワードを使用して仮想関数を呼び出すと、検証できないコードになります。 検証できないコードは、部分信頼環境で実行できなくなります。  
  
 CS1911 の 1 つの解決方法は、仮想関数呼び出しをヘルパー関数へ移動することです。  
  
## 使用例  
 次の例では CS1911 が生成されます。  
  
```  
// CS1911.cs // compile with: /W:1 using System; delegate void D(); delegate D RetD(); class B { protected virtual void M() { Console.WriteLine("B.M"); } } class Der : B { protected override void M() { Console.WriteLine("D.M"); } void Test() { base.M(); } D Test2() { return new D(base.M); } public D CallBaseM() { return delegate () { base.M(); };   // CS1911 // try the following line instead // return delegate () { Test(); }; } public RetD DelToBaseM() { return delegate () { return new D(base.M); };   // CS1911 // try the following line instead // return delegate () { return Test2(); }; } } class Program { public static void Main() { Der der = new Der(); D d = der.CallBaseM(); d(); RetD rd = der.DelToBaseM(); rd()(); } }  
```