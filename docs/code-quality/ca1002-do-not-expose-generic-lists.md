---
title: 'CA1002: ジェネリック リストを公開しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2131ef8cb0b8f0ba540d7403d7c5f8dbb8b89df
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: ジェネリック リストを公開しません
|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型にはである外部から参照できるメンバーが含まれています、<xref:System.Collections.Generic.List%601?displayProperty=fullName>型を返します、<xref:System.Collections.Generic.List%601?displayProperty=fullName>型、またはシグネチャが含まれています、<xref:System.Collections.Generic.List%601?displayProperty=fullName>パラメーター。

## <a name="rule-description"></a>規則の説明
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> パフォーマンスと継承ではない用に設計されたジェネリック コレクションです。 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 継承されたクラスの動作を変更するが簡単にする仮想メンバーは含まれません。 次のジェネリック コレクションは、継承を目的しの代わりに公開する必要があります<xref:System.Collections.Generic.List%601?displayProperty=fullName>です。

-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、変更、<xref:System.Collections.Generic.List%601?displayProperty=fullName>する継承を対象とするジェネリック コレクションの 1 つの種類。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この警告が発生したアセンブリものではありませんをライブラリに再利用可能な限り、この規則による警告は抑制しないでください。 たとえば、なりますパフォーマンス チューニング アプリケーションでは、この警告を抑制しても安全をジェネリック リストを使用した、パフォーマンスが向上を得た場所。

## <a name="related-rules"></a>関連規則
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)