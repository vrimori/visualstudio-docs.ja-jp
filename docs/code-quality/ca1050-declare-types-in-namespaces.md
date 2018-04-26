---
title: 'CA1050: 名前空間で型を宣言します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf38fde258a033fd4050e93d3ad69015f365dc60
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: 名前空間で型を宣言します
|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 名前付きの名前空間のスコープ外部パブリックまたはプロテクト型で定義されています。

## <a name="rule-description"></a>規則の説明
 名前空間名の競合を回避して、オブジェクト階層内の関連する型を整理する手段として、型が宣言されます。 コードでは参照できないグローバル名前空間にある、名前付きの名前空間の外部型です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、名前空間で型を配置します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制することはありませんが、これを行うアセンブリは他のアセンブリと共に使用しない場合も安全です。

## <a name="example"></a>例
 次の例では、名前空間の外部正しく宣言された型を持つライブラリと名前空間で宣言されている同じ名前を持つ型を示します。

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>例
 次のアプリケーションでは、以前に定義されているライブラリを使用します。 名前空間の外部で宣言されている型を作成するときに注意してください。 名前`Test`名前空間で修飾されていません。 なおへのアクセス、`Test`入力`Goodspace`、名前空間の名前が必要です。

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]