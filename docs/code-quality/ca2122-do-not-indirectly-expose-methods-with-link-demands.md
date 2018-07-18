---
title: 'CA2122: リンク確認要求で間接的にメソッドを公開しないでください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c43cfc1a448d9073a8bbe493d75c7c117f57d737
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915557"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: リンク確認要求で間接的にメソッドを公開しないでください
|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリックまたはプロテクト メンバーが指定されて、[リンク確認要求](/dotnet/framework/misc/link-demands)され、セキュリティ チェックを実行しないメンバーによって呼び出されます。

## <a name="rule-description"></a>規則の説明
 リンク確認要求では、直接の呼び出し元のアクセス許可しかチェックされません。 メンバーが`X`呼び出しコードは、保護、リンク確認要求によって、呼び出し元が、必要な権限を使用せず、呼び出し元のセキュリティ確認要求を行いません`X`プロテクト メンバーにアクセスします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 セキュリティ[データとモデリング](/dotnet/framework/data/index)またはリンク確認要求で保護されたメンバーを不要になった可能性のあるアクセスを提供するように要求をメンバーにリンクします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を安全に抑制するのには操作または破壊的な方法で使用できるリソースへのアクセスを呼び出し元に付与しないようにを確認する必要があります。

## <a name="example"></a>例
 次の例では、ルールに違反するライブラリとライブラリの脆弱性を示すアプリケーションを示します。 サンプル ライブラリは、同時に、ルールに違反している 2 つのメソッドを提供します。 `EnvironmentSetting`メソッドが環境変数への無制限アクセスのリンク確認要求によってセキュリティで保護します。 `DomainInformation`メソッドには、呼び出し元のセキュリティ確認要求、なしを呼び出す前に`EnvironmentSetting`です。

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example"></a>例
 次のアプリケーションでは、保護されていないライブラリ メンバーを呼び出します。

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

 この例を実行すると、次の出力が生成されます。

 **セキュリティ保護されていないメンバーから値: seattle.corp.contoso.com**
## <a name="see-also"></a>関連項目
 [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)[リンク確認要求](/dotnet/framework/misc/link-demands)[データとモデリング](/dotnet/framework/data/index)