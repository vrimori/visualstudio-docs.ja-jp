---
title: '2146: 型は、基本型およびインターフェイスと、少なくとも 重要ななければ |Microsoft Docs'
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
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 09b6c1ca57582ee17f048220bbb73f7605883df7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589664"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: 型は、基本型およびインターフェイスと同程度以上、重要でなければならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2146: 型は、少なくとも、基本型およびインターフェイスと同程度に重要である必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces)します。

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透過的な型はでマークされている型から派生、<xref:System.Security.SecuritySafeCriticalAttribute>または<xref:System.Security.SecurityCriticalAttribute>、またはでマークされている型、<xref:System.Security.SecuritySafeCriticalAttribute>属性でマークされている型から派生、<xref:System.Security.SecurityCriticalAttribute>属性。

## <a name="rule-description"></a>規則の説明
 派生型に透過的セキュリティ属性が設定されていて、この属性が基本型または実装されたインターフェイスほど重要ではない場合に、この規則が適用されます。 クリティカルな基本型から派生したり、クリティカルなインターフェイスを実装したりできるのは、クリティカルなデータ型だけです。また、セーフ クリティカルな基本型から派生したり、セーフ クリティカルなインターフェイスを実装したりできるのは、クリティカルまたはセーフ クリティカルなデータ型だけです。 レベル 2 の透過性では、この規則の違反が発生する、<xref:System.TypeLoadException>の派生型。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この違反を修正するには、少なくともほど重要では、基本型またはインターフェイスの透過性属性を持つ派生または実装する型をマークします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]



