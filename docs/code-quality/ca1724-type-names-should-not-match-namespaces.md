---
title: 'CA1724: 型名は名前空間と同一にすることはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: c178558743ca69fb3b62eccaf8164e4b49167ad3
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547569"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: 型名は名前空間と同一にすることはできません
|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型名と一致する、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]大文字と小文字の名前空間の名前。

## <a name="rule-description"></a>規則の説明
 型の名前は、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリで定義されている名前空間の名前と一致しないようにする必要があります。 この規則に違反すると、ライブラリが使いづらくなります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 名前に一致しない型の名前を選択して、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]クラス ライブラリの名前空間。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 新たに開発されていないシナリオが発生する、この規則による警告を抑制する必要があります。 警告を抑制する前に一致する名前で、ライブラリのユーザーを混乱する可能性がある方法慎重に検討してください。 ライブラリを配布するには、この規則による警告を抑制する必要があります。