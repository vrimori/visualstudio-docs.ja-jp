---
title: "コンパイラ エラー CS0535 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0535"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0535"
ms.assetid: 282ed5d6-acb7-445b-999f-27a973ccc0b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0535
'class' はインターフェイス メンバー 'member' を実装しません  
  
 [クラス](/dotnet/csharp/language-reference/keywords/class)は[インターフェイス](/dotnet/csharp/language-reference/keywords/interface)から派生しましたが、クラスは 1 つ以上のインターフェイスのメンバーを実装しませんでした。 クラスは、派生元のインターフェイスのすべてのメンバーを実装する必要があります。そうでない場合は `abstract` として宣言される必要があります。  
  
## 使用例  
 次の例では CS0535 が生成されます。  
  
```  
// CS0535.cs public interface A { void F(); } public class B : A {}   // CS0535 A::F is not implemented // OK public class C : A { public void F() {} public static void Main() {} }  
```  
  
## 使用例  
 次の例では CS0535 が生成されます。  
  
```  
// CS0535_b.cs using System; class C : IDisposable {}   // CS0535 // OK class D : IDisposable { void IDisposable.Dispose() {} public void Dispose() {} static void Main() { using (D d = new D()) {} } }  
```