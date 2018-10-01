---
title: 'CA1715: 識別子は正しいプレフィックスを含んでいなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e3e040b659b4e4b1484f7557a3ccececffa20e2
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549920"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: 識別子は正しいプレフィックスを含んでいなければなりません
|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|– インターフェイスで発生した場合。<br /><br /> 改行のジェネリック型パラメーターで発生したときにします。|

## <a name="cause"></a>原因
 外部から参照できるインターフェイスの名前の先頭が大文字の 'I' でありません。

 - または -

 外部から参照できる型またはメソッドのジェネリック型パラメーターの名前値で始まらない大文字 ' T '。

## <a name="rule-description"></a>規則の説明
 慣例により、特定のプログラミング要素の名前は固有のプレフィックスで開始します。

 インターフェイス名は、大文字、もう 1 つの大文字が続く 'I' で始める必要があります。 このルールは、'MyInterface' や 'IsolatedInterface' などのインターフェイス名の違反を報告します。

 ジェネリック型パラメーターの名前が大文字で始まる、' T ' 必要に応じて、もう 1 つの大文字が続く可能性があります。 このルールは、'V' と 'Type' などのジェネリック型パラメーターの名前の違反を報告します。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 識別子の名前を変更して、プレフィックスが正しくようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 **次の例では、不適切な名前のインターフェイスを示します。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>例
 **次の例では、'I' とインターフェイスを付けることで以前の違反を修正します。**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>例
 **次の例は、不適切な名前のジェネリック型パラメーターを示します。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

## <a name="example"></a>例
 **次の例では、' T のジェネリック型パラメーターを付けることで、前の違反を修正する '。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>関連するルール
 [CA1722: 識別子は不適切なプレフィックスを含むことはできません。](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)