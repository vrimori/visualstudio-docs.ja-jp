---
title: 'CA2141: 透過的メソッドは LinkDemands を満たす必要がありますされません |Microsoft Docs'
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
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b97a8b7f5e59da0eadf3be8f1867571a256282ca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589760"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: 透過的メソッドは、LinkDemand を満たしてはならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2141: 透過的メソッドは LinkDemands を満たす必要がありますいない](https://docs.microsoft.com/visualstudio/code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands)します。

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透過的セキュリティ メソッドとマークされていないアセンブリ メソッドを呼び出し、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性、または透過的セキュリティ メソッドを満たす、 <xref:System.Security.Permissions.SecurityAction> `.LinkDemand`型またはメソッドの。

## <a name="rule-description"></a>規則の説明
 特権が意図せず昇格される可能性があるセキュリティ センシティブな操作は、LinkDemand を満たします。 セキュリティ クリティカルなコードと同じセキュリティ監査要件の対象ではないために、透過的セキュリティ コードは、LinkDemands を満たしていませんする必要があります。 セキュリティ規則セットのレベル 1 アセンブリ内の透過的メソッドには、パフォーマンスの問題が発生することができますが、実行時にフル アクセス要求に変換する必要を満たすすべての LinkDemands が発生します。 セキュリティ規則のセットのレベル 2 のアセンブリ、LinkDemand を満たすために試行された場合は、ジャストイン タイム (JIT) コンパイラでコンパイルする透過的メソッドは失敗します。

 アセンブリでその機能を使用レベル 2 のセキュリティ、LinkDemand を満たしていない APTCA アセンブリのメソッドを呼び出すには透過的セキュリティ メソッドによる試行を発生させます、<xref:System.MethodAccessException>レベル 1 アセンブリでは、LinkDemand をフル アクセス要求になります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するとにアクセスするメソッドをマーク、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性、またはアクセスされるメソッドから、LinkDemand を削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 この例では、透過的メソッドは、LinkDemand を含むメソッドを呼び出すしようとします。 このルールは、このコードで起動されます。

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]



