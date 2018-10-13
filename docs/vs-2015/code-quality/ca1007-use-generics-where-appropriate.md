---
title: 'Ca 1007: 適切な場所にジェネリックを使用します |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b6731ab14d977e9c389fb98a9bc0a4072c0ce4bf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199148"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: 適切な場所にジェネリックを使用します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から見えるメソッドには、型の参照パラメーターが含まれています。 <xref:System.Object?displayProperty=fullName>、および含んでいるアセンブリのターゲット[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]します。

## <a name="rule-description"></a>規則の説明
 参照パラメーターはパラメーターを使用して変更を`ref`(`ByRef`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) キーワード。 参照パラメーターに指定する引数の型は参照パラメーターの型と正確に一致する必要があります。 参照パラメーターの型から派生した型を使用するには、種類あり必要がありますまずキャスト参照パラメーターの型の変数に代入されます。 ジェネリック メソッドの使用には、最初に参照パラメーターの型に型をキャストしていない場合、メソッドに渡される、制約の対象のすべての種類ができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、メソッドをジェネリックにして、置換、<xref:System.Object>型パラメーターを使用してパラメーター。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、非ジェネリックとジェネリック メソッドの両方として実装されている汎用スワップ ルーチンを示します。 比較する非ジェネリック メソッドとジェネリック メソッドを使用して、文字列をスワップする効率的な方法に注意してください。

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



