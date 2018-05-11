---
title: 'CA1005: ジェネリック型でパラメーターを使用しすぎないでください'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05dd6e6c27ed440cf17862ea635210682bcd9cf5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: ジェネリック型でパラメーターを使用しすぎないでください
|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できるジェネリック型では、3 つ以上の型パラメーターを持ちます。

## <a name="rule-description"></a>規則の説明
 ジェネリック型に含まれる型パラメーターが増えれば増えるほど、それぞれの型パラメーターが表す意味を調べることや覚えることが難しくなります。 通常意味は明確に示すように、1 つの型パラメーターを持つです`List<T>`、および場合によってに示すように、2 つの型パラメーターを持つ`Dictionary<TKey, TValue>`します。 3 つ以上の型パラメーターが存在する場合は難易度がほとんどのユーザーに過剰になります (たとえば、 `TooManyTypeParameters<T, K, V>` (C#) または`TooManyTypeParameters(Of T, K, V)`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには 2 つの型パラメーターを使用してデザインを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 設計は、3 つ以上の型パラメーターを絶対に必要な場合を除き、この規則による警告は抑制しないでください。 新しいライブラリの導入速度になり習得に必要な時間が短縮を簡単に理解し、使用する構文でジェネリック型を提供することです。

## <a name="related-rules"></a>関連規則
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)