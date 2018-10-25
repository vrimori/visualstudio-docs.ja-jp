---
title: '1722: ca 識別子はな不適切なプレフィックス |Microsoft Docs'
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
ms.openlocfilehash: ca506e853d2f32a7932620ff576a2769574f1cc7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921302"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: 識別子は不適切なプレフィックスを含むことはできません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



