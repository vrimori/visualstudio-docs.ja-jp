---
title: CA1002:ジェネリック リストを公開しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb3ecbeb2150554d989e00705709a26bb7a3479c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957963"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002:ジェネリック リストを公開しません

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型には、外部から参照できるメンバーが含まれています、<xref:System.Collections.Generic.List%601?displayProperty=fullName>型を返します、<xref:System.Collections.Generic.List%601?displayProperty=fullName>型、またはシグネチャが含まれています、<xref:System.Collections.Generic.List%601?displayProperty=fullName>パラメーター。

## <a name="rule-description"></a>規則の説明
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> パフォーマンスを継承しないように設計されたジェネリック コレクションであります。 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 継承されたクラスの動作を変更するが簡単にする仮想メンバーは含まれません。 次のジェネリック コレクションは、継承を目的しの代わりに公開する必要があります<xref:System.Collections.Generic.List%601?displayProperty=fullName>します。

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、変更、<xref:System.Collections.Generic.List%601?displayProperty=fullName>を継承するために設計されたジェネリック コレクションの 1 つの型。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この警告が発生したアセンブリを再利用可能なライブラリを使用する必要はありませんしない限り、この規則による警告を抑制しないでください。 たとえば、なりますパフォーマンス チューニングのアプリケーションでは、この警告を抑制しても安全をジェネリック リストを使用したパフォーマンス上の利点を得た場所。

## <a name="related-rules"></a>関連するルール
 [CA1005:ジェネリック型で過剰なパラメーターを回避します。](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA 1010:コレクションは、ジェネリック インターフェイスを実装する必要があります。](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA 1000:ジェネリック型で静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA 1006:ジェネリック型メンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA 1004:ジェネリック メソッドは、型パラメーターを指定する必要があります。](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA 1003:汎用イベント ハンドラーのインスタンスを使用して、](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA 1007:適切な場所にジェネリックを使用します。](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)