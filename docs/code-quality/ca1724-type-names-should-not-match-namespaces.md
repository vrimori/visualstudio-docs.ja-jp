---
title: CA1724:型名は名前空間と同一にすることはできません
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c28bf4af55e1c12045357a76e3488ff4083fcee5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848942"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724:型名が名前空間と一致する必要があります。

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

型名では、1 つまたは複数の外部から参照できる型を持つ参照先の名前空間の名前と一致します。 大文字と小文字は名前の比較です。

## <a name="rule-description"></a>規則の説明

ユーザーが作成した型名は、外部から参照できる型を持つ参照先の名前空間の名前と一致する必要があります。 この規則に違反すると、ライブラリの使いやすさを減らすことができます。

## <a name="how-to-fix-violations"></a>違反の修正方法

型の名前を変更して、外部から参照できる型を持つ参照される名前空間の名前に一致しないようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

新たに開発されていないシナリオが発生する、この規則による警告を抑制する必要があります。 警告を抑制する前に一致する名前で、ライブラリのユーザーを混乱する可能性がある方法慎重に検討してください。 ライブラリを配布するには、この規則による警告を抑制する必要があります。