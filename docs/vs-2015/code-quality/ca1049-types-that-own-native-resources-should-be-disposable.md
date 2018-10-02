---
title: 'Ca 1049: ネイティブ リソースを所有する型は、破棄可能でなければなりません。Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a3a9e2bb8030fe5273e70da03e6df14bb9dd5607
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589704"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: ネイティブ リソースを所有する型は、破棄可能でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1049: ネイティブ リソースを破棄する必要がありますを所有する型](https://docs.microsoft.com/visualstudio/code-quality/ca1049-types-that-own-native-resources-should-be-disposable)します。

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型参照を<xref:System.IntPtr?displayProperty=fullName>フィールド、<xref:System.UIntPtr?displayProperty=fullName>フィールド、または<xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>フィールドしますが、実装されません<xref:System.IDisposable?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 このルールは、仮定<xref:System.IntPtr>、 <xref:System.UIntPtr>、および<xref:System.Runtime.InteropServices.HandleRef>フィールドに格納されているアンマネージ リソースへのポインター。 アンマネージ リソースを割り当てる型を実装する必要があります<xref:System.IDisposable>呼び出し元をオンデマンドでリソースを解放し、リソースを保持するオブジェクトの有効期間を短縮できるようにします。

 アンマネージ リソースをクリーンアップする推奨デザイン パターンは、暗黙的なとを使用してこれらのリソースを解放するための明示的な方法を提供する、<xref:System.Object.Finalize%2A?displayProperty=fullName>メソッドと<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>メソッドでは、それぞれします。 ガベージ コレクター、<xref:System.Object.Finalize%2A>に到達可能で不要になったオブジェクトを決定したら、ある時点で、オブジェクトのメソッド。 後<xref:System.Object.Finalize%2A>が呼び出されると、追加のオブジェクトを解放するガベージ コレクションが必要です。 <xref:System.IDisposable.Dispose%2A>メソッドが明示的に要求時、ガベージ コレクターの場合、リソースがリリースされるよりも前にリソースを解放する呼び出し元を使用します。 非管理対象のリソースをクリーンアップした後<xref:System.IDisposable.Dispose%2A>呼び出す必要があります、<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>ガベージ コレクターに通知されるようにするメソッド<xref:System.Object.Finalize%2A>されなく; 呼び出す必要がありますとガベージ コレクションの必要はなくなり、短縮、オブジェクトの有効期間。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、実装<xref:System.IDisposable>します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 型がアンマネージ リソースを参照していない場合、この規則による警告を抑制するのには安全です。 ため、この規則による警告を抑制しないでくださいそれ以外の場合、実装<xref:System.IDisposable>アンマネージ リソースを利用できない、または過少になりますが発生することができます。

## <a name="example"></a>例
 次の例では、実装する型<xref:System.IDisposable>アンマネージ リソースをクリーンアップします。

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA2115: ネイティブ リソースを使用しているときには GC.KeepAlive を呼び出します](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize を正しく呼び出します](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: 破棄できる型ではファイナライザーを宣言します](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: 破棄可能なフィールドを所有する型は、破棄可能でなければなりません](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>関連項目
  [Dispose パターン](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



