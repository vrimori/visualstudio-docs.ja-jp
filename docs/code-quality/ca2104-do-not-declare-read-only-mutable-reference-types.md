---
title: CA2104:読み取り専用の変更可能な参照型を宣言しません
ms.date: 11/01/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8c1e2ceed83564c5ccdd6de87eefe3537b410612
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037669"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104:読み取り専用の変更可能な参照型を宣言しません

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|なし|

> [!NOTE]
> Ca 2104 のルールは廃止され、Visual Studio の将来のバージョンで削除される予定です。

## <a name="cause"></a>原因

外部から参照できる型に、変更可能な参照型である、外部から参照可能な読み取り専用のフィールドがあります。

## <a name="rule-description"></a>規則の説明

変更可能な型とは、インスタンス データを変更できる型です。 <xref:System.Text.StringBuilder?displayProperty=fullName>クラスは、変更可能な参照型の例を示します。 クラスのインスタンスの値を変更できるメンバーが含まれています。 変更不可の参照型の例は、<xref:System.String?displayProperty=fullName>クラス。 インスタンス化された後、その値は変化しません。

読み取り専用修飾子 ([readonly](/dotnet/csharp/language-reference/keywords/readonly)でC#、 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) Visual basic でと[const](/cpp/cpp/const-cpp) C++ で) 参照型のフィールド (または C++ でのポインター) により、フィールドから参照型の別のインスタンスを置き換えられます。 ただし、修飾子は、参照型を変更できないよう、フィールドのインスタンス データを妨げません。

このルールが誤って表示の種類の違反は、実際には、変更できません。 その場合は、警告を抑制しても安全です。

読み取り専用配列フィールドはこの規則から除外されますが、代わりに、違反が発生、 [ca 2105。配列フィールドを読み取ることができませんのみ](../code-quality/ca2105-array-fields-should-not-be-read-only.md)ルール。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、読み取り専用修飾子を削除するか、重大な変更が許容される場合は、変更不可の型でフィールドを置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

フィールドの種類は変更可能なは場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例

次の例では、この規則違反の原因となるフィールド宣言を示します。

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]