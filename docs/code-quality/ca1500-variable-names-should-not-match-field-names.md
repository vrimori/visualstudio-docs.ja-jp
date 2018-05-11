---
title: 'CA1500: 変数名はフィールド名と同一にすることはできません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f291b603c94292cc86536a212a4ab8286600740b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: 変数名はフィールド名と同一にすることはできません
|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|フィールドと同じ名前を持つパラメーターで発生しました。<br /><br /> -改行なしの場合は、変更に関係なく、アセンブリの外側フィールドとパラメーターを宣言するメソッドの両方を表示できません。<br />改行の場合は、フィールドの名前を変更し、アセンブリ外見なすことができます。<br />-あり - パラメーターの名前を変更すると、アセンブリの外側に宣言するメソッドを確認できます。<br /><br /> フィールドと同じ名前を持つローカル変数で発生しました。<br /><br /> -改行なしの場合は、変更に関係なく、アセンブリの外側、フィールドを表示できません。<br />-改行なしの場合は、ローカル変数の名前を変更し、フィールドの名前は変更されません。<br />-あり - フィールドの名前を変更すると、アセンブリの外側に表示されることができます。|

## <a name="cause"></a>原因
 インスタンス メソッドでは、パラメーターまたは名前には、宣言型のインスタンス フィールドが一致するローカル変数を宣言します。 ルールに違反しているローカル変数をキャッチするには、デバッグ情報を使用してテスト済みのアセンブリをビルドし、関連付けられているプログラム データベース (.pdb) ファイルを使用する必要があります。

## <a name="rule-description"></a>規則の説明
 インスタンス フィールドの名前には、パラメーターまたはローカル変数の名前が一致すると、ときに、インスタンス フィールドを使用して、 `this` (`Me`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) メソッドの本文のキーワードです。 コードを保守する場合は、この違いを忘れたパラメーター/ローカル変数を指す、[インスタンス] フィールドは、エラーにつながることを想定して簡単です。 これは、時間のかかるメソッド本体に特に当てはまります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するのには、パラメーター/変数またはフィールドのいずれかの名前を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、ルールの 2 つの違反を示します。

 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]