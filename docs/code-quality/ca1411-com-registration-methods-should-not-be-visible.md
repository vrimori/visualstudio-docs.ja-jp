---
title: "1411: ca COM 登録メソッドはできません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67a4d4124ac1aae99327fdcd757db546cb50adfe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: COM 登録メソッドは参照可能であることはできません
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|カテゴリ|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 マークされているメソッド、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>または<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>属性は、外部から参照可能です。  
  
## <a name="rule-description"></a>規則の説明  
 アセンブリには、コンポーネント オブジェクト モデル (COM) が登録されると、アセンブリで COM から参照できる各種類のレジストリにエントリが追加されます。 マークされたメソッド、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>と<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>属性中に呼び出される、登録および登録解除のプロセスをそれぞれに、これらの型の登録/登録解除に固有であるユーザー コードを実行します。 このコードは、これらのプロセス外呼び出すことはできません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、メソッドのアクセシビリティを変更`private`または`internal`(`Friend`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、規則に違反する 2 つの方法を示します。  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1410: COM 登録メソッドは一致しなければなりません](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [COM へのアセンブリの登録](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (アセンブリ登録ツール)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)