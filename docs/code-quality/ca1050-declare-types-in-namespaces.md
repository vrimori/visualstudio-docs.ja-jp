---
title: CA1050:名前空間で型を宣言します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 97cc36e7b454484f4fcdfb3d3be499e48af9c407
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018840"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050:名前空間で型を宣言します

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型は、名前付きの名前空間のスコープ外に定義されます。

## <a name="rule-description"></a>規則の説明
 名前空間名の競合を回避して、オブジェクト階層内の関連する種類を整理する方法として、型が宣言されます。 任意の名前付き名前空間の外部にある型は、コードでは参照できない、グローバル名前空間でです。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、名前空間の型を配置します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 このルールから警告を抑制することはありませんが、アセンブリは他のアセンブリと共に使用しない場合、これに安全です。

## <a name="example"></a>例
 次の例では、正しくない、名前空間の外部宣言の型を持つライブラリと名前空間で宣言されている同じ名前を持つ型を示します。

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>例
 次のアプリケーションでは、既に定義されているライブラリを使用します。 名前空間の外部で宣言された型が作成されるときに注意してください。 名前`Test`名前空間で修飾されていません。 またにアクセスする、`Test`入力`Goodspace`、名前空間名が必要です。

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]