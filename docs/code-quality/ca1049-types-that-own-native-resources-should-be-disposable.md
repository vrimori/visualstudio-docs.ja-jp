---
title: 'CA1049: ネイティブ リソースを所有する型は、破棄可能でなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 0f96f737274204018be3b30aaa4d85e07cc59f53
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900483"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: ネイティブ リソースを所有する型は、破棄可能でなければなりません
|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 型を参照、<xref:System.IntPtr?displayProperty=fullName>フィールド、<xref:System.UIntPtr?displayProperty=fullName>フィールド、または<xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>フィールドでは実装されません<xref:System.IDisposable?displayProperty=fullName>です。

## <a name="rule-description"></a>規則の説明
 このルールでは<xref:System.IntPtr>、 <xref:System.UIntPtr>、および<xref:System.Runtime.InteropServices.HandleRef>フィールドは、アンマネージ リソースへのポインターを保存します。 アンマネージ リソースを割り当てる型を実装する<xref:System.IDisposable>呼び出し元を要求時にリソースを解放し、リソースを保持するオブジェクトの有効期間を短縮できるようにします。

 アンマネージ リソースをクリーンアップする推奨されるデザイン パターンは、暗黙的なとを使用してそれらのリソースを解放する明示的な手段を提供する、<xref:System.Object.Finalize%2A?displayProperty=fullName>メソッドおよび<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>メソッド、それぞれします。 ガベージ コレクターの呼び出し、<xref:System.Object.Finalize%2A>不確定からしばらく経った時点に到達可能で不要になったオブジェクトを特定のオブジェクトのメソッドです。 後に<xref:System.Object.Finalize%2A>が呼び出されると、追加のオブジェクトを解放するガベージ コレクションが必要です。 <xref:System.IDisposable.Dispose%2A>メソッドにより、呼び出し元が明示的に要求時、ガベージ コレクターの場合に、リソースを解放するとより前にリソースを解放します。 、アンマネージ リソースをクリーンアップ後<xref:System.IDisposable.Dispose%2A>呼び出す必要があります、<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>メソッドをガベージ コレクターのことに注意して<xref:System.Object.Finalize%2A>がなくなりました。 呼び出される追加のガベージ コレクションが不要し、が短縮され、この、オブジェクトの有効期間。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、実装<xref:System.IDisposable>です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 種類は、アンマネージ リソースを参照していない場合は、この規則による警告を抑制するのには安全です。 この規則による警告は抑制しないでくださいそれ以外の場合、実装する障害<xref:System.IDisposable>アンマネージ リソースを使用できないか、使用率の低いになる可能性があります。

## <a name="example"></a>例
 次の例を実装する型を示しています。<xref:System.IDisposable>アンマネージ リソースをクリーンアップします。

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>関連規則
 [CA2115: ネイティブ リソースを使用しているときには GC.KeepAlive を呼び出します](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize を正しく呼び出します](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: 破棄できる型ではファイナライザーを宣言します](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: 破棄可能なフィールドを所有する型は、破棄可能でなければなりません](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>関連項目
 [アンマネージ リソースをクリーンアップする](/dotnet/standard/garbage-collection/unmanaged) [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)