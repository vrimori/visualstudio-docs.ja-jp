---
title: CA1012:抽象型にはコンストラクターを含めません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dd35cd7b084deb34b23b49ebc04517733c5478c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006783"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012:抽象型にはコンストラクターを含めません

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック型は abstract であり、パブリック コンス トラクターがあります。

## <a name="rule-description"></a>規則の説明
 抽象型上のコンストラクターは、派生型からのみ呼び出すことができます。 パブリック コンストラクターで型のインスタンスが作成され、抽象型のインスタンスは自分で作成できないため、パブリック コンストラクターが含まれる抽象型のデザインは不適切になります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、コンス トラクターを保護するか、または抽象型を宣言しないでください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。 抽象型では、パブリック コンス トラクターがあります。

## <a name="example"></a>例
 次の例には、この規則に違反する抽象型が含まれています。

 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

## <a name="example"></a>例
 次の例では、前の違反を修正からコンス トラクターのアクセシビリティを変更することで`public`に`protected`します。

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]