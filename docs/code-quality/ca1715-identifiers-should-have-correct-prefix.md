---
title: 'CA1715: 識別子は正しいプレフィックスを含んでいなければなりません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b4ddef7b6a9ae7eafb6c169ec9e07e89e20fc6b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: 識別子は正しいプレフィックスを含んでいなければなりません
|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|– インターフェイスで発生した場合。<br /><br /> 改行のジェネリック型パラメーターで発生するとします。|

## <a name="cause"></a>原因
 外部から参照できるインターフェイスの名前は、大文字の 'I' で始まらないです。

 - または -

 外部から参照できる型またはメソッドのジェネリック型パラメーターの名前で始まらない大文字 'T' です。

## <a name="rule-description"></a>規則の説明
 規則では、特定のプログラミング要素の名前は、特定のプレフィックスで開始します。

 インターフェイスの名前は、別の文字を大文字に続く 'I' 大文字で開始する必要があります。 このルールは、'MyInterface' や 'IsolatedInterface' などのインターフェイス名の違反を報告します。

 ジェネリック型パラメーター名は、まず大文字の 'T' 必要に応じて、後に別の文字が大文字でします。 このルールは、ジェネリック型パラメーター名 'V' と 'Type' などの違反を報告します。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 識別子の名前を変更して、プレフィックスが正しくようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 **次の例では、不適切な名前のインターフェイスを示します。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>例
 **次の例では、'I' とインターフェイスを付けることによって上記の違反を修正します。**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>例
 **次の例では、不適切な名前のジェネリック型パラメーターを示します。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

## <a name="example"></a>例
 **次の例では、以前の違反を修正、ジェネリック型パラメーターに"t"を付けることによって ' です。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>関連規則
 [CA1722: 識別子は不適切なプレフィックスを含むことはできません。](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)