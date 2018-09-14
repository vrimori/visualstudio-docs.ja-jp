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
ms.openlocfilehash: 8d17c2981e4dabe82817aeedcf4fcab93e970b47
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548898"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: リンク確認要求で間接的にメソッドを公開しないでください

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリックまたはプロテクト メンバーが、[リンク確認要求](/dotnet/framework/misc/link-demands)と、セキュリティ チェックを実行しないメンバーによって呼び出されます。

## <a name="rule-description"></a>規則の説明
 リンク確認要求では、直接の呼び出し元のアクセス許可しかチェックされません。 場合、メンバー`X`セキュリティ要求呼び出しコード要求によって保護された、リンク、呼び出し元、必要な権限を使用せず、呼び出し元の責任も負わない`X`プロテクト メンバーにアクセスします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 セキュリティ[データとモデリング](/dotnet/framework/data/index)またはメンバーへのオンデマンドのリンクを不要になったリンク確認要求で保護されたメンバーをセキュリティ保護されていないアクセスを提供するようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告を安全に抑制するのには操作または破壊的な方法で使用できるリソースへのアクセスを呼び出し元に付与しないようにを確認する必要があります。

## <a name="example-1"></a>例 1
 次の例では、ライブラリの規則に違反して、ライブラリの脆弱性を示すアプリケーションを示します。 サンプル ライブラリは、まとめてルールに違反している 2 つのメソッドを提供します。 `EnvironmentSetting`メソッドは、環境変数への無制限アクセスのリンク確認要求によってセキュリティで保護されます。 `DomainInformation`メソッドには、呼び出し元のセキュリティ確認要求、なしを呼び出す前に`EnvironmentSetting`します。

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>例 2
 次のアプリケーションでは、セキュリティ保護されていないライブラリ メンバーを呼び出します。

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

この例を実行すると、次の出力が生成されます。

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)
- [リンク確認要求](/dotnet/framework/misc/link-demands)
- [データとモデリング](/dotnet/framework/data/index)