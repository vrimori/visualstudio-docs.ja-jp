---
title: "CA2119: プライベート インターフェイスを満たすメソッドをシールします | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2119: プライベート インターフェイスを満たすメソッドをシールします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 継承可能なパブリック型により、`internal` \(Visual Basic では `Friend`\) インターフェイスのオーバーライド可能なメソッド実装が提供されます。  
  
## 規則の説明  
 インターフェイス メソッドにはパブリック アクセシビリティがあります。実装する型によるアクセシビリティの変更はできません。  内部インターフェイスでは、インターフェイスを定義するアセンブリの外部に実装することを目的としていないコントラクトが作成されます。  `virtual` \(Visual Basic では `Overridable`\) 修飾子を使用して内部インターフェイスのメソッドを実装するパブリック型により、メソッドをアセンブリの外部にある派生型でオーバーライドできます。  アセンブリの定義における 2 番目の型によりメソッドが呼び出され、内部限定のコントラクトが想定されている場合に、外部のアセンブリでオーバーライドされたメソッドが実行されると、処理が危険にさらされる可能性があります。  これにより、セキュリティの脆弱性が発生します。  
  
## 違反の修正方法  
 この規則違反を修正するには、次のいずれかの方法を使用してアセンブリ外部でメソッドがオーバーライドされないようにします。  
  
-   宣言している型を `sealed` \(Visual Basic では `NotInheritable`\) にします。  
  
-   宣言している型のアクセシビリティを `internal` \(Visual Basic では `Friend`\) に変更します。  
  
-   宣言している型からパブリック コンストラクターをすべて削除します。  
  
-   `virtual` 修飾子を使用せずに、メソッドを実装します。  
  
-   メソッドを明示的に実装します。  
  
## 警告を抑制する状況  
 メソッドがアセンブリの外部でオーバーライドされる場合、悪用される可能性があるセキュリティ問題が存在しないことを注意深く確認すれば、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反する型である `BaseImplementation` を次の例に示します。  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## 使用例  
 次に示す例では、前の例の仮想メソッドの実装を悪用しています。  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## 参照  
 [インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)