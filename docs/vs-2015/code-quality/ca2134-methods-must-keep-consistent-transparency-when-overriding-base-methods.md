---
title: '2134 ca: メソッドする必要があります保つ透過性の整合基本メソッドをオーバーライドする場合 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 218114a87b3f81fb4b422852b6d92f952474f668
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844199"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: メソッドは、基本メソッドをオーバーライドしている場合、透過性の整合性を保つ必要がある
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールからの警告を抑制しないでください。 この規則の違反が、ランタイムで発生<xref:System.TypeLoadException>レベル 2 の透過性を使用するアセンブリ。

## <a name="examples"></a>使用例

### <a name="code"></a>コード
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>関連項目
 [透過的セキュリティ コード、レベル 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)



