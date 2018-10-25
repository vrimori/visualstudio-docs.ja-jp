---
title: '2224: オーバー ロードする演算子 equals で equals をオーバーライド |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 66f4b4bcc7c2c1d359f5d8fa91227fb51a27adc4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815235"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: オーバーロードする演算子 equals で Equals をオーバーライドします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリック型は、等値演算子を実装しますが、オーバーライドしない<xref:System.Object.Equals%2A?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 構文上便利な方法の機能にアクセスするものでは、等値演算子、<xref:System.Object.Equals%2A>メソッド。 そのロジックがの場合と同じである必要があります、等値演算子を実装する場合<xref:System.Object.Equals%2A>します。

 C# コンパイラは、コードにこの規則に違反している場合に警告を発行します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、する必要があります、等値演算子の実装を削除または上書き<xref:System.Object.Equals%2A>し、2 つのメソッドが同じ値を返します。 実装を提供することで、違反を修正するには、等値演算子は、一貫性のない動作を導入していない場合、<xref:System.Object.Equals%2A>を呼び出す、<xref:System.Object.Equals%2A>基底クラス メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 等値演算子は、継承された実装のと同じ値を返す場合、この規則による警告を抑制するのには安全では<xref:System.Object.Equals%2A>します。 例のセクションには、この規則による警告を安全に抑制する型が含まれています。

## <a name="examples-of-inconsistent-equality-definitions"></a>一貫性のない等価性の定義の例

### <a name="description"></a>説明
 次の例では、等値の一貫性のない定義を持つ型を示します。 `BadPoint` 等値の意味を等値演算子のカスタム実装を提供することで変更しますが、オーバーライドしない<xref:System.Object.Equals%2A>と同様に動作できるようにします。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>例
 次のコードの動作をテストする`BadPoint`します。

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **= ([0] 1, 1) と b = ([1] 2, 2) が等しいか?いいえ**
**b = = でしょうか。いいえ**
**a1 と等しいか?[はい]**
**a1 = =、?[はい]**
**b と bcopy が等しいか?いいえ**
**b bcopy = = でしょうか。うん**
## <a name="example"></a>例
 次の例では、技術的には、この規則に違反していますが、一貫性のある方法で動作しない型を示します。

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>例
 次のコードの動作をテストする`GoodPoint`します。

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **= (1, 1) と b = (2, 2) が等しいか?いいえ**
**b = = でしょうか。いいえ**
**a1 と等しいか?[はい]**
**a1 = =、?[はい]**
**b と bcopy が等しいか?[はい]**
**b bcopy = = でしょうか。うん**
## <a name="class-example"></a>クラスの例

### <a name="description"></a>説明
 次の例では、この規則に違反するためのクラス (参照型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>例
 次の例では、オーバーライドすることで、違反を修正する<xref:System.Object.Equals%2A?displayProperty=fullName>します。

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>構造の例

### <a name="description"></a>説明
 次の例では、この規則に違反する構造体 (値型) を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>例
 次の例では、オーバーライドすることで、違反を修正する<xref:System.ValueType.Equals%2A?displayProperty=fullName>します。

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1046: 参照型で、演算子 equals をオーバーロードしないでください](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: 演算子オーバーロードには名前付けされた代替が存在します](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: 演算子は対称型オーバーロードを含まなければなりません](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: オーバーライドする Equals で GetHashCode をオーバーライドします](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)



