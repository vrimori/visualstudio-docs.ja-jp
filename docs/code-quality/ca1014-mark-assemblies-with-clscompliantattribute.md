---
title: CA1014:アセンブリに CLSCompliantAttribute を設定します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3c97d7731cc3bbad98ce5b62346bab1b7d5029ea
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986645"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014:アセンブリに CLSCompliantAttribute を設定します

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

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。 属性を適用し、その値に設定に準拠するアセンブリにしたくない場合`false`します。

## <a name="example"></a>例
 次の例では、アセンブリが、 <xref:System.CLSCompliantAttribute?displayProperty=fullName> CLS 準拠を宣言する属性が適用されています。

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>関連項目

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [言語への非依存性、および言語非依存コンポーネント](/dotnet/standard/language-independence-and-language-independent-components)