---
title: CA1411:COM 登録メソッドは参照可能であることはできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: da83faf5c2ca1a60d4f931cd498caf3717c21e2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926997"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411:COM 登録メソッドは参照可能であることはできません

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

マークされているメソッド、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>または<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>属性は、外部から参照します。

## <a name="rule-description"></a>規則の説明
 アセンブリ コンポーネント オブジェクト モデル (COM) で登録されると、アセンブリで COM から参照できる各型のレジストリにエントリが追加されます。 マークされているメソッド、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>と<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>属性中に呼び出される登録および登録解除プロセスでは、それぞれに、これらの型の登録または登録解除に固有のユーザー コードを実行します。 このコードは、これらのプロセス外呼び出されませんする必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、メソッドのアクセシビリティを変更`private`または`internal`(`Friend`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、ルールに違反している 2 つの方法を示します。

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA 1410:COM 登録メソッドは一致する必要があります。](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [COM へのアセンブリの登録](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (アセンブリ登録ツール)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)