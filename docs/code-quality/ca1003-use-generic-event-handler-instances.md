---
title: CA1003:汎用イベント ハンドラーのインスタンスを使用します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 26630aa008e944f0af3fdcc66a16dc4c08bd4e8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887334"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003:汎用イベント ハンドラーのインスタンスを使用します

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型が void を返す、2 つのパラメーター (1 つはオブジェクトと、2 つ目は EventArgs に割り当て可能な型) と包含アセンブリの対象を含むシグネチャを持つデリゲートを含む[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]します。

## <a name="rule-description"></a>規則の説明
 前に[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]、イベント ハンドラーにカスタム情報を渡すために、新しいデリゲートを宣言から派生したクラスを指定する必要がある、<xref:System.EventArgs?displayProperty=fullName>クラス。 場合は true。 これは不要になった[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]、導入された、<xref:System.EventHandler%601?displayProperty=fullName>を委任します。 この汎用デリゲートにより、任意のクラスから派生した<xref:System.EventArgs>イベント ハンドラーと共に使用します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、デリゲートを削除しを使用してその使用を置き換える、<xref:System.EventHandler%601?displayProperty=fullName>を委任します。 デリゲートがによって自動生成された場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]コンパイラを使用するイベントの宣言の構文を変更、<xref:System.EventHandler%601?displayProperty=fullName>を委任します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、規則に違反するデリゲートを示します。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]例では、コメント、ルールを満たすために例を変更する方法を示しています。 例では、c# の例で、変更されたコードが表示されるに従います。

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>例
 次の例では、デリゲート宣言を削除で使用し、ルールを満たす前の例から、`ClassThatRaisesEvent`と`ClassThatHandlesEvent`メソッドを使用して、<xref:System.EventHandler%601?displayProperty=fullName>を委任します。

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1005:ジェネリック型で過剰なパラメーターを回避します。](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA 1010:コレクションは、ジェネリック インターフェイスを実装する必要があります。](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA 1000:ジェネリック型で静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA 1002:ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA 1006:ジェネリック型メンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA 1004:ジェネリック メソッドは、型パラメーターを指定する必要があります。](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA 1007:適切な場所にジェネリックを使用します。](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>関連項目

- [ジェネリック](/dotnet/csharp/programming-guide/generics/index)