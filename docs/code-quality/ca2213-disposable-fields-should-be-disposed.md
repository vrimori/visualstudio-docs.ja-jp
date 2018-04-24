---
title: 'CA2213: 破棄可能なフィールドは破棄されなければなりません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 914f4f14742bcac3de94a25a547767b714058b7c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: 破棄可能なフィールドは破棄されなければなりません
|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 実装する型<xref:System.IDisposable?displayProperty=fullName>も実装する型のフィールドを宣言<xref:System.IDisposable>です。 <xref:System.IDisposable.Dispose%2A> 、フィールドのメソッドが呼び出されていない、<xref:System.IDisposable.Dispose%2A>宣言型のメソッドです。

## <a name="rule-description"></a>規則の説明
 型はすべて、アンマネージ リソースの破棄を担当します。これを実装することによって実現<xref:System.IDisposable>です。 このルールは、破棄可能な型かどうかをチェック`T`フィールドを宣言して`F`破棄可能な型のインスタンスである`FT`です。 各フィールドの`F`、ルールへの呼び出しを特定しようとしています。`FT.Dispose`です。 ルールによって呼び出されるメソッドを検索する`T.Dispose`、および下位のレベル (によって呼び出されるメソッドによって呼び出されるメソッド`FT.Dispose`)。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、呼び出す<xref:System.IDisposable.Dispose%2A>を実装する型のフィールドの <xref:System.IDisposable>の割り当てを担当する場合、そのフィールドによって保持されているアンマネージ リソースを解放します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 フィールドによって保持されているリソースを解放するため、担当するがない場合、または場合に、この規則による警告を抑制するのには安全では呼び出し<xref:System.IDisposable.Dispose%2A>ルール チェックよりも深い呼び出しレベルで発生します。

## <a name="example"></a>例
 次の例は、型を示しています。`TypeA`を実装する<xref:System.IDisposable>(`FT` previosu ディスカッション内)。

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

## <a name="example"></a>例
 次の例は、型を示しています。`TypeB`フィールドを宣言することでこの規則に違反する`aFieldOfADisposableType`(`F`上記の説明で)、破棄可能な型として (`TypeA`) を呼び出さない<xref:System.IDisposable.Dispose%2A>フィールドにします。 `TypeB` 対応する`T`で、前に説明します。

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>関連項目
 <xref:System.IDisposable?displayProperty=fullName> [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)