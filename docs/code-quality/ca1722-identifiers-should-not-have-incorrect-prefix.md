---
title: CA1722:識別子は不適切なプレフィックスを含むことはできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e997bce3c3e6cd96478e5b7ba6899d8563b4ac7e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029675"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722:識別子は不適切なプレフィックスを含むことはできません

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 識別子が、不適切なプレフィックス。

## <a name="rule-description"></a>規則の説明
 規則では、特定のプログラミング要素にのみ、固有のプレフィックスで始まる名前を付けることができます。

 型名は、特定のプレフィックスがないといません 'C' を付ける必要があります。 このルールは、'CMyClass' などの型名の違反を報告し、違反の 'Cache' などの型名はレポートされません。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 この一貫性では、学習曲線を新しいソフトウェア ライブラリに必要なライブラリがマネージ コード開発の専門知識を持つユーザーによって開発された、顧客の信頼度が高まりますが減少します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 識別子のプレフィックスを削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="related-rules"></a>関連するルール
 [CA1715:識別子は正しいプレフィックスをいなければなりません](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)