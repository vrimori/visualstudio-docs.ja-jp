---
title: "Ca 2136: メンバーのない透過性注釈の競合 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 350504d6e49351e96aa1c986ddf08893dc490d69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: メンバーには、透過性注釈の競合があってはならない
|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 この規則は、型のメンバーが付いている場合、<xref:System.Security>をさまざまな透過性は、メンバーのコンテナーのセキュリティ属性を持つセキュリティ属性。  
  
## <a name="rule-description"></a>規則の説明  
 透過性属性は、大きいスコープのコード要素から小さいスコープの要素に適用されます。 大きいスコープのコード要素の透過性属性は、最初の要素に含まれているコード要素の透過性属性よりも優先されます。 マークされているクラスなど、<xref:System.Security.SecurityCriticalAttribute>属性でマークされているメソッドを含めることはできません、<xref:System.Security.SecuritySafeCriticalAttribute>属性。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この違反を修正するを下位のスコープを持つコード要素からセキュリティ属性を削除またはコンテナーのコード要素と同じにするには、その属性を変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、メソッドが付いて、<xref:System.Security.SecuritySafeCriticalAttribute>属性でマークされているクラスのメンバーである、<xref:System.Security.SecurityCriticalAttribute>属性。 セキュリティ セーフである属性を削除する必要があります。  
  
 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]