---
title: 'Ca 2220: ファイナライザーは基本クラスのファイナライザーを呼び出す必要があります |Microsoft Docs'
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
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e00419ed7f6b4d388b9fb28f56d85990a4257b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862711"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: ファイナライザーは基本クラスのファイナライザーを呼び出さなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 共通言語ランタイムを対象とする一部のコンパイラでは、Microsoft intermediate language (MSIL) に、基本型のファイナライザーの呼び出しを挿入します。 この規則による警告が報告された場合、コンパイラは、呼び出しを挿入できませんし、コードに追加する必要があります。

## <a name="example"></a>例
 次の Visual Basic の例は、型を示しています。`TypeB`を正しく呼び出す、 <xref:System.Object.Finalize%2A> 、基本クラス メソッド。

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>関連項目
 [Dispose パターン](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



