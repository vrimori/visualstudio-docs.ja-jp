---
title: "Ca 1017: アセンブリに ComVisibleAttribute をマーク |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e4c76efff009c85f9d607611d92d53cad5d2759
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: アセンブリに ComVisibleAttribute を設定します
|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 アセンブリがない、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>属性を適用します。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>属性は、COM クライアントがマネージ コードにアクセスする方法を決定します。 アセンブリで COM の参照範囲を明示することをお勧めします。 COM の参照範囲は、アセンブリ全体に設定し、それぞれの型と型のメンバー用にオーバーライドできます。 属性が存在しない場合、アセンブリのコンテンツは COM クライアントに表示されます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、アセンブリに属性を追加します。 属性を適用し、その値に設定されるアセンブリの COM クライアントで表示したくない場合`false`です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。 属性を適用し、その値に設定を表示するアセンブリを実行する場合に、`true`です。  
  
## <a name="example"></a>例  
 次の例では、アセンブリが、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> COM クライアントに表示されないようにする適用される属性です。  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)   
 [要件 (相互運用のための .NET 型の)](/dotnet/framework/interop/qualifying-net-types-for-interoperation)