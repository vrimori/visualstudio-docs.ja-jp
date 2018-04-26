---
title: 'CA1801: 使用されていないパラメーターをレビューします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 142ed6bca0513022b8edd1a062c443aa50d08191
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: 使用されていないパラメーターをレビューします
|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|なし - メンバーが変更に関係なく、アセンブリの外側に表示されていない場合。<br /><br /> なし - の本体にあるパラメーターを使用するメンバーを変更する場合。<br /><br /> 互換性に影響する - パラメーターを削除して、アセンブリ外部から参照である場合。|

## <a name="cause"></a>原因
 メソッドのシグネチャに、メソッドの本体で使用されていないパラメーターがあります。 このルールは、次の方法を確認していません。

-   デリゲートによって参照されるメソッド。

-   イベント ハンドラーとして使用されるメソッド。

-   宣言されたメソッド、 `abstract` (`MustOverride` Visual basic) 修飾子。

-   宣言されたメソッド、 `virtual` (`Overridable` Visual basic) 修飾子。

-   宣言されたメソッド、 `override` (`Overrides` Visual basic) 修飾子。

-   宣言されたメソッド、 `extern` (`Declare` Visual Basic でのステートメント) 修飾子。

## <a name="rule-description"></a>規則の説明
 アクセス エラー関連の正確性が存在しないかどうかを確認するメソッドの本体で使用されていない非仮想メソッドのパラメーターを確認します。 使用されていないパラメーターには、メンテナンスとパフォーマンスのコストが発生します。

 この規則違反場合があります、メソッドの実装に関するバグにポイントされます。 たとえば、パラメーターがメソッドの本体で使用されてが必要があります。 パラメーターに旧バージョンと互換性のために存在する場合は、この規則の警告を抑制します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、未使用のパラメーター (重大な変更) を削除またはメソッドの本体 (改行なしの変更) でパラメーターを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 修正プログラムは、重大な変更になりますが、以前にリリース済みコードのこの規則による警告を抑制しても安全です。

## <a name="example"></a>例
 次の例では、2 つの方法を示します。 規則に違反する 1 つのメソッドと、ルールに適合するその他のメソッドです。

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)