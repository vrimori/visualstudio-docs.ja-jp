---
title: "CA1036: 比較可能な型でメソッドをオーバーライドします | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036: 比較可能な型でメソッドをオーバーライドします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック型またはプロテクト型で <xref:System.IComparable?displayProperty=fullName> インターフェイスが実装されています。これによって <xref:System.Object.Equals%2A?displayProperty=fullName> はオーバーライドされません。また、"等しい"、"等しくない"、"未満"、"より大きい" を示す言語固有の演算子はオーバーロードされません。  型でインターフェイスの実装のみを継承している場合、この規則違反はレポートされません。  
  
## 規則の説明  
 カスタムの並べ替え順序を定義する型では、<xref:System.IComparable> インターフェイスを実装します。  <xref:System.IComparable.CompareTo%2A> メソッドは、その型の 2 つのインスタンスについて、適切な並べ替え順序を示す整数値を返します。  この規則では、並べ替え順序を設定する型を識別します。つまり、一般的な意味の "等しい"、"等しくない"、"未満"、"より大きい" は適用されません。  <xref:System.IComparable> の実装を提供する場合、一般に <xref:System.Object.Equals%2A> をオーバーライドする必要もあります。これは、<xref:System.IComparable.CompareTo%2A> との整合性がある値を返すためです。  <xref:System.Object.Equals%2A> をオーバーライドし、使用している言語で演算子のオーバーロードがサポートされている場合、<xref:System.Object.Equals%2A> との整合性がある演算子も指定します。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Object.Equals%2A> をオーバーライドします。  プログラミング言語で演算子のオーバーロードがサポートされている場合、次の演算子を指定します。  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 C\# では、記述に使用されるトークンはこれらの演算子は次のとおりです。: \=\=、\! \= \<。\>  
  
## 警告を抑制する状況  
 演算子がないために違反が発生し、プログラミング言語で演算子のオーバーロードをサポートしていない場合、この規則による警告を抑制しても安全です。これは、Visual Basic .NET の場合も同様です。  また、この規則が op\_Equality 以外の等値演算子に適用されているときに、その等値演算子を実装することがアプリケーション コンテキストにおいて意味がないと判断した場合も、この規則による警告を抑制しても安全です。  ただし、Object.Equals をオーバーライドする場合は、必ず op\_Equality と \=\= 演算子をオーバーロードする必要があります。  
  
## 使用例  
 <xref:System.IComparable> を正しく実装した型を次の例に示します。  コードのコメントで、<xref:System.Object.Equals%2A> と <xref:System.IComparable> インターフェイスに関連するさまざまな規則に適合するメソッドを識別しています。  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## 使用例  
 次のアプリケーションでは、前述した <xref:System.IComparable> 実装の動作をテストします。  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## 参照  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [等値演算子](../Topic/Equality%20Operators.md)