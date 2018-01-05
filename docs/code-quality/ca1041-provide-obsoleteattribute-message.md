---
title: "1041: ObsoleteAttribute メッセージを指定します |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a7536130842c78ca2c00bab1afc3caf842e02cba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute メッセージを指定します
|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 使用して、型またはメンバーになって、<xref:System.ObsoleteAttribute?displayProperty=fullName>属性を持たないその<xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>プロパティが指定されています。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.ObsoleteAttribute>非推奨のライブラリの型およびメンバーを示すために使用します。 ライブラリのコンシューマーは、任意の種類または旧式とマークされているメンバーの使用を避ける必要があります。 これはサポートされない可能性があり、、最終的に以降のバージョンのライブラリから削除されるためです。 型またはメンバーをマークされている場合を使用して<xref:System.ObsoleteAttribute>をコンパイルすると、<xref:System.ObsoleteAttribute.Message%2A>属性のプロパティが表示されます。 これによって、ユーザーは旧式の型またはメンバーに関する情報を知ることができます。 この情報には通常、旧式の型がどのくらいの時間が含まれています。 またはメンバーを使用するには、ライブラリのデザイナーと優先の交換によってサポートされます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには追加、`message`パラメーターを<xref:System.ObsoleteAttribute>コンス トラクターです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください、<xref:System.ObsoleteAttribute.Message%2A>プロパティは旧式の型またはメンバーに関する重要な情報を提供します。  
  
## <a name="example"></a>例  
 次の例は、旧式のメンバーを持つ、正しく宣言されている<xref:System.ObsoleteAttribute>です。  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## <a name="see-also"></a>参照  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>