---
title: CA1414:ブール型の P/Invoke 引数を MarshalAs に設定します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 68b0400e366f70690acb7a04b425472e0059b726
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021976"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414:ブール型の P/Invoke 引数を MarshalAs に設定します

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメソッド宣言に含まれる、<xref:System.Boolean?displayProperty=fullName>パラメーターまたは戻り値が、<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>属性は、パラメーターまたは戻り値には適用されません。

## <a name="rule-description"></a>規則の説明
 プラットフォームがメソッドへのアクセスのアンマネージ コードを呼び出すし、によって定義されている、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]または<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>します。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> マネージ コードとアンマネージ コード間のデータ型の変換に使用されるマーシャ リング動作を指定します。 などの多くの単純なデータ型<xref:System.Byte?displayProperty=fullName>と<xref:System.Int32?displayProperty=fullName>、アンマネージ コードに 1 つの表現がある、マーシャ リング動作の仕様を必要としない、共通言語ランタイムが自動的に正しい動作を提供します。

 <xref:System.Boolean>データ型が、アンマネージ コードの複数の表現。 ときに、<xref:System.Runtime.InteropServices.MarshalAsAttribute>が指定されていない、既定のマーシャ リングの動作、<xref:System.Boolean>データ型は<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>します。 これは、すべての状況では、32 ビットの整数です。 アンマネージ メソッドで必要とされるブール型の表現を特定する必要がありますし、適切な一致<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>します。 UnmanagedType.Bool は、常に 4 バイトある Win32 BOOL 型です。 C++ の UnmanagedType.U1 を使用する必要があります`bool`またはその他の 1 バイトの種類。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、次のように適用されます。<xref:System.Runtime.InteropServices.MarshalAsAttribute>を、<xref:System.Boolean>パラメーターまたは戻り値。 適切な属性の値を設定<xref:System.Runtime.InteropServices.UnmanagedType>します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。 既定のマーシャ リング動作が適切な場合でも、コードは、動作が明示的に指定されたときに維持より簡単にします。

## <a name="example"></a>例

プラットフォーム呼び出しメソッドに、適切なでマークされている次の例は<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性。

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>関連するルール
 [CA1901:P/invoke 宣言はポータブルでなければなりません](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA 2101:P/invoke 文字列引数に対してマーシャ リングを指定します。](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)