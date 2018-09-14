---
title: 'CA2104: 読み取り専用の変更可能な参照型を宣言しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 80d40dd60b0a6b6e507b903fd7a6185c5419422e
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551692"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: 読み取り専用の変更可能な参照型を宣言しません

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 外部から参照できる型に、変更可能な参照型である、外部から参照可能な読み取り専用のフィールドがあります。

## <a name="rule-description"></a>規則の説明
 変更可能な型とは、インスタンス データを変更できる型です。 <xref:System.Text.StringBuilder?displayProperty=fullName>クラスは、変更可能な参照型の例を示します。 クラスのインスタンスの値を変更できるメンバーが含まれています。 変更不可の参照型の例は、<xref:System.String?displayProperty=fullName>クラス。 インスタンス化された後、その値は変化しません。

 読み取り専用修飾子 ([readonly](/dotnet/csharp/language-reference/keywords/readonly) c# で[ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]と[const](/cpp/cpp/const-cpp) C++ で) 参照型のフィールド (C++ でのポインター) により、フィールドを防止参照型の別のインスタンスで置き換えられます。 ただし、修飾子は、参照型を変更できないよう、フィールドのインスタンス データを妨げません。

 読み取り専用配列フィールドはこの規則から除外されますが、代わりに、違反が発生、 [ca 2105: 配列フィールドを読み取ることができませんのみ](../code-quality/ca2105-array-fields-should-not-be-read-only.md)ルール。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、読み取り専用修飾子を削除するか、重大な変更が許容される場合は、変更不可の型でフィールドを置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 フィールドの種類は変更可能なは場合、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、この規則違反の原因となるフィールド宣言を示します。

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]