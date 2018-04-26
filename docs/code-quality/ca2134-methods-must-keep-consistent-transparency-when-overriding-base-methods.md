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
ms.openlocfilehash: 6c02ce23c341df377bc16b56cdd85769acf5582c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: メソッドは、基本メソッドをオーバーライドしている場合、透過性の整合性を保つ必要がある
|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 この規則はメソッドが付いている場合、<xref:System.Security.SecurityCriticalAttribute>は透過的またはでマークされているメソッドをオーバーライドして、<xref:System.Security.SecuritySafeCriticalAttribute>です。 規則は、ときに、透過的またはでマークされたメソッドを<xref:System.Security.SecuritySafeCriticalAttribute>でマークされているメソッドをオーバーライドして、<xref:System.Security.SecurityCriticalAttribute>です。

 この規則は、仮想メソッドをオーバーライドする場合やインターフェイスを実装する場合に適用されます。

## <a name="rule-description"></a>規則の説明
 このルールは、継承チェーンをさらにメソッドのセキュリティ アクセシビリティを変更しようとすると発生します。 たとえば、基底クラス仮想メソッドが透過的またはセーフ クリティカルである場合、し、派生クラスは、する必要がありますメソッドをオーバーライド透過的またはセーフ クリティカルなメソッドを使用しています。 逆に、仮想がセキュリティ クリティカルな場合、派生クラス必要がありますをセキュリティ クリティカルなメソッドを使用してオーバーライドします。 インターフェイス メソッドを実装するため、同じ規則が適用されます。

 透過性の計算に動的な型情報が必要があるないように、コードが JIT の代わりに、実行時にコンパイルされたとき、透過性規則が適用されます。 したがって、透過性の計算の結果は、動的な型に関係なく、JIT でコンパイルされた静的な型からのみを特定することができる必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するが仮想メソッドをオーバーライドするか、仮想の透明度またはインターフェイスのメソッドに一致するインターフェイスを実装するメソッドの透明度を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 ランタイムにこの規則の違反が発生<xref:System.TypeLoadException>レベル 2 の透過性を使用するアセンブリ。

## <a name="examples"></a>使用例

### <a name="code"></a>コード
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>関連項目
 [透過的セキュリティ コード、レベル 2](/dotnet/framework/misc/security-transparent-code-level-2)