---
title: CA1048:シールド型の仮想メンバーを宣言しません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 026a1b2cbcd75bd2f39cc6f169b0a1a2feddb258
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872883"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048:シールド型の仮想メンバーを宣言しません

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型は封印されており、両方であるメソッドを宣言`virtual`(`Overridable` Visual basic) と最終されません。 このルールは、デリゲートの型は、このパターンに従う必要がありますの違反を報告しません。

## <a name="rule-description"></a>規則の説明
 型でメソッドを仮想と宣言するのは、継承する型が仮想メソッドの実装をオーバーライドできるようにするためです。 定義上には、意味のない、シールされた型の仮想メソッドを作成、シールされた型から継承することはできません。

 Visual Basic および c# コンパイラでは、この規則に違反する型は使用できません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、非仮想メソッドを作成または、型が継承できるようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。 メンテナンスの問題が発生することができ、すべての特典を提供しない型の現在の状態のままになります。

## <a name="example"></a>例
 次の例では、この規則に違反する型を示します。

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]