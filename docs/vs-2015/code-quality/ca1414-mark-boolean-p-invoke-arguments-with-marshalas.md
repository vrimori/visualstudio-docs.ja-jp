---
title: 'Ca 1414: ブール型の P/invoke 引数を MarshalAs のマーク |Microsoft Docs'
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
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7f8378d2b3f498146fc960e57d1d3562827fe347
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918403"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: ブール型の P/Invoke 引数を MarshalAs に設定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメソッド宣言に含まれる、<xref:System.Boolean?displayProperty=fullName>パラメーターまたは戻り値が、<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>属性は、パラメーターまたは戻り値には適用されません。

## <a name="rule-description"></a>規則の説明
 プラットフォームがメソッドへのアクセスのアンマネージ コードを呼び出すし、によって定義されている、`Declare`キーワード[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]または<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>します。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> マネージ コードとアンマネージ コード間のデータ型の変換に使用されるマーシャ リング動作を指定します。 などの多くの単純なデータ型<xref:System.Byte?displayProperty=fullName>と<xref:System.Int32?displayProperty=fullName>、アンマネージ コードに 1 つの表現がある、マーシャ リング動作の仕様を必要としない、共通言語ランタイムが自動的に正しい動作を提供します。

 <xref:System.Boolean>データ型が、アンマネージ コードの複数の表現。 ときに、<xref:System.Runtime.InteropServices.MarshalAsAttribute>が指定されていない、既定のマーシャ リングの動作、<xref:System.Boolean>データ型は<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>します。 これは、すべての状況では、32 ビットの整数です。 アンマネージ メソッドで必要とされるブール型の表現を特定する必要がありますし、適切な一致<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>します。 UnmanagedType.Bool は、常に 4 バイトある Win32 BOOL 型です。 C++ の UnmanagedType.U1 を使用する必要があります`bool`またはその他の 1 バイトの種類。 詳細については、次を参照してください。[ブール型の既定のマーシャ リング](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、次のように適用されます。<xref:System.Runtime.InteropServices.MarshalAsAttribute>を、<xref:System.Boolean>パラメーターまたは戻り値。 適切な属性の値を設定<xref:System.Runtime.InteropServices.UnmanagedType>します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 既定のマーシャ リング動作が適切な場合でも、コードは、動作が明示的に指定されたときに維持より簡単にします。

## <a name="example"></a>例
 次の例は、2 つのプラットフォーム呼び出しメソッドに、適切なでマークされている<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性。

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1901: P/Invoke 宣言はポータブルでなければなりません](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [既定のブール型のマーシャ リング](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)[アンマネージ コードと相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



