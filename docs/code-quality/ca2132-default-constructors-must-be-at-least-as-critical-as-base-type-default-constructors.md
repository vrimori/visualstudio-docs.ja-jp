---
title: CA2132:既定のコンストラクターは、基本型の既定コンストラクターと同程度以上、重要であることが必要
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cfe6e4f3ce896e5ae3d728a002bf2caf9f1948ef
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013536"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132:既定のコンストラクターは、基本型の既定コンストラクターと同程度以上、重要であることが必要

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

> [!NOTE]
> この警告は CoreCLR (Silverlight web アプリケーションに固有である CLR のバージョン) を実行しているコードにのみ適用されます。

## <a name="cause"></a>原因

派生クラスの既定のコンス トラクターの透過性属性は、基底クラスの透明度としてほど重要ではないです。

## <a name="rule-description"></a>規則の説明

型とメンバーを持つ、 <xref:System.Security.SecurityCriticalAttribute> Silverlight アプリケーション コードによって使用されることはできません。 セキュリティが重要な型やメンバーは、.NET Framework for Silverlight クラス ライブラリの信頼されているコードからのみ使用できます。 派生クラスにおけるパブリックな構築または保護された構築の透過性は、基底クラスと同程度以上である必要があるため、アプリケーション内のクラスを、SecurityCritical としてマークされたクラスから派生させることはできません。

CoreCLR プラットフォーム コードは、基本データ型に非透過的な既定の public または protected のコンス トラクターがある場合、派生型に従う必要がある既定のコンス トラクターの継承ルール。 派生型は既定のコンス トラクターにも必要し、そのコンス トラクターが基本型の重要な既定のコンス トラクターとして以上である必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法

違反を修正するには、型を削除するか、セキュリティの非透過的な型から派生していません。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

このルールからの警告を抑制しないでください。 型を読み込もうと拒否 CoreCLR アプリケーション コードでは、この規則の違反が発生する<xref:System.TypeLoadException>します。

### <a name="code"></a>コード

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]