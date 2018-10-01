---
title: 'CA1005: ジェネリック型でパラメーターを使用しすぎないでください'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 8b13441c279254525c4ffd892e60ae2b018e39ae
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547698"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: ジェネリック型でパラメーターを使用しすぎないでください
|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照のジェネリック型には、3 つ以上の型パラメーターがあります。

## <a name="rule-description"></a>規則の説明
 ジェネリック型に含まれる型パラメーターが増えれば増えるほど、それぞれの型パラメーターが表す意味を調べることや覚えることが難しくなります。 1 つの型パラメーターを使用して、通常は明確では`List<T>`、およびように、2 つの型パラメーターを持つ特定のケースで`Dictionary<TKey, TValue>`。 難しさがほとんどのユーザーに対して多すぎる 2 つ以上の型パラメーターが存在しない場合 (たとえば、 `TooManyTypeParameters<T, K, V>` (C#) または`TooManyTypeParameters(Of T, K, V)`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、以下の 2 つの型パラメーターを使用する設計を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 デザインは、2 つ以上の型パラメーターを絶対に必要な場合を除き、この規則による警告を抑制しないでください。 ジェネリックでは簡単に理解して使用する構文を提供するには、習得に必要なされ、新しいライブラリの導入速度を向上する時間が短縮されます。

## <a name="related-rules"></a>関連するルール
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)