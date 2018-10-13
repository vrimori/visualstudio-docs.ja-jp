---
title: '1708: 識別子は、大文字小文字以外で相違する必要があります |Microsoft Docs'
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
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 07f4b9f9a69de3458bf0f7ea7dcb316e2e9a086a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187643"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 2 つの型、メンバー、パラメーター、または完全修飾名前空間の名前は、小文字に変換されるときと同じです。

## <a name="rule-description"></a>規則の説明
 名前空間、型、メンバー、およびパラメーターの各識別子は、大文字/小文字以外のみでは区別できません。共通言語ランタイムを対象とする言語は、大文字と小文字を区別する必要はないためです。 たとえば、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]は広く使用されている大文字言語です。

 この規則は、公開されているメンバーのみに適用されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 大文字と小文字の他の識別子を比較した場合に一意の名前を選択します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 ライブラリで使用可能なすべての言語で使用できない可能性があります、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]します。

## <a name="example-of-a-violation"></a>違反の例
 次の例では、この規則違反を示します。

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)



