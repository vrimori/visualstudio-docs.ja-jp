---
title: 'Ca 1816: では、Gc が発生します。SuppressFinalize 正しく |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.workload:
- multiple
ms.openlocfilehash: 9d6d65561e9b902202d4fc69d15d200482880cf4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize を正しく呼び出します
|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|カテゴリ|Microsoft です。 使用法|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
  
-   メソッドの実装である<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>呼び出しません<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>です。  
  
-   メソッドの実装ではない<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>呼び出し<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>です。  
  
-   メソッドを呼び出す<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>し、この (Visual Basic で Me) 以外のものを渡します。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>メソッドにより、ユーザーはいつでもはガベージ コレクションの対象になるオブジェクトの前にリソースを解放します。 場合、<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>メソッドが呼び出されると、オブジェクトのリソースを解放します。 これにより、終了処理が不要なにします。 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 呼び出す必要があります<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>ガベージ コレクターがオブジェクトのファイナライザーを呼び出さないようにします。  
  
 派生型にファイナライザーが再実装することがないようにする<xref:System.IDisposable>に呼び出し、ファイナライザーせず unsealed 型は呼び出す必要がありますと<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには。  
  
 メソッドの実装が場合<xref:System.IDisposable.Dispose%2A>、呼び出しを追加して<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>です。  
  
 メソッドの実装ではない場合<xref:System.IDisposable.Dispose%2A>への呼び出しを削除するか<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>または型への移動<xref:System.IDisposable.Dispose%2A>実装します。  
  
 すべての呼び出しを変更する<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>に渡すこの (Visual Basic で Me) です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 使用してを deliberating いる場合のみこの規則による警告は抑制<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>を他のオブジェクトの有効期間を制御します。 実装は、この規則による警告を抑制しないでください<xref:System.IDisposable.Dispose%2A>呼び出しません<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>です。 このような状況で終了処理を非表示に失敗するパフォーマンスの低下、利点がありません。  
  
## <a name="example"></a>例  
 次の例はいないメソッドを正しく呼び出す<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>です。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## <a name="example"></a>例  
 次の例は、メソッドを正しく呼び出す<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>です。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA2215: Dispose メソッドから基本クラスの破棄を呼び出します](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: 破棄できる型ではファイナライザーを宣言します](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## <a name="see-also"></a>関連項目  
 [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)