---
title: 'CA1014: アセンブリに CLSCompliantAttribute を設定します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51e5a43a402bb215a939b37354dd30f24e4d5d14
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: アセンブリに CLSCompliantAttribute を設定します
|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 アセンブリがない、<xref:System.CLSCompliantAttribute?displayProperty=fullName>属性を適用します。

## <a name="rule-description"></a>規則の説明
 共通言語仕様 (CLS) には、名前付けの制約、データ型、および規則が定義されています。アセンブリを複数のプログラミング言語で使用する場合、この仕様に準拠する必要があります。 優れた設計ですべてのアセンブリが CLS への準拠を明示こと<xref:System.CLSCompliantAttribute>です。 属性がアセンブリに存在しない場合は、アセンブリが準拠していません。

 CLS 準拠のアセンブリ型が含まれますかに準拠していないメンバーを入力することができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、アセンブリに属性を追加します。 非準拠としてアセンブリ全体をマークするには、代わりに準拠していないと、その要素をマーク型または型のメンバーを決定する必要があります。 可能であれば、最も幅の広い可能な対象ユーザーが、アセンブリのすべての機能にアクセスできるようにする、非準拠メンバーの CLS 準拠の代替を指定する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 準拠しているアセンブリしたくない場合、属性を適用し、その値に設定`false`です。

## <a name="example"></a>例
 次の例では、アセンブリが、 <xref:System.CLSCompliantAttribute?displayProperty=fullName> CLS に準拠して宣言する属性が適用されます。

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>関連項目
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [言語非依存および言語非依存コンポーネント](/dotnet/standard/language-independence-and-language-independent-components)