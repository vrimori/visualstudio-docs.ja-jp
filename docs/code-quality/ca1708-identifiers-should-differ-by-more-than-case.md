---
title: 'CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c952d4cf2533034c12a287149404bee6d267214
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915585"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません
|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 2 つの型、メンバー、パラメーター、または完全修飾名前空間の名前は、小文字に変換されるときと同じです。

## <a name="rule-description"></a>規則の説明
 名前空間、型、メンバー、およびパラメーターの各識別子は、大文字/小文字以外のみでは区別できません。共通言語ランタイムを対象とする言語は、大文字と小文字を区別する必要はないためです。 たとえば、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]広く使用されている大文字と小文字の言語です。

 この規則は、公開されているメンバーのみに適用されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 大文字小文字の他の識別子を比較した場合に一意の名前を選択します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 ライブラリを使用可能なすべての言語で使用できない可能性があります、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。

## <a name="example-of-a-violation"></a>違反の例
 次の例では、この規則違反を示します。

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)