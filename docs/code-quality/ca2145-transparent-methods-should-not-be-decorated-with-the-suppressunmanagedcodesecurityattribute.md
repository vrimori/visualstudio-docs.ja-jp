---
title: "Ca 2145: 透過的メソッド必要がありますいない SuppressUnmanagedCodeSecurityAttribute で修飾ならない、|Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 23cf7599e4d699a6be42bae55381ffb31ce1556e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: 透過的メソッドを SuppressUnmanagedCodeSecurityAttribute で修飾してはならない
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 透過的メソッドでマークされているメソッド、<xref:System.Security.SecuritySafeCriticalAttribute>メソッド、またはメソッドが含まれる型がでマークされた、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性。  
  
## <a name="rule-description"></a>規則の説明  
 メソッドで修飾して、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>属性がある、暗黙的な LinkDemand を呼び出しているメソッドに配置します。 この LinkDemand では、呼び出し元のコードがセキュリティ クリティカルなコードである必要があります。 Suppressunmanagedcodesecurity を使用するメソッドに、<xref:System.Security.SecurityCriticalAttribute>属性は、メソッドの呼び出し元に対してこの要件をより明確です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、メソッドをマークまたは型が、<xref:System.Security.SecurityCriticalAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### <a name="comments"></a>コメント