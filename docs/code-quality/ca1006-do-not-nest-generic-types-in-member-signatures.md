---
title: 'CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 120acca8486d65962a5d8e3cd26a05ae8cc5ac78
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません
|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できるメンバーには、入れ子にされた型引数を含む署名があります。

## <a name="rule-description"></a>規則の説明
 入れ子にされた型引数は、ジェネリック型の型引数でもあります。 入れ子にされた型引数を含むシグネチャを持つメンバーを呼び出すには、ユーザーが 1 つのジェネリック型をインスタンス化し、別のジェネリック型のコンストラクターにこの型を渡す必要があります。 複雑な手順と構文が必要となるため、これは避けるようにしてください。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、入れ子にされた型引数を削除する設計を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 新しいライブラリの導入速度になり習得に必要な時間が短縮を簡単に理解し、使用する構文でジェネリック型を提供することです。

## <a name="example"></a>例
 次の例では、規則に違反するメソッドとを違反するメソッドを呼び出すために必要な構文を示します。

 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)