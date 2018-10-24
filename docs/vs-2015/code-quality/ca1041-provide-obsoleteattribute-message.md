---
title: '1041: ObsoleteAttribute メッセージを指定 |Microsoft Docs'
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
ms.openlocfilehash: f67bbd93816da3bcae389493b74623f0cf4776c0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914724"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute メッセージを指定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



