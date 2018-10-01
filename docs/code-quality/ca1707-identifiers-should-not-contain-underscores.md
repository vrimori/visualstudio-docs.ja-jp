---
title: 'CA1707: 識別子はアンダースコアを含むことはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74746897f8ce27a79f666ae1d691b235035b4626
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548598"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: 識別子はアンダースコアを含むことはできません

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|重大なアセンブリで発生したときに<br /><br /> 非的な型パラメーターで発生したときに|

## <a name="cause"></a>原因

識別子の名前にアンダー スコアが含まれています (\_) 文字。

## <a name="rule-description"></a>規則の説明

慣例により、識別子名を含まない、アンダー スコア (\_) 文字。 このルールは、名前空間、型、メンバー、およびパラメーターを確認します。

名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法

名前からは、すべてのアンダー スコア文字を削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。

## <a name="related-rules"></a>関連するルール

- [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
