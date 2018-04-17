---
title: 'Ca 1408: AutoDual ClassInterfaceType を使用しないで |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ee8c016896381814aa5406b4023e24799f29219
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: AutoDual ClassInterfaceType を使用しないでください
|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|カテゴリ|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 コンポーネント オブジェクト モデル (COM) 参照できる型が付いて、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性に設定、`AutoDual`値<xref:System.Runtime.InteropServices.ClassInterfaceType>です。  
  
## <a name="rule-description"></a>規則の説明  
 デュアル インターフェイスを使用する型を使用することで、クライアントを特定のインターフェイス レイアウトに対応付けることができます。 将来のバージョンで、この型またはその基本型のレイアウトに変更が加えられると、インターフェイスに対応付けられた COM クライアントが切り離されます。 既定では場合、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性が指定されていない、ディスパッチ専用インターフェイスを使用します。  
  
 他のマークがない限り、すべてのパブリックの非ジェネリック型は COM; から参照できます。すべてのパブリックでないとジェネリック型を COM に表示されません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、値を変更、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性を`None`の値<xref:System.Runtime.InteropServices.ClassInterfaceType>し、明示的にインターフェイスを定義します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 将来のバージョンでは、型およびその基本型のレイアウトを変更しないというが確実である場合を除き、この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、規則に違反すると、明示的なインターフェイスを使用してクラスの再宣言するクラスを示します。  
  
 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1403: Auto 配置の型を COM 参照可能にすることはできません](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: ComSource インターフェイスを IDispatch として設定します](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## <a name="see-also"></a>関連項目  
 [要件 (相互運用のための .NET 型の)](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)