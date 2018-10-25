---
title: '1027: FlagsAttribute で列挙をマークする |Microsoft Docs'
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
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b8cebc05fa58c589f07beed70ab222d31bc8553a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879221"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: FlagsAttribute で列挙値をマークします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック列挙型の値は、列挙で定義されているその他の値の組み合わせは、2 の累乗と<xref:System.FlagsAttribute?displayProperty=fullName>属性が存在しません。 偽陽性を減らすためには、このルールは、連続した値を持つ列挙体の違反を報告しません。

## <a name="rule-description"></a>規則の説明
 列挙型は、関連する名前付き定数が複数定義された値型です。 適用<xref:System.FlagsAttribute>列挙型の名前付き定数を有意に結合できるときにします。 たとえば、利用できる日付のリソースの追跡するアプリケーションで曜日の列挙体を検討してください。 各リソースの可用性を持つ列挙型を使用してエンコードは<xref:System.FlagsAttribute>現在のところ、日の任意の組み合わせを表すことができます。 属性がない、週の 1 日だけを表すことができます。

 組み合わせ可能な列挙型を格納するフィールドの場合は、個々 の列挙値は、フィールド内のビットのグループとして扱われます。 そのため、このようなフィールドが呼ば*ビット フィールド*します。 ビット フィールドに格納するための列挙値を結合するには、ブール条件演算子を使用します。 特定の列挙値が存在するかどうかを決定するビット フィールドをテストするには、ブール型の論理演算子を使用します。 ビット フィールドを格納および結合された列挙値を正しく取得には、列挙体で定義されている各値は 2 の累乗である必要があります。 そうしないと、ブール型の論理演算子は、フィールドに格納されている個々 の列挙値を抽出できません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、次のように追加します。<xref:System.FlagsAttribute>列挙体にします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 列挙値を結合できるしたくない場合は、この規則による警告を抑制します。

## <a name="example"></a>例
 次の例では、`DaysEnumNeedsFlags`が列挙体を使用するための要件を満たす<xref:System.FlagsAttribute>、ことはありません。 `ColorEnumShouldNotHaveFlag`列挙体が 2 の累乗である値はありませんが、正しくないを指定します<xref:System.FlagsAttribute>します。 ルールに違反する[CA2217: FlagsAttribute で列挙をマークしない](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)します。

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.FlagsAttribute?displayProperty=fullName>



