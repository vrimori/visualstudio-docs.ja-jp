---
title: "コンパイラ エラー CS0462 | Microsoft Docs"
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
  - "CS0462"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0462"
ms.assetid: 0732b12d-0f7a-47d5-bc54-8b6147d7249f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0462
継承したメンバー 'member1' と 'member2' に 'type' 型の同じシグネチャがあるためオーバーライドできません。  
  
 このエラーは、ジェネリックの導入に伴い発生します。 通常、同じシグネチャを持つ 2 つのバージョンのメソッドをクラスで指定することはできません。 ただし、ジェネリックでは、特定の型でインスタンス化される場合は、別のメソッドを複製するジェネリック メソッドを指定できます。  
  
## 使用例  
 `C<int>` がインスタンス化されると、メソッド `F` の 2 つのバージョンが同じシグネチャを使用して作成されるため、クラス `D` でのオーバーライドでは、どちらにオーバーライドを適用するかを判断できません。  
  
 次の例では CS0462 が生成されます。  
  
```  
// CS0462.cs // compile with: /target:library class C<T> { public virtual void F(T t) {} public virtual void F(int t) {} } class D : C<int> { public override void F(int t) {}   // CS0462 }  
```