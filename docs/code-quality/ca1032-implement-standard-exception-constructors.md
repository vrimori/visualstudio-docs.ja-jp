---
title: CA1032:標準例外コンストラクターを実装します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 947b22929c58ce962861c65946941513d7845152
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957783"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032:標準例外コンストラクターを実装します

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

型拡張<xref:System.Exception?displayProperty=fullName>しますが、必要なすべてのコンス トラクターを宣言しません。

## <a name="rule-description"></a>規則の説明

例外の種類には、次の 3 つのコンス トラクターを実装する必要があります。

- パブリック NewException()

- パブリック NewException(string)

- パブリック NewException (文字列、例外)

さらに、レガシ FxCop 静的コード分析を実行している場合ではなく[Roslyn ベースの FxCop アナライザー](../code-quality/roslyn-analyzers-overview.md)、4 番目のコンス トラクターがない場合は、違反も生成されます。

- 保護されたまたはプライベート NewException (SerializationInfo, StreamingContext)

コンストラクターを完全に宣言していないと、例外を正しく処理するのが困難になります。 シグネチャを持つコンス トラクターなど`NewException(string, Exception)`他の例外によって引き起こされる例外を作成するために使用します。 せず、このコンス トラクターには、作成して、内部、例外はどのようなマネージ コードは、このような状況で行う必要があります (入れ子になった) を含む独自の例外のインスタンスをスローすることはできません。

最初の 3 つの例外のコンス トラクターでは、規則でパブリックです。 4 番目のコンス トラクターが封印されていないクラスで保護されているシール クラスではプライベートです。 詳細については、次を参照してください。 [ca 2229。シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、例外に不足しているコンス トラクターを追加し、適切なアクセシビリティであるかどうかを確認します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

パブリック コンス トラクターを異なるアクセス レベルを使用して、違反が発生する場合、この規則による警告を抑制するのには安全です。 さらの警告を抑制してもかまいませんが、`NewException(SerializationInfo, StreamingContext)`ポータブル クラス ライブラリ (PCL) を作成する場合は、コンス トラクター。

## <a name="example"></a>例

次の例には、この規則に違反する例外の種類と例外の種類が正しく実装されているが含まれています。

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>関連項目

[CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)