---
title: 'CA2134: メソッドは、基本メソッドをオーバーライドしている場合、透過性の整合性を保つ必要がある'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f56b81f3f3ce16f509f29791e28992402c222f9
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45552004"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: メソッドは、基本メソッドをオーバーライドしている場合、透過性の整合性を保つ必要がある
|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 マークされたメソッドと、この規則が適用されます、<xref:System.Security.SecurityCriticalAttribute>を透明またはでマークされたメソッドをオーバーライドして、<xref:System.Security.SecuritySafeCriticalAttribute>します。 このルールは、ときに透明またはでマークされたメソッドにも発生、<xref:System.Security.SecuritySafeCriticalAttribute>でマークされているメソッドをオーバーライドして、<xref:System.Security.SecurityCriticalAttribute>します。

 この規則は、仮想メソッドをオーバーライドする場合やインターフェイスを実装する場合に適用されます。

## <a name="rule-description"></a>規則の説明
 このルールは、継承チェーンをさらにメソッドのセキュリティのアクセシビリティの変更の試行に対して適用されます。 たとえば場合は、基底クラス仮想メソッドは、transparent またはセーフ クリティカルには、派生クラスする必要がありますオーバーライド透明またはセーフ クリティカル メソッドを使用。 逆に、仮想がセキュリティ クリティカルな場合、派生クラスする必要がありますをセキュリティの重要なメソッドを使用してオーバーライドします。 インターフェイス メソッドを実装するため、同じ規則が適用されます。

 透過性の計算には動的な型情報がないように、コードが JIT の代わりに、実行時にコンパイルされた場合、透過性規則が適用されます。 そのため、透過性の計算の結果は、動的な型に関係なく、JIT でコンパイルされた静的な型からのみ判断できる必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、仮想メソッドをオーバーライドするか、仮想の透明度またはインターフェイスのメソッドと一致するインターフェイスを実装するメソッドの透明度を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 このルールからの警告を抑制しないでください。 この規則の違反が、ランタイムで発生<xref:System.TypeLoadException>レベル 2 の透過性を使用するアセンブリ。

## <a name="examples"></a>使用例

### <a name="code"></a>コード
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>関連項目
 [透過的セキュリティ コード、レベル 2](/dotnet/framework/misc/security-transparent-code-level-2)