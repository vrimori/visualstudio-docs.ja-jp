---
title: CA1404:P-Invoke の直後に GetLastError を呼び出します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ae16f99aefe4411b345a1b135c7f014a1061911
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963111"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404:P/Invoke の直後に GetLastError を呼び出します

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

呼び出し、<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>メソッドまたは同等の Win32`GetLastError`関数、およびは直前の呼び出しでないプラットフォームにメソッドを呼び出します。

## <a name="rule-description"></a>規則の説明
 プラットフォームがメソッドへのアクセスのアンマネージ コードを呼び出すし、によって定義されている、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]または<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性。 一般に、障害時に、アンマネージ関数呼び出し、Win32`SetLastError`エラーに関連付けられているエラー コードを設定します。 失敗した関数の呼び出し元の呼び出し、Win32`GetLastError`エラー コードを取得し、エラーの原因を特定する関数。 エラー コードはスレッドごと上で管理され、次回の呼び出しによって上書きされます`SetLastError`します。 マネージ コードが呼び出すことで、エラー コードを取得後、失敗したプラットフォームへの呼び出しでは、メソッドを呼び出し、<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>メソッド。 エラー コードは、その他のマネージ クラス ライブラリのメソッドから内部の呼び出しによって上書きできるので、`GetLastError`または<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>プラットフォーム呼び出しメソッドの呼び出し後にすぐに、メソッドを呼び出す必要があります。

 規則は、次の呼び出し、プラットフォームへの呼び出しの間で発生したときに管理対象のメンバーを呼び出すメソッドを呼び出す<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>します。 これらのメンバーでは、エラーは変更しないで呼び出しメソッドの呼び出しのコードとはいくつかのプラットフォームの成功を判断するのに役立ちます。

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するへの呼び出しを移動<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>メソッドの呼び出しに、プラットフォームへの呼び出し直後に続くようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 プラットフォーム間でコードがメソッドの呼び出しを呼び出す場合は、この規則による警告を抑制するのには安全では、<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>メソッドの呼び出しできません明示的または暗黙的に発生するエラー コードを変更します。

## <a name="example"></a>例
 次の例では、規則に違反するメソッドと、規則に適合するメソッドを示します。

 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1060:P/invoke を NativeMethods クラスに移動します。](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400:P/invoke エントリ ポイントが存在する必要があります。](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401:P/invoke を表示することはできません。](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA 2101:P/invoke 文字列引数に対してマーシャ リングを指定します。](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205:Win32 API に相当するマネージドの使用します。](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)