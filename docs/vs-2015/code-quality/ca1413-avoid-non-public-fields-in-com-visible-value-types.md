---
title: ': Ca 1413 COM 参照可能な値の型で非パブリック フィールド |Microsoft Docs'
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
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 041dbcb355a5aa3bd6925fcabe2d3f815f990890
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935095"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている値の型は、非パブリック インスタンス フィールドを宣言します。

## <a name="rule-description"></a>規則の説明
 COM から参照できる値型の非パブリック インスタンス フィールドは、COM クライアントで表示できます。 情報を公開してはなりません、または意図しないデザインまたはセキュリティ効果が含まれてのフィールドの内容を確認します。

 既定では、すべてのパブリック値型が COM から参照 ただし、偽陽性を減らすためには、この規則を明示的に指定する型の COM の参照範囲が必要です。 格納しているアセンブリをマークする必要があります、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>に設定`false`で型をマークする必要があり、<xref:System.Runtime.InteropServices.ComVisibleAttribute>に設定`true`します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 非表示フィールドの変更にこの規則の違反を修正するには、参照型に値の型を変更または削除、<xref:System.Runtime.InteropServices.ComVisibleAttribute>型からの属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 フィールドをパブリックに公開が許容される場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目
 [アンマネージ コードと相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)[の相互運用性に対応する .NET 型](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)



