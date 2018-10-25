---
title: 'CA1719: パラメーター名はメンバー名と同一にすることはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64a10bd39ef34d207d910c3bc428ba862019369e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924019"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: パラメーター名はメンバー名と同一にすることはできません

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できるメンバーの名前は、大文字と小文字をそのパラメーターの 1 つの名前と一致します。

## <a name="rule-description"></a>規則の説明
 パラメーターはパラメーターの意味、メンバーはメンバーの意味を伝える名前にします。 この 2 つの名前が一致するデザインは、まれにしか見られません。 パラメーターにメンバーと同じ名前を付けるとわかりづらくなり、ライブラリの操作が難しくなります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 メンバー名に一致しないパラメーター名を選択します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 新たに開発されていないシナリオが発生する、この規則による警告を抑制する必要があります。 ライブラリを配布するには、この規則による警告を抑制する必要があります。

## <a name="related-rules"></a>関連するルール
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: 識別子はアンダースコアを含むことはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)