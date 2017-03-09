---
title: "コンパイラ エラー CS0831 | Microsoft Docs"
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
  - "CS0831"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0831"
ms.assetid: f626a77d-3844-4438-954b-b8201e72b1b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0831
式ツリーに、ベース アクセスを含めることはできません。  
  
 ベース アクセスは、通常は仮想関数呼び出しになる関数呼び出しを、基底クラス メソッド上の非仮想関数呼び出しにします。 これは、式ツリー自体では許可されませんが、基底クラス メソッドを呼び出すクラスのヘルパー メソッドを呼び出すことができます。  
  
### このエラーを解決するには  
  
1.  この方法で基底クラス メソッドにアクセスする必要がある場合は、基底クラスを呼び出すヘルパー メソッドを作成し、式ツリーがヘルパー メソッドを呼び出すようにします。 この手法を次のコードに示します。  
  
## 使用例  
 次の例では CS0831 が生成されます。  
  
```  
// cs0831.cs using System; using System.Linq; using System.Linq.Expressions; public class A { public virtual int BaseMethod() { return 1; } } public class C : A { public override int BaseMethod() { return 2; } public int Test(C c) { Expression<Func<int>> e = () => base.BaseMethod(); // CS0831 // Try the following line instead, // along with the BaseAccessHelper method. // Expression<Func<int>> e2 = () => BaseAccessHelper(); return 1; } // Uncomment to call from e2 expression above. // int BaseAccessHelper() // { //     return base.BaseMethod(); // } }   
```