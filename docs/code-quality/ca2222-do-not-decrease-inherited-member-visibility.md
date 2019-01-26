---
title: CA2222:継承されたメンバーの参照範囲を縮小しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bdae21ec1a95cdc12cb6511a39f45e610e09b329
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031787"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222:継承されたメンバーの参照範囲を縮小しません

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

封印されていない型のプライベート メソッドには、基本データ型で宣言されたパブリック メソッドと同じである署名があります。 プライベート メソッドは、最終版ではありません。

## <a name="rule-description"></a>規則の説明

継承されたメンバーのアクセス修飾子を変更しないでください。 継承メンバーをプライベートに変更しても、呼び出し元はメソッドの基本クラスの実装にアクセスできます。 メンバーがプライベートにする型が封印されていない場合は、継承する型と、メソッドの最後のパブリックの実装が継承階層で呼び出すことができます。 アクセス修飾子を変更する必要があります、メソッドは、最終的なマークする必要がありますか、またはメソッドがオーバーライドされることを防ぐためにその型をシールする必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を解決するには、プライベート以外へのアクセスを変更します。 または、使用するプログラミング言語がサポートする場合行うことができます、メソッド最終的です。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。

## <a name="example"></a>例

次の例では、この規則に違反する型を示します。

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]