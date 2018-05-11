---
title: 'CA2133: デリゲートは透過性の整合がとれたメソッドにバインドする必要がある'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eee7b4857f91d4d201b79e0814113b36b03fc151
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: デリゲートは透過性の整合がとれたメソッドにバインドする必要がある
|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

> [!NOTE]
>  この警告は、CoreCLR (Silverlight Web アプリケーションに固有である CLR のバージョン) を実行しているコードにのみ適用されます。

## <a name="cause"></a>原因
 マークされているデリゲートをバインドするメソッドでこの警告が発生、<xref:System.Security.SecurityCriticalAttribute>透過的またはでマークされたメソッドに、<xref:System.Security.SecuritySafeCriticalAttribute>です。 この警告は、透過的なデリゲートまたはセーフ クリティカルなデリゲートを、クリティカル メソッドにバインドするメソッドに対しても適用されます。

## <a name="rule-description"></a>規則の説明
 デリゲート型とそのバインド先メソッドには、透過性の整合性がある場合があります。 透過的かつセーフ クリティカルなデリゲート可能性がありますのみメソッドにバインド他の透過的またはセーフ クリティカルです。 同様に、重要なデリゲートは重要なメソッドにのみバインド可能性があります。 これらのバインディング規則をデリゲート経由でメソッドを呼び出すことのできるコードにのみでしたがもメソッドを呼び出した同じ直接ことを確認します。 たとえば、バインディング規則では、透過的なデリゲート経由で直接クリティカルなコードの呼び出しから透過的なコードを防ぐためです。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この警告の違反を修正するには、またはそのバインド先、2 つの透過性は同等のメソッドのデリゲートの透明度を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]