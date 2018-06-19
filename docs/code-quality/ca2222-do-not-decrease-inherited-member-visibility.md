---
title: 'CA2222: 継承されたメンバーの参照範囲を縮小しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d91425ecb5be33d23b1d7775caac04c616c89a9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921245"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: 継承されたメンバーの参照範囲を縮小しません
|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 封印されていない型のプライベート メソッドには、基本型で宣言されたパブリック メソッドと同じである署名があります。 プライベート メソッドは final ではないです。

## <a name="rule-description"></a>規則の説明
 継承メンバーのアクセス修飾子は変更しないでください。 継承メンバーをプライベートに変更しても、呼び出し元はメソッドの基本クラスの実装にアクセスできます。 メンバーをプライベートには、種類が封印されていない場合は、継承する型の実装を呼び出す最後パブリック メソッドの継承階層にします。 アクセス修飾子を変更する必要があります、メソッドは、最終的な設定する必要がありますか、またはメソッドがオーバーライドされないようにするその型をシールする必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、プライベート以外へのアクセスを変更します。 また、使用するプログラミング言語でサポートされる場合、行うことができますメソッド最終的なです。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例は、この規則に違反する型を示しています。

 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]