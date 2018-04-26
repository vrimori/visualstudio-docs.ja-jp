---
title: 'CA1064: 例外は public として設定する必要があります'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b60127eee3ea333e324c656961eaf383a6ef409f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: 例外は public として設定する必要があります
|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリックでない例外がから直接派生<xref:System.Exception>、 <xref:System.SystemException>、または<xref:System.ApplicationException>です。

## <a name="rule-description"></a>規則の説明
 内部例外では、その内部スコープ内で表示されるだけです。 内部スコープの外側にある例外は、基本例外を使用しなければキャッチできません。 場合、内部例外から継承<xref:System.Exception>、 <xref:System.SystemException>、または<xref:System.ApplicationException>、外部のコードには、例外を行うには何かを認識するための十分な情報はありません。

 あるコードをさらにできるようになります基本例外で高度な処理を行うと考えることは、コードに、ベースとして内部の例外の後で使用されているパブリック例外がある場合。 パブリックの例外がで提供されるより多くの情報が<xref:System.Exception>、 <xref:System.SystemException>、または<xref:System.ApplicationException>です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 例外をパブリックまたはパブリック例外ではないから内部例外を派生させる<xref:System.Exception>、 <xref:System.SystemException>、または<xref:System.ApplicationException>です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 すべての場合、独自の内部スコープ内でプライベートの例外がキャッチされることを確認する場合は、この規則からのメッセージを抑制します。

## <a name="example"></a>例
 このルールは、例外クラスは内部があり、例外から直接派生したため、最初の例のメソッド、FirstCustomException に対して適用されます。 クラスは、例外から直接派生しても、ですが、クラスがパブリックとして宣言されているために、ルールは SecondCustomException クラスには発生しません。 3 番目のクラスもさせませんルールから直接派生しないため<xref:System.Exception?displayProperty=fullName>、 <xref:System.SystemException?displayProperty=fullName>、または<xref:System.ApplicationException?displayProperty=fullName>です。

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
