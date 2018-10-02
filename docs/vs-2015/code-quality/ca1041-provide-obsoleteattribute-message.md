---
title: '1041: ObsoleteAttribute メッセージを指定 |Microsoft Docs'
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
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 298f6d3cbfc8b71443fe9e8e9733e5729963cea8
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592359"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute メッセージを指定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1041: 提供 ObsoleteAttribute メッセージ](https://docs.microsoft.com/visualstudio/code-quality/ca1041-provide-obsoleteattribute-message)します。

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 使用して、型またはメンバーになって、<xref:System.ObsoleteAttribute?displayProperty=fullName>属性がないその<xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>プロパティを指定します。

## <a name="rule-description"></a>規則の説明
 <xref:System.ObsoleteAttribute> 非推奨のライブラリの型およびメンバーを示すために使用します。 ライブラリのコンシューマーは、任意の型または不使用とマークされているメンバーの使用を避ける必要があります。 これは、サポートされない可能性がありますには最終的に、ライブラリの以降のバージョンから削除するためです。 型またはメンバーをマークを使用して<xref:System.ObsoleteAttribute>がコンパイルされる、<xref:System.ObsoleteAttribute.Message%2A>属性のプロパティが表示されます。 これによって、ユーザーは旧式の型またはメンバーに関する情報を知ることができます。 この情報には、旧式の型がどのくらいの時間通常が含まれます。 またはメンバーを使用するには、ライブラリの設計者と優先の交換によってサポートされます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、追加、`message`パラメーターを<xref:System.ObsoleteAttribute>コンス トラクター。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制しないでください、<xref:System.ObsoleteAttribute.Message%2A>プロパティは、旧式の型またはメンバーに関する重要な情報を提供します。

## <a name="example"></a>例
 次の例は、旧式のメンバーを持つ、正しく宣言<xref:System.ObsoleteAttribute>します。

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>関連項目
 <xref:System.ObsoleteAttribute?displayProperty=fullName>



