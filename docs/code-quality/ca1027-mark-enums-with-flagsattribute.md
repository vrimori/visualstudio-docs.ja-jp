---
title: "1027 ca: マーク enums を FlagsAttribute |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e2fa3e93b8c4673a4b50b1baa46befbc01f7f7e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: FlagsAttribute で列挙値をマークします
|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 パブリック列挙型の値が 2 の累乗または、列挙で定義されている他の値の組み合わせであり、<xref:System.FlagsAttribute?displayProperty=fullName>属性が存在しません。 偽陽性を減らすためには、このルールは、連続した値を持つ列挙型の違反を報告しません。  
  
## <a name="rule-description"></a>規則の説明  
 列挙型は、関連する名前付き定数が複数定義された値型です。 適用<xref:System.FlagsAttribute>を名前付き定数を有意に結合できる場合、列挙値。 たとえば、曜日、追跡する曜日のリソースが利用可能なアプリケーションでの列挙体を検討してください。 各リソースの可用性を持つ列挙型を使用してエンコードされたかどうかは<xref:System.FlagsAttribute>現在のところ、日の任意の組み合わせを表すことができます。 属性がない 1 つの週の曜日のみを表すことができます。  
  
 組み合わせ可能な列挙体を格納するフィールド、個々 の列挙値は、フィールド内のビットのグループとして扱われます。 そのため、このようなフィールドとも呼ば*ビット フィールド*です。 記憶域、ビット フィールドの列挙値を結合するには、ブール条件演算子を使用します。 特定の列挙値が存在するかどうかを決定するビット フィールドをテストするには、ブール型の論理演算子を使用します。 ビット フィールドを保存し、結合された列挙値を正しく取得するには、列挙体で定義されている各値は 2 の累乗をする必要があります。 そうしないと、ブール型の論理演算子をフィールドに格納されている個々 の列挙値を抽出することはできません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、次のように追加します。<xref:System.FlagsAttribute>列挙体にします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 列挙値を結合できるしたくない場合は、この規則による警告を抑制します。  
  
## <a name="example"></a>例  
 次の例では、`DaysEnumNeedsFlags`列挙体を使用するための要件を満たすの<xref:System.FlagsAttribute>、ことはありません。 `ColorEnumShouldNotHaveFlag`列挙型は、2 の累乗値はありませんが、正しく指定されません<xref:System.FlagsAttribute>です。 ルールに違反する[CA2217: enums を FlagsAttribute のマークを付けないでください](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)です。  
  
 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.FlagsAttribute?displayProperty=fullName>