---
title: '1724: ca 型名と名前空間 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5331a32db054b1cb3939bbfd3ba088ab5da33f96
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903180"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: 型名は名前空間と同一にすることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型名と一致する、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]大文字と小文字の名前空間の名前。

## <a name="rule-description"></a>規則の説明
 型の名前は、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] クラス ライブラリで定義されている名前空間の名前と一致しないようにする必要があります。 この規則に違反すると、ライブラリが使いづらくなります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 名前に一致しない型の名前を選択して、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]クラス ライブラリの名前空間。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 新たに開発されていないシナリオが発生する、この規則による警告を抑制する必要があります。 警告を抑制する前に一致する名前で、ライブラリのユーザーを混乱する可能性がある方法慎重に検討してください。 ライブラリを配布するには、この規則による警告を抑制する必要があります。



