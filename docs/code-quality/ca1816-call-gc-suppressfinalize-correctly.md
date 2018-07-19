---
title: 'CA1816: GC.SuppressFinalize を正しく呼び出します'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5c874aac5d84d45159ef7d169ab2749269fa0905
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174232"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize を正しく呼び出します

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|カテゴリ|Microsoft。 使用法|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

この規則の違反は、によって発生することができます。

- メソッドの実装である<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>呼び出さないと<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>します。

- メソッドの実装ではない<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>と呼び出し<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>します。

- メソッドを呼び出す<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>以外の何か渡します[this (c#)](/dotnet/csharp/language-reference/keywords/this)または[Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)します。

## <a name="rule-description"></a>規則の説明

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>メソッドにより、ユーザーはガベージ コレクションの対象になるオブジェクトの前に、いつでもリソースを解放します。 場合、<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>メソッドが呼び出されると、オブジェクトのリソースを解放します。 これにより、終了処理は不要です。 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 呼び出す必要があります<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>ガベージ コレクターがオブジェクトのファイナライザーを呼び出さないようにします。

ファイナライザーで派生型の再実装することを防ぐために<xref:System.IDisposable>を付けますについては、封印されていない型のファイナライザーなしは呼び出す必要がありますと<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには。

- メソッドの実装が場合<xref:System.IDisposable.Dispose%2A>、呼び出しを追加して<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>します。

- メソッドの実装でない場合<xref:System.IDisposable.Dispose%2A>への呼び出しを削除するか<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>に型の移動または<xref:System.IDisposable.Dispose%2A>実装します。

- すべての呼び出しを変更する<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>渡す[this (c#)](/dotnet/csharp/language-reference/keywords/this)または[Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

意図的に使用する場合にのみ、この規則による警告を抑制<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>他のオブジェクトの有効期間を制御します。 実装の場合、この規則による警告を抑制しない<xref:System.IDisposable.Dispose%2A>呼び出さない<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>します。 このような状況で失敗をファイナライズを抑制するのにはパフォーマンスが低下し、メリットは提供されません。

## <a name="example-that-violates-ca1816"></a>Ca 1816 に違反する例

このコードを呼び出す方法を示しています。 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>、に合格しなかったが、 [this (c#)](/dotnet/csharp/language-reference/keywords/this)または[Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)します。 その結果、このコードには、ca 1816 ルールに違反しています。

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Ca 1816 に適合する例

この例では、メソッドを正しく呼び出し<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>を渡すことによって[this (c#)](/dotnet/csharp/language-reference/keywords/this)または[Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)します。

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>関連するルール

- [CA2215: Dispose メソッドから基本クラスの破棄を呼び出します](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: 破棄できる型ではファイナライザーを宣言します](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>関連項目

- [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)