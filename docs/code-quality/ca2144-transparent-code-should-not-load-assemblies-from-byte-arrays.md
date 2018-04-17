---
title: 'Ca 2144: バイト配列から、透過的なコードはアセンブリを読み込む必要がありますいない |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed5f7e94d47145f6b6eea3c70108f9202b884443
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: 透過的コードは、バイト配列からアセンブリを読み込んではならない
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|CheckId|CA2144|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 透過的メソッドは、次のいずれかを使用してバイト配列からアセンブリを読み込みます。  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## <a name="rule-description"></a>規則の説明  
 透過的なコードはセキュリティ上重要な操作を実行できないため、透過的なコードのセキュリティ レビューは、クリティカル コードのセキュリティ レビューほど完全ではありません。 バイト配列から読み込まれるアセンブリは透過的なコード内で認識されない場合がありますが、監査を必要とする、クリティカルなコード、またはさらに重要であるセーフ クリティカルなコードがそのバイト配列に含まれる可能性があります。 そのため、透過的なコードは、バイト配列からアセンブリを読み込んで必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、使用して、アセンブリを読み込んでいるメソッドをマーク、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 ルールは、透過的メソッドは、バイト配列からアセンブリを読み込むために、次のコードに対して適用されます。  
  
 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]