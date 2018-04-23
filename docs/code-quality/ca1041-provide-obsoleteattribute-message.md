---
title: 'CA1041: ObsoleteAttribute メッセージを指定します'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94a8204b2b19ae32fb8eb22438d747f4b4e0cf6c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
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
 <xref:System.ObsoleteAttribute> 非推奨のライブラリの型およびメンバーを示すために使用します。 ライブラリのコンシューマーは、任意の種類または旧式とマークされているメンバーの使用を避ける必要があります。 これはサポートされない可能性があり、、最終的に以降のバージョンのライブラリから削除されるためです。 型またはメンバーをマークされている場合を使用して<xref:System.ObsoleteAttribute>をコンパイルすると、<xref:System.ObsoleteAttribute.Message%2A>属性のプロパティが表示されます。 これによって、ユーザーは旧式の型またはメンバーに関する情報を知ることができます。 この情報には通常、旧式の型がどのくらいの時間が含まれています。 またはメンバーを使用するには、ライブラリのデザイナーと優先の交換によってサポートされます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには追加、`message`パラメーターを<xref:System.ObsoleteAttribute>コンス トラクターです。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください、<xref:System.ObsoleteAttribute.Message%2A>プロパティは旧式の型またはメンバーに関する重要な情報を提供します。

## <a name="example"></a>例
 次の例は、旧式のメンバーを持つ、正しく宣言されている<xref:System.ObsoleteAttribute>です。

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>関連項目
 <xref:System.ObsoleteAttribute?displayProperty=fullName>