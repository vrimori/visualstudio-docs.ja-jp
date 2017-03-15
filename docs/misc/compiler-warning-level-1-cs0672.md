---
title: "コンパイラの警告 (レベル 1) CS0672 | Microsoft Docs"
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
  - "CS0672"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0672"
ms.assetid: 140a8708-97d0-444b-980b-62e74328cafb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS0672
メンバー 'member1' が古い形式のメンバー 'member2' をオーバーライドします。 Obsolete 属性を 'member1' に追加してください  
  
 コンパイラが `obsolete` としてマークされたメソッドへの `override` を検出しました。 ただし、オーバーライド元のメソッド自体は obsolete とマークされていませんでした。 オーバーライド元のメソッドを呼び出すと、引き続き [CS0612](/dotnet/csharp/misc/cs0612) が生成されます。  
  
 メソッド宣言を確認し、メソッド \(およびそのすべてのオーバーライド\) を `obsolete` とマークするかどうかを明示的に指定します。  
  
 次の例では CS0672 が生成されます。  
  
```  
// CS0672.cs // compile with: /W:1 class MyClass { [System.Obsolete] public virtual void ObsoleteMethod() { } } class MyClass2 : MyClass { public override void ObsoleteMethod()   // CS0672 { } } class MainClass { static public void Main() { } }  
```