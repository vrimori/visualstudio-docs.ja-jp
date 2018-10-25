---
title: 'Ca 1403: Auto 配置の型が COM に表示することはできません |Microsoft Docs'
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
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e6f675c2d13efbf029aa515402be4bf75bad867e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816853"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Auto 配置の型を COM 参照可能にすることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) 参照可能な値の型が付いて、<xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>属性に設定<xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 <xref:System.Runtime.InteropServices.LayoutKind> レイアウトの種類は、共通言語ランタイムによって管理されます。 これらの型のレイアウトは、COM クライアントが特定のレイアウトが予期される動作しなくなる .NET Framework のバージョン間で変更できます。 されている場合、<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性が指定されていない、c#、 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]、C++ コンパイラを指定し、<xref:System.Runtime.InteropServices.LayoutKind>値型のレイアウト。

 それ以外の場合にマークされている場合は、すべてのパブリックの非ジェネリック型の COM; から参照できるものすべての非パブリックとジェネリック型が COM に表示されません。 ただし、偽陽性を減らすためには、このルールが必要です。 明示的に指定する対象の型の COM の参照範囲格納しているアセンブリをマークする必要があります、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>に設定`false`で型をマークする必要があり、<xref:System.Runtime.InteropServices.ComVisibleAttribute>に設定`true`します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、値を変更、<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性を<xref:System.Runtime.InteropServices.LayoutKind>または<xref:System.Runtime.InteropServices.LayoutKind>、か、com 型を非表示

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反する型と、規則に適合する型を示します。

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1408: AutoDual ClassInterfaceType を使用しないでください](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>関連項目
 [クラス インターフェイスの概要](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)[相互運用のための .NET 型を修飾](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)[アンマネージ コードと相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



