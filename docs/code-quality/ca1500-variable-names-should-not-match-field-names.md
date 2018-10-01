---
title: 'CA1500: 変数名はフィールド名と同一にすることはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 74f9cfadc4bc413c3b176d5f37f1017074547435
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548278"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: 変数名はフィールド名と同一にすることはできません

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|カテゴリ|Microsoft.Maintainability|
|互換性に影響する変更点|フィールドと同じ名前を持つパラメーターで発生した: 場合<br /><br /> -改行なしの場合は、変更に関係なく、アセンブリ外フィールドとパラメーターを宣言するメソッドの両方を表示できません。<br />-重大 - フィールドの名前を変更し、アセンブリ外見なすことができます。<br />-重大な - パラメーターの名前を変更すると、アセンブリの外側に宣言するメソッドを確認できます。<br /><br /> フィールドと同じ名前を持つローカル変数で発生した: 場合<br /><br /> -改行なしで行った変更に関係なく、アセンブリの外部、フィールドを表示できない場合。<br />-改行なしの場合は、ローカル変数の名前を変更し、フィールドの名前は変更されません。<br />-重大な - フィールドの名前を変更すると、アセンブリの外側に表示されることができます。|

## <a name="cause"></a>原因

インスタンス メソッドでは、パラメーターまたは宣言型のインスタンス フィールドと一致する名前を持つローカル変数を宣言します。 ルールに違反しているローカル変数をキャッチするには、デバッグ情報を使用してテスト対象のアセンブリをビルドし、関連付けられているプログラム データベース (.pdb) ファイルは、使用可能なである必要があります。

## <a name="rule-description"></a>規則の説明

インスタンス フィールドを使用してアクセスするインスタンス フィールドの名前には、パラメーターまたはローカル変数の名前が一致すると、 `this` (`Me`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) メソッドの本文のキーワード。 コードを保守する際に、簡単に、この違いを忘れるし、パラメーターまたはローカル変数がエラーにつながるインスタンス フィールドを指すことを前提としています。 これは時間のかかるメソッド本体に特に当てはまります。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するのには、パラメーター/変数またはフィールドのいずれかの名前を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。

## <a name="example"></a>例

次の例では、ルールの 2 つの違反を示します。

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]