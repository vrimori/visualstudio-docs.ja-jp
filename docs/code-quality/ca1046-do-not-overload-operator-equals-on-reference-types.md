---
title: CA1046:参照型で、演算子 equals をオーバーロードしないでください
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7d3994c827e7d090ead52d0ea6345ba8d79b2a3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018511"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046:参照型で、演算子 equals をオーバーロードしないでください

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたは入れ子になったパブリック参照型は、等値演算子をオーバー ロードします。

## <a name="rule-description"></a>規則の説明
 参照型の場合、等値演算子は既定の実装でほぼ問題がありません。 既定で、2 つの参照が等値と見なされるのは、同じオブジェクトを参照する場合のみです。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を解決するには、等値演算子の実装を削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 参照型は組み込みの値型のように動作する場合は、この規則による警告を抑制するのには安全です。 型のインスタンスで加算または減算を実行する意味場合は、等値演算子を実装し、違反を抑制するのには正しい可能性があります。

## <a name="example"></a>例
 次の例は、2 つの参照を比較するときに、既定の動作を示します。

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>例

次のアプリケーションでは、いくつかの参照を比較します。

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

この例を実行すると、次の出力が生成されます。

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>関連するルール

[CA1013:オーバー ロードで、演算子 equals をオーバー ロードの加算および減算](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>関連項目

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [等値演算子](/dotnet/standard/design-guidelines/equality-operators)