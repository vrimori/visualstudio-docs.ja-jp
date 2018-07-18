---
title: 'CA1802: 適切な場所にリテラルを使用します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: baa2252b4cdea8312f9d9b309b48604252852b71
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915842"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: 適切な場所にリテラルを使用します
|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 フィールドが宣言されている`static`と`readonly`(`Shared`と`ReadOnly`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])、コンパイル時に計算できる値に初期化されます。

## <a name="rule-description"></a>規則の説明
 値、`static``readonly`フィールドは、宣言する型の静的コンス トラクターが呼び出されたときに実行時に計算されます。 場合、`static``readonly`が宣言されているし、静的コンス トラクターが宣言されていません明示的に、コンパイラは、フィールドを初期化するために、静的コンス トラクター、フィールドを初期化します。

 値、`const`フィールドがコンパイル時に計算されと比較した場合、実行時のパフォーマンスを向上すると、メタデータに格納されている、`static``readonly`フィールドです。

 対象フィールドに割り当てられている値は、コンパイル時に計算であるため、宣言を変更、`const`フィールド ランタイムではなく、コンパイル時に値を計算できるようにします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、置換、`static`と`readonly`これらの修飾子を`const`修飾子です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パフォーマンスが問題になる場合、この規則による警告は抑制またはルールを無効にしても安全です。

## <a name="example"></a>例
 次の例は、型`UseReadOnly`、ルールを型に違反する`UseConstant`規則に適合します。

 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]