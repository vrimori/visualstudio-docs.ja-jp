---
title: 'CA1007: 適切な場所にジェネリックを使用します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d3e03c1028dc310748aff7c8263ce75ace9985be
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551737"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: 適切な場所にジェネリックを使用します

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から見えるメソッドには、型の参照パラメーターが含まれています。 <xref:System.Object?displayProperty=fullName>、および含んでいるアセンブリのターゲット[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]します。

## <a name="rule-description"></a>規則の説明
 参照パラメーターはパラメーターを使用して変更を`ref`(`ByRef`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) キーワード。 参照パラメーターに指定する引数の型は参照パラメーターの型と正確に一致する必要があります。 参照パラメーターの型から派生した型を使用するには、種類あり必要がありますまずキャスト参照パラメーターの型の変数に代入されます。 ジェネリック メソッドの使用には、最初に参照パラメーターの型に型をキャストしていない場合、メソッドに渡される、制約の対象のすべての種類ができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、メソッドをジェネリックにして、置換、<xref:System.Object>型パラメーターを使用してパラメーター。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、非ジェネリックとジェネリック メソッドの両方として実装されている汎用スワップ ルーチンを示します。 比較する非ジェネリック メソッドとジェネリック メソッドを使用して、文字列をスワップする効率的な方法に注意してください。

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)