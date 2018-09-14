---
title: 'CA2116: APTCA メソッドは APTCA メソッドのみを呼び出すことができます'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7decf94644bdb055f38c267c945dc0dcc813550a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547920"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA メソッドは APTCA メソッドのみを呼び出すことができます

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

アセンブリのメソッド、<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>属性が属性がないアセンブリ内のメソッドを呼び出します。

## <a name="rule-description"></a>規則の説明

既定では、厳密な名前付きアセンブリで public または protected のメソッドは暗黙的にによって保護、[リンク確認要求](/dotnet/framework/misc/link-demands)は完全な信頼ののみ完全に信頼された呼び出し元は、厳密な名前のアセンブリにアクセスできます。 アセンブリの厳密な名前が付いて、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性には、この保護はありません。 属性には、アセンブリにイントラネットまたはインターネットからのコード実行などの完全な信頼がない呼び出し元にアクセスできるように、リンク確認要求が無効にします。

APTCA 属性が完全に信頼されたアセンブリに存在すると、アセンブリが部分的に信頼された呼び出し元が許可されない別のアセンブリ内のコードの実行、セキュリティ上の弱点は可能性があります。 場合は 2 つのメソッド`M1`と`M2`次の条件を満たしている、悪意のある呼び出し元は、メソッドを使用できる`M1`を保護する暗黙の型の完全な信頼リンク確認要求をバイパスする`M2`:

- `M1` パブリック メソッドは APTCA 属性を持つ完全に信頼されたアセンブリで宣言されます。

- `M1` メソッドを呼び出す`M2`外`M1`のアセンブリ。

- `M2`アセンブリは、APTCA 属性がないと、そのため、実行してはならない、または部分的に信頼されている呼び出し元の代わりです。

部分的に信頼された呼び出し元`X`メソッドを呼び出すことができます`M1`原因となる、`M1`を呼び出す`M2`します。 `M2` APTCA 属性、その直前の呼び出し元がありません (`M1`) は完全な信頼のリンク確認要求を満たす必要があります`M1`完全な信頼があり、したがってこのチェックに適合します。 セキュリティ リスクは`X`を保護するリンク確認要求を満たすに関与しません`M2`呼び出し元が信頼されていないからです。 そのため、APTCA 属性を持つメソッド属性を持たないメソッドを呼び出していません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 APCTA 属性が必要な場合は、完全信頼アセンブリを呼び出すメソッドを保護する要求を使用します。 正確なアクセス許可要求するには、メソッドによって公開される機能は異なります。 可能な場合は、完全な信頼の基盤となる機能は部分的に信頼された呼び出し元に公開されないことを確認する要求を持つメソッドを保護します。 それができない場合は、公開されている機能を効果的に保護するアクセス許可のセットを選択します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告を安全に抑制するには、メソッドによって公開される機能が許可しないこと直接的または間接的に呼び出し元が機密情報、操作、または、破壊的な方法で使用できるリソースにアクセスすることを確認する必要があります。

## <a name="example-1"></a>例 1
 次の例では、2 つのアセンブリとテスト アプリケーションを使用して、この規則で検出されるセキュリティの脆弱性を示しています。 最初のアセンブリは APTCA 属性がないと部分的に信頼された呼び出し元にアクセスできないする必要があります (によって表される`M2`上記の説明で)。

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>例 2
 2 番目のアセンブリが完全に信頼されていると、部分的に信頼された呼び出し元を許可 (によって表される`M1`上記の説明で)。

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>例 3
 テスト アプリケーション (によって表される`X`上記の説明で) が部分的に信頼されています。

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

この例を実行すると、次の出力が生成されます。

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>関連するルール

- [CA2117: APTCA 型は APTCA 基本型のみを拡張することができます](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)
- [部分信頼コードからのライブラリの使用](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [リンク確認要求](/dotnet/framework/misc/link-demands)
- [データとモデリング](/dotnet/framework/data/index)