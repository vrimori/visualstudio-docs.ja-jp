---
title: '1722: ca 識別子はな不適切なプレフィックス |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83843a7713adf3d0c3680470df05bb378c797d38
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591975"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: 識別子は不適切なプレフィックスを含むことはできません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1722: 識別子は不適切なプレフィックスをな](https://docs.microsoft.com/visualstudio/code-quality/ca1722-identifiers-should-not-have-incorrect-prefix)します。

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

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 識別子のプレフィックスを削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="related-rules"></a>関連規則
 [CA1715: 識別子は正しいプレフィックスを含んでいなければなりません](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)



