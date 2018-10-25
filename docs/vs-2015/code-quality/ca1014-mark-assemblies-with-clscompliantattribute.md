---
title: 'Ca 1014: アセンブリに CLSCompliantAttribute を設定する |Microsoft Docs'
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
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 60bc7b47e2bfa275f1a1b4f28138e968f15bbfd9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859485"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: アセンブリに CLSCompliantAttribute を設定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 アセンブリがない、<xref:System.CLSCompliantAttribute?displayProperty=fullName>属性が適用されています。

## <a name="rule-description"></a>規則の説明
 共通言語仕様 (CLS) には、名前付けの制約、データ型、および規則が定義されています。アセンブリを複数のプログラミング言語で使用する場合、この仕様に準拠する必要があります。 優れた設計では、すべてのアセンブリが CLS への準拠を明示的に示すことによって決まります<xref:System.CLSCompliantAttribute>します。 属性がアセンブリに存在しない場合は、アセンブリは、準拠していません。

 CLS 準拠のアセンブリ型が含まれますか準拠していないメンバーを入力することができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、アセンブリに属性を追加します。 非準拠としてアセンブリ全体を設定するには、代わりに、準拠していないし、そのため、これらの要素をマーク型または型のメンバーを決定する必要があります。 可能であれば、できるだけ多くが、アセンブリのすべての機能にアクセスできるように、非準拠メンバーを CLS 準拠の代替を提供する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 属性を適用し、その値に設定に準拠するアセンブリにしたくない場合`false`します。

## <a name="example"></a>例
 次の例では、アセンブリが、 <xref:System.CLSCompliantAttribute?displayProperty=fullName> CLS 準拠を宣言する属性が適用されています。

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>関連項目
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Language Independence and Language-independent Components](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



