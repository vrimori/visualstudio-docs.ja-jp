---
title: CA2131:セキュリティ上重要な型は型等価性に参加してはならない
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f91f5be2aad41006dacab059db27e9609a4f84f7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913030"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131:セキュリティ上重要な型は型等価性に参加してはならない

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型が型の等価性と、型自体に参加するか、メンバーまたは型のフィールドが付いて、<xref:System.Security.SecurityCriticalAttribute>属性。

## <a name="rule-description"></a>規則の説明
 この規則は、すべての重要な型、または型の等価性に関与する重要なメソッドあるいはフィールドが定義されたすべての型に対して適用されます。 読み込みが失敗し、CLR では、このような型を検出すると、<xref:System.TypeLoadException>実行時にします。 通常は、tlbimp やコンパイラによって型の等価性を実装するのではなく、ユーザーが手動で実装した場合に、この規則が適用されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、SecurityCritical 属性を削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、インターフェイス、メソッド、および起動するには、このルールを原因となるフィールドを示します。

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>関連項目
 [透過的セキュリティ コード、レベル 2](/dotnet/framework/misc/security-transparent-code-level-2)