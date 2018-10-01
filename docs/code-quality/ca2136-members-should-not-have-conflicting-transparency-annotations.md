---
title: 'CA2136: メンバーには、透過性注釈の競合があってはならない'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3af665f3a0f59cb1dd8c8c8ee581fc37f9da7e78
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550922"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: メンバーには、透過性注釈の競合があってはならない
|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型のメンバーが付いたときに、この規則が適用されます、<xref:System.Security>セキュリティ属性を持つメンバーのコンテナーのセキュリティ属性は異なる、透過性。

## <a name="rule-description"></a>規則の説明
 透過性属性は、大きいスコープのコード要素から小さいスコープの要素に適用されます。 大きいスコープのコード要素の透過性属性は、最初の要素に含まれているコード要素の透過性属性よりも優先されます。 マークされたクラスなど、<xref:System.Security.SecurityCriticalAttribute>属性でマークされているメソッドを含めることはできません、<xref:System.Security.SecuritySafeCriticalAttribute>属性。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この違反を修正するには、下位のスコープを持つコード要素からセキュリティ属性を削除または含まれているコード要素と同じにするには、その属性を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 このルールからの警告を抑制しないでください。

## <a name="example"></a>例
 次の例では、メソッドが付いて、<xref:System.Security.SecuritySafeCriticalAttribute>と属性でマークされているクラスのメンバーである、<xref:System.Security.SecurityCriticalAttribute>属性。 セキュリティ セーフ属性を削除する必要があります。

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]