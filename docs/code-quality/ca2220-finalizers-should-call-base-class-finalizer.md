---
title: 'CA2220: ファイナライザーは基本クラスのファイナライザーを呼び出さなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c814324ac21017acf6a0182f7807b0a0878c8aca
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551208"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: ファイナライザーは基本クラスのファイナライザーを呼び出さなければなりません

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

オーバーライドする型<xref:System.Object.Finalize%2A?displayProperty=fullName>呼び出しません、<xref:System.Object.Finalize%2A>基本クラス メソッド。

## <a name="rule-description"></a>規則の説明

終了処理は、継承の階層構造を使用して反映する必要があります。 これを確実に型が基本クラスを呼び出す必要があります<xref:System.Object.Finalize%2A>メソッド独自内から<xref:System.Object.Finalize%2A>メソッド。 C# コンパイラでは、基本クラスのファイナライザーの呼び出しが自動的に追加します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、呼び出す基本型の<xref:System.Object.Finalize%2A>からメソッド、<xref:System.Object.Finalize%2A>メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。 共通言語ランタイムを対象とする一部のコンパイラでは、Microsoft intermediate language (MSIL) に、基本型のファイナライザーの呼び出しを挿入します。 この規則による警告が報告された場合、コンパイラは、呼び出しを挿入できませんし、コードに追加する必要があります。

## <a name="example"></a>例

次の Visual Basic の例は、型を示しています。`TypeB`を正しく呼び出す、 <xref:System.Object.Finalize%2A> 、基本クラス メソッド。

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>関連項目

- [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)