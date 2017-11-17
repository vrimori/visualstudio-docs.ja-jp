---
title: "Ca 2142: 透過的なコード保護されてはならないために LinkDemands を |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d0b9712ec0ed9d5ecd8e76b1ecf208505f07623
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: 透過的コードは、LinkDemand を使用して保護されてはならない
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 透過的なメソッドが必要な<xref:System.Security.Permissions.SecurityAction>またはその他のセキュリティ確認要求します。  
  
## <a name="rule-description"></a>規則の説明  
 この規則は、アクセスするために LinkDemands を要求する透過的メソッドに対して適用されます。 透過的セキュリティ コードでは、操作のセキュリティ検証を行うことができないため、アクセス許可を要求できません。 透過的メソッドはセキュリティに中立的になっている、ので、行うことができません、セキュリティ上の決定します。 さらに、セキュリティ上の決定を行う、セーフ クリティカル コードはこのような意志決定を行いましたが以前に透過的なコードに依存しない必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正する透過的メソッドに対して、リンク確認要求を削除するかを使用してメソッドをマーク<xref:System.Security.SecuritySafeCriticalAttribute>セキュリティ確認要求など、セキュリティを実行している場合、属性を確認します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例で、規則は、メソッドのメソッドは透過的であり、LinkDemand でマークされているため<xref:System.Security.PermissionSet>を格納している、<xref:System.Security.Permissions.SecurityAction>です。  
  
 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 この規則による警告は抑制しないでください。