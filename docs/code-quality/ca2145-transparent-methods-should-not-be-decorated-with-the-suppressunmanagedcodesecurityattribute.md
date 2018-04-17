---
title: 'Ca 2145: 透過的メソッド必要がありますいない SuppressUnmanagedCodeSecurityAttribute で修飾ならない、|Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: e0571656905642b9f8bdd12a93a8aa83256124f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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