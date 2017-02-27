---
title: "CA2226: 演算子は対称型オーバーロードを含まなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorsShouldHaveSymmetricalOverloads"
  - "CA2226"
helpviewer_keywords: 
  - "CA2226"
  - "OperatorsShouldHaveSymmetricalOverloads"
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2226: 演算子は対称型オーバーロードを含まなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 型で等値演算子または非等値演算子を実装し、逆の働きをする演算子を実装していません。  
  
## 規則の説明  
 等値演算子または非等値演算子が型のインスタンスに適用できて、逆の働きをする演算子が定義されない、という状況はありません。  一般に、非等値演算子は、等値演算子の否定値を返すことで実装します。  
  
 C\# コンパイラでは、この規則違反に対してエラーを発行します。  
  
## 違反の修正方法  
 この規則違反を修正するには、等値演算子と非等値演算子の両方を実装するか、一方しか実装されていない演算子を削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  型が、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] と整合性を取る方法では機能しなくなります。  
  
## 関連規則  
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)