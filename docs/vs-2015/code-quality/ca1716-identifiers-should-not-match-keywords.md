---
title: '1716: ca 識別子とキーワード |Microsoft Docs'
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
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 000e28642a10c565e525b2714eed0d7abaca9340
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858876"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: 識別子はキーワードと同一にすることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

  大文字と小文字が使用される[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]他の言語キーワード、および大文字小文字の比較を使用します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 キーワードの一覧に表示されていない名前を選択します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールから警告を抑制するには、識別子は、API のユーザーを混同しないでことと、ライブラリが使用可能なすべての言語で使用できることと確信している場合、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]します。



