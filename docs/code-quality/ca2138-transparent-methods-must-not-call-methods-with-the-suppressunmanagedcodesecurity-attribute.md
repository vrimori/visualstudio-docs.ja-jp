---
title: "CA2138: 透過的メソッドを呼び出してはならない、SuppressUnmanagedCodeSecurity 属性を持つメソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf17c69673649ac1f3af64bafcb718e8c84eb213
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: 透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出してはならない
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 透過的セキュリティ メソッドでマークされているメソッドを呼び出して、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性。  
  
## <a name="rule-description"></a>規則の説明  
 この規則を使用して、ネイティブ コードを直接呼び出すすべての透過的メソッドに対して適用、P/invoke を使用して (プラットフォーム呼び出し) を呼び出します。 P/invoke メソッドと COM 相互運用機能メソッドでマークされている、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>呼び出し元のメソッドに対して実行されている LinkDemand で結果の属性です。 セキュリティ透過的なコードは、Linkdemand を満たすことができない、ため、コードも呼び出すことはできません、SuppressUnmanagedCodeSecurity 属性でマークされたメソッドまたは SuppressUnmanagedCodeSecurity 属性でマークされているクラスのメソッドです。 メソッドが失敗すると、または要求は、フル アクセス要求に変換されます。  
  
 この規則の違反が発生する可能性、<xref:System.MethodAccessException>第 2 レベルのセキュリティ透過性モデルとの完全な要求で<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>レベル 1 の透過性モデルでします。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を解決するには、削除、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性を使用してメソッドをマーク、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]