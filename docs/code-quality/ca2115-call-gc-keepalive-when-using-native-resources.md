---
title: 'CA2115: ネイティブ リソースを使用しているときには GC.KeepAlive を呼び出します'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 3eea5a288dc907881b7eb444b26d7018e8008ad2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: ネイティブ リソースを使用しているときには GC.KeepAlive を呼び出します
|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 ファイナライザーを含む型で宣言されたメソッドを参照して、<xref:System.IntPtr?displayProperty=fullName>または<xref:System.UIntPtr?displayProperty=fullName>フィールドでは呼び出しません<xref:System.GC.KeepAlive%2A?displayProperty=fullName>です。

## <a name="rule-description"></a>規則の説明
 ガベージ コレクションは、マネージ コードで参照がある場合、オブジェクトを終了しません。 アンマネージ オブジェクトへの参照は、ガベージ コレクションを阻止しません。 この規則では、アンマネージ コードでまだ使用されているのに、アンマネージ リソースが終了されたときに発生する可能性のあるエラーを検出します。

 このルールでは<xref:System.IntPtr>と<xref:System.UIntPtr>フィールドは、アンマネージ リソースへのポインターを保存します。 ファイナライザーの目的は、アンマネージ リソースを解放はであるため、ルールでは、ポインターのフィールドによって示されるアンマネージ リソースをファイナライザーが解放される想定しています。 このルールでは、メソッドがアンマネージ コードにアンマネージ リソースを渡すポインター フィールドを参照していることも前提とします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、呼び出しを追加して<xref:System.GC.KeepAlive%2A>、メソッドに渡して、現在のインスタンス (`this` c# および C++ で) の引数として。 ガベージ コレクションからオブジェクトを保護する必要があるコードの最後の行の後に呼び出しを配置します。 呼び出しの直後に<xref:System.GC.KeepAlive%2A>オブジェクトへの参照がマネージはないと想定されるガベージ コレクションの準備完了と見なされますもう一度です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則は、偽陽性につながる可能性があるいくつかの前提条件を使用します。 場合は、安全にこの規則による警告を抑制することができます。

-   ファイナライザーの内容を確保できない、<xref:System.IntPtr>または<xref:System.UIntPtr>メソッドによって参照されるフィールドです。

-   メソッドは渡さないようにして、<xref:System.IntPtr>または<xref:System.UIntPtr>フィールドをアンマネージ コードにします。

 慎重に除外する前に他のメッセージを確認します。 このルールは、再生やデバッグが困難なエラーを検出します。

## <a name="example"></a>例
 次の例では、`BadMethod`への呼び出しを含まない`GC.KeepAlive`し、そのため、規則に違反します。 `GoodMethod` 修正後のコードが含まれています。

> [!NOTE]
>  この例では、コードをコンパイルして実行、擬似コード、アンマネージ リソースの作成または解放されていないために、この警告は発生しません。

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>関連項目
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName> <xref:System.Object.Finalize%2A?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)