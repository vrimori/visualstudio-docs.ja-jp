---
title: "CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック型で等値演算子が実装されていますが、<xref:System.Object.Equals%2A?displayProperty=fullName> はオーバーライドされません。  
  
## 規則の説明  
 等値演算子は、構文上、<xref:System.Object.Equals%2A> メソッドの機能を簡単に使用できるように用意されています。  等値演算子を実装するときの論理は、<xref:System.Object.Equals%2A> の場合と同様にする必要があります。  
  
 この規則に違反すると、C\# コンパイラから警告が発行されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、等値演算子の実装を取り除くか、<xref:System.Object.Equals%2A> をオーバーライドし、2 つのメソッドで同じ値を返すようにします。  等値演算子によって動作が矛盾しない場合、違反を修正するには、基本クラスで <xref:System.Object.Equals%2A> メソッドを呼び出す <xref:System.Object.Equals%2A> を実装します。  
  
## 警告を抑制する状況  
 等値演算子が、<xref:System.Object.Equals%2A> の継承を受けた実装と同じ値を返す場合、この規則による警告を抑制しても安全です。  例では、この規則による警告を安全に抑制できる型が使用されています。  
  
## 等値の定義が矛盾している例  
  
### 説明  
 次の例は、等値の定義が矛盾している型を示します。  `BadPoint` では、等値演算子の実装をカスタマイズしているため、等値の意味が変わります。ただし、<xref:System.Object.Equals%2A> をオーバーライドしないため、動作は同じです。  
  
### コード  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## 使用例  
 次のコードでは、`BadPoint` の動作をテストします。  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **a \=  \(\[0\] 1,1\) and b \= \(\[1\] 2,2\) are equal?  No**  
**a \=\= b ?  No**  
**a1 and a are equal?  Yes**  
**a1 \=\= a ?  Yes**  
**b and bcopy are equal ?  No**  
**b \=\= bcopy ?  Yes**    
## 使用例  
 理論的にはこの規則に違反しているのですが、動作が矛盾しない型を次の例に示します。  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## 使用例  
 次のコードでは、`GoodPoint` の動作をテストします。  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **a \=  \(1,1\) and b \= \(2,2\) are equal?  No**  
**a \=\= b ?  No**  
**a1 and a are equal?  Yes**  
**a1 \=\= a ?  Yes**  
**b and bcopy are equal ?  Yes**  
**b \=\= bcopy ?  Yes**    
## クラスの例  
  
### 説明  
 この規則に違反するクラス \(参照型\) を次の例に示します。  
  
### コード  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## 使用例  
 <xref:System.Object.Equals%2A?displayProperty=fullName> をオーバーライドすることによって違反を修正するコード例を次に示します。  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## 構造体の例  
  
### 説明  
 この規則に違反する構造体 \(値型\) の定義を次の例に示します。  
  
### コード  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## 使用例  
 <xref:System.ValueType.Equals%2A?displayProperty=fullName> をオーバーライドすることによって違反を修正するコード例を次に示します。  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## 関連規則  
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)