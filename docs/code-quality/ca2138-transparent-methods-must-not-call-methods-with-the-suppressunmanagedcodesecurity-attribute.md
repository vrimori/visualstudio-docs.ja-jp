---
title: CA2138:透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出してはならない
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 036eabaca00c8a30a3dce70987d0978998ed8e25
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904852"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138:透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出してはならない

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透過的セキュリティ メソッドでマークされているメソッドを呼び出し、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性。

## <a name="rule-description"></a>規則の説明
 このルールは、P/invoke を使用して、たとえば、ネイティブ コードを直接呼び出すすべての透過的メソッドに対して適用されます (プラットフォーム呼び出し) を呼び出します。 マークされている P/invoke と COM の相互運用メソッド、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>呼び出し元のメソッドに対して行われている LinkDemand で結果の属性します。 セキュリティ透過的なコードでは、LinkDemands を満たすことはできません、ため、コードも呼び出すことはできません、SuppressUnmanagedCodeSecurity 属性でマークされているメソッドまたは SuppressUnmanagedCodeSecurity 属性でマークされたクラスのメソッド。 メソッドは失敗するか、要求は、フル アクセス要求に変換されます。

 この規則に違反が発生、<xref:System.MethodAccessException>レベル 2 のセキュリティ透過性モデルとの完全な要求で<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>レベル 1 の透過性モデルでします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、削除、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性し、メソッド、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]