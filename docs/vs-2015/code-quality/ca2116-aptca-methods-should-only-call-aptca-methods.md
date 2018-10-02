---
title: '2116: APTCA メソッドのみを呼び出す APTCA メソッド |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 78e3136ed2671de2962ae4de994bae178fcbceca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589697"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA メソッドは APTCA メソッドのみを呼び出すことができます
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2116: APTCA メソッドは APTCA メソッドのみを呼び出す必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca2116-aptca-methods-should-only-call-aptca-methods)します。

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 アセンブリのメソッド、<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>属性が属性がないアセンブリ内のメソッドを呼び出します。

## <a name="rule-description"></a>規則の説明
 既定では、厳密な名前付きアセンブリで public または protected のメソッドは暗黙的にによって保護、[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)は完全な信頼ののみ完全に信頼された呼び出し元は、厳密な名前のアセンブリにアクセスできます。 アセンブリの厳密な名前が付いて、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性には、この保護はありません。 属性には、アセンブリにイントラネットまたはインターネットからのコード実行などの完全な信頼がない呼び出し元にアクセスできるように、リンク確認要求が無効にします。

 APTCA 属性が完全に信頼されたアセンブリに存在すると、アセンブリが部分的に信頼された呼び出し元が許可されない別のアセンブリ内のコードの実行、セキュリティ上の弱点は可能性があります。 場合は 2 つのメソッド`M1`と`M2`次の条件を満たしている、悪意のある呼び出し元は、メソッドを使用できる`M1`を保護する暗黙の型の完全な信頼リンク確認要求をバイパスする`M2`:

-   `M1` パブリック メソッドは APTCA 属性を持つ完全に信頼されたアセンブリで宣言されます。

-   `M1` メソッドを呼び出す`M2`外`M1`のアセンブリ。

-   `M2`アセンブリは、APTCA 属性がないと、そのため、実行してはならない、または部分的に信頼されている呼び出し元の代わりです。

 部分的に信頼された呼び出し元`X`メソッドを呼び出すことができます`M1`原因となる、`M1`を呼び出す`M2`します。 `M2` APTCA 属性、その直前の呼び出し元がありません (`M1`) は完全な信頼のリンク確認要求を満たす必要があります`M1`完全な信頼があり、したがってこのチェックに適合します。 セキュリティ リスクは`X`を保護するリンク確認要求を満たすに関与しません`M2`呼び出し元が信頼されていないからです。 そのため、APTCA 属性を持つメソッド属性を持たないメソッドを呼び出していません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 APCTA 属性が必要な場合は、完全信頼アセンブリを呼び出すメソッドを保護する要求を使用します。 正確なアクセス許可要求するには、メソッドによって公開される機能は異なります。 可能な場合は、完全な信頼の基盤となる機能は部分的に信頼された呼び出し元に公開されないことを確認する要求を持つメソッドを保護します。 それができない場合は、公開されている機能を効果的に保護するアクセス許可のセットを選択します。 要求の詳細については、次を参照してください。[要求](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を安全に抑制するには、メソッドによって公開される機能が許可しないこと直接的または間接的に呼び出し元が機密情報、操作、または、破壊的な方法で使用できるリソースにアクセスすることを確認する必要があります。

## <a name="example"></a>例
 次の例では、2 つのアセンブリとテスト アプリケーションを使用して、この規則で検出されるセキュリティの脆弱性を示しています。 最初のアセンブリは APTCA 属性がないと部分的に信頼された呼び出し元にアクセスできないする必要があります (によって表される`M2`上記の説明で)。

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>例
 2 番目のアセンブリが完全に信頼されていると、部分的に信頼された呼び出し元を許可 (によって表される`M1`上記の説明で)。

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>例
 テスト アプリケーション (によって表される`X`上記の説明で) が部分的に信頼されています。

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **完全な信頼: 要求の要求が失敗しました。** 
 **ClassRequiringFullTrust.DoWork が呼び出されました。**
## <a name="related-rules"></a>関連規則
 [CA2117: APTCA 型は APTCA 基本型のみを拡張することができます](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>関連項目
 [安全なコーディングのガイドライン](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework アセンブリから呼び出すことで部分的に信頼されているコード](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d)[からライブラリを使用して部分的に信頼されているコード](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74)[要求](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[データとモデリング](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



