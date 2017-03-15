---
title: "CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします | Microsoft Docs"
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
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック型は <xref:System.Object.Equals%2A?displayProperty=fullName> をオーバーライドしますが、<xref:System.Object.GetHashCode%2A?displayProperty=fullName> をオーバーライドしません。  
  
## 規則の説明  
 <xref:System.Object.GetHashCode%2A> は、現在のインスタンスに基づいて、ハッシュ アルゴリズムやデータ構造 \(ハッシュ テーブルなど\) に適した値を返します。  以下の型のインスタンスが適切に機能するには、同じ型で等値の 2 つのオブジェクトによって同じハッシュ コードが返される必要があります。  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName> を実装する型  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Object.GetHashCode%2A> を実装します。  同じ型のオブジェクト ペアの場合、<xref:System.Object.Equals%2A> の実装でそのペアに対して `true` を返すときに、同じ値を返す実装にする必要があります。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## クラスの例  
  
### 説明  
 この規則に違反するクラス \(参照型\) を次の例に示します。  
  
### コード  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### コメント  
 <xref:System.Object.GetHashCode> をオーバーライドすることによって違反を修正するコード例を次に示します。  
  
### コード  
 [!CODE [FxCop.Usage.GetHashCodeFixedClass#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass#1)]  
  
## 構造体の例  
  
### 説明  
 この規則に違反する構造体 \(値型\) の定義を次の例に示します。  
  
### コード  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
### コメント  
 <xref:System.Object.GetHashCode> をオーバーライドすることによって違反を修正するコード例を次に示します。  
  
### コード  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
## 関連規則  
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## 参照  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [等値演算子](../Topic/Equality%20Operators.md)