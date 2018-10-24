---
title: 'CA1716: 識別子はキーワードと同一にすることはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfaef87f8463c43c412c5db3c83a899fb22b4f66
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862438"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: 識別子はキーワードと同一にすることはできません

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

名前空間、型、または viritual またはインターフェイス メンバーの名前では、プログラミング言語で予約済みキーワードと一致します。

## <a name="rule-description"></a>規則の説明

識別子の名前空間、型、および仮想インターフェイス メンバーを共通言語ランタイムを対象とする言語で定義されているキーワードと一致する必要があります。 によって使用される言語とキーワードの場合は、コンパイラのエラーやあいまいさづらくなる可能性、ライブラリを使用します。

このルールは、次の言語のキーワードを確認します。

- Visual Basic

- C#

- C++/CLI

大文字と小文字が使用される[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]他の言語キーワード、および大文字小文字の比較を使用します。

## <a name="how-to-fix-violations"></a>違反の修正方法

キーワードの一覧に表示されていない名前を選択します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

いる識別子は、API のユーザーを混同しないでおよびライブラリが .NET Framework で使用可能なすべての言語で使用できると確信している場合は、この規則による警告を抑制できます。