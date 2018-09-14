---
title: 'CA2126: 型のリンク要求には継承要求が必要です'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82fe9045173e65b24204a3b04e12b6a7f655c651
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548401"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: 型のリンク要求には継承要求が必要です

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックの封印されていない型が保護されているリンク確認要求、オーバーライド可能なメソッドを持つし、型でも、メソッドが継承確認要求で保護されています。

## <a name="rule-description"></a>規則の説明
 メソッドまたはその宣言型のリンク確認要求では、指定したアクセス許可が、メソッドの直接の呼び出し元が必要です。 メソッドの継承確認要求では、指定したアクセス許可がオーバーライドするメソッドが必要です。 型の継承確認要求では、指定した権限を持っているために派生クラスが必要です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、型またはリンク確認要求と同じアクセス許可の継承確認要求でメソッドをセキュリティで保護します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA2108: 値型での宣言セキュリティをレビューします](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: セキュリティで保護された型はフィールドを公開してはなりません](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: リンク確認要求で間接的にメソッドを公開しないでください](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: オーバーライドのリンク確認要求は基本と同様にします](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)
- [リンク確認要求](/dotnet/framework/misc/link-demands)