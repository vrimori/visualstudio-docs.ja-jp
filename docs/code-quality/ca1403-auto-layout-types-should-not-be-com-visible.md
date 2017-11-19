---
title: "Ca 1403: Auto 配置の型が COM 参照することはできません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e5f8617b7ed5f0bec9ecaa2f4fbca1653cee46f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Auto 配置の型を COM 参照可能にすることはできません
|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|カテゴリ|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 コンポーネント オブジェクト モデル (COM) 参照可能な値の型が付いて、<xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>属性に設定<xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>です。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.Runtime.InteropServices.LayoutKind>レイアウトのタイプは、共通言語ランタイムによって管理されます。 これらの型のレイアウトは、COM クライアントが特定のレイアウトが予期される動作しなくなる .NET Framework のバージョン間で変更できます。 されている場合、<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性が指定されていない、c#、 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]、C++ コンパイラを指定し、<xref:System.Runtime.InteropServices.LayoutKind>のレイアウトを値型です。  
  
 他のマークがない限り、すべてのパブリックの非ジェネリック型は COM; から参照できます。すべてのパブリックでないとジェネリック型を COM に表示されません。 ただし、偽陽性を減らすためには、この規則が必要、COM 型の可視性、明示的に指定します。格納しているアセンブリをマークする必要があります、 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 'éý'`false`で型をマークする必要がありますと、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 'éý'`true`です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、値を変更、<xref:System.Runtime.InteropServices.StructLayoutAttribute>属性を<xref:System.Runtime.InteropServices.LayoutKind>または<xref:System.Runtime.InteropServices.LayoutKind>、か、com 型を非表示  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、規則に違反する型と、規則に適合する型を示します。  
  
 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1408: AutoDual ClassInterfaceType を使用しないでください](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>関連項目  
 [クラス インターフェイスの概要](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [要件 (相互運用のための .NET 型の)](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)