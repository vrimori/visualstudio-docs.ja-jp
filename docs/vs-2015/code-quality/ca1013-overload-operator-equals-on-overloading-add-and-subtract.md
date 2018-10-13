---
title: '1013: ca オーバー ロードで、演算子 equals をオーバー ロードを追加および減算 |Microsoft Docs'
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
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ad1213ad0f24ef3e98a7311719fbff4dc7667a20
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191985"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: オーバーロードする加算および減算で、演算子 equals をオーバーロードします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 パブリック型またはプロテクト型で、等値演算子を実装しないまま、加算演算子または減算演算子を実装しています。

## <a name="rule-description"></a>規則の説明
 返すには、等しいかどうかを定義する型のインスタンスは、加算や減算などの操作を使用して組み合わせることができます、ほぼ常にする必要があります`true`同じの構成値を持つ 2 つのインスタンス。

 オーバー ロードされた等値演算子の実装では、既定の等値演算子を使用できません。 こうと、スタック オーバーフローが発生します。 等値演算子を実装するには、実装で、Object.Equals メソッドを使用します。 次の例を参照してください。

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、加算と減算演算子と数学的に矛盾があるように、等値演算子を実装します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 等値演算子の既定の実装の種類の正しい動作を提供するときに、この規則による警告を非表示にも安全です。

## <a name="example"></a>例
 次の例では、型を定義する (`BadAddableType`) をこの規則に違反します。 この型は、テスト、同じフィールド値を持つ 2 つのインスタンスに等値演算子を実装する必要があります`true`等しいかどうか。 型`GoodAddableType`修正の実装を示しています。 この型も非等値演算子を実装し、上書きことに注意してください<xref:System.Object.Equals%2A>を他のルールを満たすためにします。 完全な実装は実装も<xref:System.Object.GetHashCode%2A>します。

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>例
 次の例は、等値演算子の既定値と正しい動作を説明するためには、このトピックで以前に定義された型のインスタンスを使用して、等しいかどうかテストします。

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **無効な型: {2,2} {2,2}が等しいか?いいえ**
**適切な型: {3,3} {3,3}が等しいか?[はい]**
**適切な型: {3,3} {3,3}は、= = でしょうか。 [はい]**
**無効な型: {2,2} {9,9}が等しいか?いいえ**
**適切な型: {3,3} {9,9}は、= = でしょうか。 違います**
## <a name="see-also"></a>関連項目
 [等値演算子](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



