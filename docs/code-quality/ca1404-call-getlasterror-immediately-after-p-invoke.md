---
title: 'Ca 1404: プラットフォーム呼び出しの直後に GetLastError を呼び出します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f29549f6b062a34a8b9e49bc7418b05d2d4e8831
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: P/Invoke の直後に GetLastError を呼び出します
|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 呼び出しが行われた、<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>メソッドまたは同等の Win32`GetLastError`関数が、直前に付属している呼び出しではプラットフォームにメソッドを呼び出します。

## <a name="rule-description"></a>規則の説明
 プラットフォームがメソッドへのアクセスのアンマネージ コードを呼び出すし、によって定義されている、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]または<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性。 一般に、障害時に、アンマネージ関数を呼び出して、Win32`SetLastError`エラーに関連付けられているエラー コードを設定します。 失敗した関数の呼び出し元の呼び出し、Win32`GetLastError`エラー コードを取得し、エラーの原因を判断する関数。 エラー コードは、スレッドごとに保持されは、次の呼び出しによって上書きされます`SetLastError`です。 マネージ コードが、エラー コードを呼び出すことによって取得できます障害が発生したプラットフォームへの呼び出しでは、メソッドを呼び出し後、<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>メソッドです。 エラー コードは、他のマネージ クラス ライブラリのメソッドから内部の呼び出しによって上書きできるので、`GetLastError`または<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>プラットフォーム呼び出しのメソッドの呼び出し後にすぐに、メソッドを呼び出す必要があります。

 ルールには、次の呼び出しは無視されます、プラットフォーム呼び出しの間で発生した場合に、マネージ メンバーを呼び出すメソッドを呼び出すまで<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>です。 これらのメンバーでは、エラーは変更しないで呼び出しメソッドの呼び出しのコードであり、一部のプラットフォームの成功を判断するのに役立ちます。

-   <xref:System.IntPtr.Zero?displayProperty=fullName>

-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、呼び出しに移動<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>メソッドを呼び出すプラットフォーム呼び出しの直後にできるようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 プラットフォーム間のコード呼び出しメソッドを呼び出す場合は、この規則による警告を抑制するのには安全では、<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>メソッドを呼び出すことはできません明示的または暗黙的に発生するエラー コードを変更します。

## <a name="example"></a>例
 次の例では、規則に違反するメソッドと、規則に適合するメソッドを示します。

 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA1060: 移動 P/invoke を NativeMethods クラス](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [1400: P/invoke エントリ ポイントが存在する必要があります。](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [Ca 1401: P/invoke になりません](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [Ca 2101: P/invoke 文字列引数に対してマーシャ リングを指定します。](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Win32 API に相当するマネージ API を使用します](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)