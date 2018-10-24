---
title: 'Ca 1004: ジェネリック メソッドは型パラメーターを指定する必要があります |Microsoft Docs'
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
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1e47276ad5be70308dc4c6e249204a65ef9f08b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880209"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照のジェネリック メソッドのパラメーター シグネチャに、メソッドのすべての型パラメーターに対応する型が含まれていません。

## <a name="rule-description"></a>規則の説明
 型引数を明示的に指定するのではなく、メソッドに渡す引数の型によってジェネリック メソッドの型引数を決定する方法が推論されます。 推論を有効にするには、ジェネリック メソッドのパラメーター シグネチャに、そのメソッドの型パラメーターと同じ型のパラメーターが含まれている必要があります。 この場合、型引数を指定する必要がなくなります。 すべての型パラメーターの推論を使用する場合は、ジェネリックと非ジェネリック インスタンス メソッドの呼び出しの構文は同じです。 これには、ジェネリック メソッドの使いやすさが簡略化します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、パラメーター シグネチャが、メソッドの型パラメーターごとに同じ型が含まれるようにデザインを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 ジェネリックでは簡単に理解して使用する構文を提供するには、習得に必要なされ、新しいライブラリの導入速度を向上する時間が短縮されます。

## <a name="example"></a>例
 次の例では、2 つのジェネリック メソッドを呼び出すための構文を示します。 型引数`InferredTypeArgument`が推論し、型引数`NotInferredTypeArgument`明示的に指定する必要があります。

 [!code-csharp[FxCop.Design.Inference#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/cs/FxCop.Design.Inference.cs#1)]
 [!code-vb[FxCop.Design.Inference#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/vb/FxCop.Design.Inference.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)