---
title: 'CA1720: 識別子には型名を含めないでください'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8a981dc4c8ccd016836ea55b2ecd624e781c5a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: 識別子には型名を含めないでください
|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できるメンバーのパラメーターの名前には、データ型の名前が含まれています。

 - または -

 外部から参照できるメンバーの名前には、言語固有のデータ型の名前が含まれています。

## <a name="rule-description"></a>規則の説明
 パラメーターの名前とメンバーは、その型は、開発ツールによって提供されると予想されるを説明するよりもその意味を通信するためにより使用されます。 データ型の名前を使用する場合、メンバーの名前は、言語固有のものではなく言語非依存の名前を使用します。 たとえば、c# の型名 'int' ではなく Int32 言語に依存しないデータ型の名前を使用します。

 各トークン パラメーターまたはメンバーの名前は、大文字と小文字で、次の言語に固有のデータ型名に対してチェックされます。

-   Bool

-   WChar

-   Int8

-   UInt8

-   Short

-   UShort

-   Int

-   UInt

-   整数型

-   UInteger

-   Long

-   ULong

-   符号なし

-   符号付き

-   Float

-   Float32

-   Float64

 さらに、パラメーターの名前もチェックインに対して次の言語に依存しないデータ型名では、大文字と小文字。

-   Object

-   obj

-   ブール型

-   Char

-   String

-   SByte

-   Byte

-   UByte

-   Int16

-   UInt16

-   Int32

-   UInt32

-   Int64

-   UInt64

-   IntPtr

-   Ptr

-   ポインター

-   UInptr

-   UPtr

-   UPointer

-   Single

-   倍精度浮動小数点型

-   Decimal (10 進数型)

-   GUID

## <a name="how-to-fix-violations"></a>違反の修正方法
 **パラメーターに対して発生します。 場合**

 データ型の識別子、パラメーターの名前をより深くの意味を説明する用語または 'value' などの汎用的な用語のいずれかに置き換えます。

 **メンバーに対して発生します。 場合、**

 用語の意味、言語に無関係なまたは 'value' などの汎用的な用語をよく表すを言語固有のデータ型識別子、メンバーの名前に置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 時折を型に基づくパラメーター名およびメンバー名の使用は適切なにあります。 ただし、新規の開発、されていないシナリオでは、この規則による警告を抑制する必要がありますが発生します。 ライブラリが付属してで以前では、この規則による警告を抑制する必要があります。

## <a name="related-rules"></a>関連規則
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: 識別子はアンダースコアを含むことはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: パラメーター名はメンバー名と同一にすることはできません](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)