---
title: "コンパイラ エラー CS0447 | Microsoft Docs"
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
  - "CS0447"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0447"
ms.assetid: a25486c5-e9bf-4528-8533-c1aaab22ace0
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0447
型引数には属性を使用できません。型パラメーターでのみ使用できます  
  
 このエラーは、呼び出しステートメント内の型引数に属性を適用するときに発生します。 次のように、クラスまたはメソッド宣言ステートメントで型パラメーターに属性を適用できます。  
  
```  
class C<[some attribute] T> {…}  
```  
  
 次のコード行ではこのエラーが生成されます。 前のコード行に定義されているクラス `C` に、`MyStaticMethod` という静的メソッドがあることを前提にしています。  
  
```  
C<[some attribute] T>.MyStaticMethod();  
```  
  
## 使用例  
 次のコードではエラー CS0447 が生成されます。  
  
```  
// CS0447.cs using System; namespace Test41 { public interface I<A> { void Meth<B>(); } public class B : I<int> { void I<[Test] int>.Meth<X>() { }  // CS0447 } }  
```