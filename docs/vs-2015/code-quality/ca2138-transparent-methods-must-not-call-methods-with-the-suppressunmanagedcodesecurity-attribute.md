---
title: '2138: 透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出してする必要がありますされません |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 127f2cb0a6aec99b858c75c43a2ee6cbbb2c6e94
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "47593247"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: 透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出してはならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2138: 透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出す必要がありますいない](https://docs.microsoft.com/visualstudio/code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute)します。

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 透過的セキュリティ メソッドでマークされているメソッドを呼び出し、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性。

## <a name="rule-description"></a>規則の説明
 この規則を使用して、ネイティブ コードを直接呼び出すすべての透過的メソッドに対して適用されます、P/invoke を使用して (プラットフォーム呼び出し) を呼び出します。 マークされている P/invoke と COM の相互運用メソッド、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>呼び出し元のメソッドに対して行われている LinkDemand で結果の属性します。 セキュリティ透過的なコードでは、LinkDemands を満たすことはできません、ため、コードも呼び出すことはできません、SuppressUnmanagedCodeSecurity 属性でマークされているメソッドまたは SuppressUnmanagedCodeSecurity 属性でマークされたクラスのメソッド。 メソッドは失敗するか、要求は、フル アクセス要求に変換されます。

 この規則に違反が発生、<xref:System.MethodAccessException>レベル 2 のセキュリティ透過性モデルとの完全な要求で<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>レベル 1 の透過性モデルでします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、削除、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性し、メソッド、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]



