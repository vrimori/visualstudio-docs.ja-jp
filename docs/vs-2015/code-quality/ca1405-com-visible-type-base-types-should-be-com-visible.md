---
title: 'Ca 1405: COM から参照できる型の基本データ型は COM 参照可能である必要があります |Microsoft Docs'
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
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 43f18eb26cdbdf6ce97a17d2cc3f14dbecb62540
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200760"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: COM 参照可能な型の基本型は COM 参照可能でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|DependsOnFix|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) 参照できる型は、COM 参照可能でない型から派生します。

## <a name="rule-description"></a>規則の説明
 COM から参照できる型では、新しいバージョンのメンバーを追加、ときに、現在のバージョンにバインドされた COM クライアントが壊れないように厳密なガイドラインに従う必要があります。 COM から参照できる型では、COM のバージョン管理規則に従うと、新しいメンバーを追加する必要はありませんが前提としています。 場合は、COM 参照可能型は COM の非表示の型から派生しのクラス インターフェイスを公開<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>または<xref:System.Runtime.InteropServices.ClassInterfaceType>(既定)、基本型のすべてのパブリック メンバー (専用としてマークされている COM 非表示をしない限り、このことは不要)COM に公開されます。 基本データ型は、以降のバージョンで新しいメンバーを追加する場合は、派生型のクラス インターフェイスにバインドされた COM クライアントが壊れる可能性があります。 COM 参照可能な型は、COM クライアントの可能性を低減する COM 参照可能な型からのみ派生する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、基本型を COM 参照可能または派生型を COM を非表示にします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反する型を示します。

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [クラス インターフェイスの概要](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)[アンマネージ コードと相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



