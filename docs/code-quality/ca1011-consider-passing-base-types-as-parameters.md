---
title: CA1011:基本型をパラメーターとして渡すことを考慮します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9388dc1b6649efd1f43e353e69833ad59ad5ff29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860687"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011:基本型をパラメーターとして渡すことを考慮します

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

メソッドの宣言には、派生型では、仮パラメーターが含まれていて、メソッドは、パラメーターの基本型のメンバーだけを呼び出します。

## <a name="rule-description"></a>規則の説明

メソッドの宣言で基本型をパラメーターとして指定すると、その基本型から派生した型は、メソッドに対応する引数として渡すことができます。 メソッド本体内で、引数を使用する場合に実行される特定のメソッドは、引数の型に依存します。 派生型によって提供される追加機能が必要ない場合、基本データ型の使用により、メソッドのより広範囲に利用します。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を解決するには、その基本型にパラメーターの型を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

このルールから警告を抑制しても安全です。

- メソッドが派生型によって提供される特定の機能が必要な場合

     \- または -

- 派生型のみ、またはより強い派生型では、適用するのには、メソッドに渡されます。

このような場合は、コードは、堅牢になります、コンパイラとランタイムによって提供される厳密な型チェックのためです。

## <a name="example"></a>例

次の例では、メソッド、`ManipulateFileStream`でのみ使用できる、<xref:System.IO.FileStream>オブジェクトで、この規則に違反します。 2 番目のメソッド`ManipulateAnyStream`、置き換えることで、ルールを満たす、<xref:System.IO.FileStream>パラメーターを使用して、<xref:System.IO.Stream>します。

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>関連するルール

[CA 1059:メンバーが特定の具象型に公開することはできません。](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)