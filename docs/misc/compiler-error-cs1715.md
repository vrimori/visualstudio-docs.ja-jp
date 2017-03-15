---
title: "コンパイラ エラー CS1715 | Microsoft Docs"
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
  - "CS1715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1715"
ms.assetid: 740044d1-a61c-4156-bc6a-adf26c7499ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1715
'Type1': オーバーライドされたメンバー 'MemberName' に対応するために、型は 'Type2' でなければなりません  
  
 このエラーは [コンパイラ エラー CS0508](../misc/compiler-error-cs0508.md) と同じですが、CS0508 が戻り値の型を持つメソッドにのみ適用されるようになったのに対し、CS1715 は '戻り値の型' ではなく '型' のみを持つプロパティとインデクサーに適用される点が異なります。  
  
## 使用例  
 次のコードでは CS1715 が生成されます。  
  
```  
// CS1715.cs abstract public class Base { abstract public int myProperty { get; set; } } public class Derived : Base { int myField; public override double myProperty  // CS1715 // try the following line instead // public override int myProperty { get { return myField; } set { myField;= value; } } public static void Main() { Derived d = new Derived(); d.myProperty = 5; } }  
```