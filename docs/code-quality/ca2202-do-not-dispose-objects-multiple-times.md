---
title: CA2202:オブジェクトを複数回破棄しない
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d65e9466a57e28b8e0322fc45401fb6e2333aaf7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012262"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202:オブジェクトを複数回破棄しない

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

メソッドの実装には、複数の呼び出しを引き起こす可能性のあるコード パスが含まれています。<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>または同じオブジェクトで、一部の型に対する Close() メソッドなどの Dispose と同等です。

## <a name="rule-description"></a>規則の説明

正しく実装する<xref:System.IDisposable.Dispose%2A>メソッドは、例外をスローせず複数回呼び出すことができます。 ただし、これは保証されませんが生成されないようにして、<xref:System.ObjectDisposedException?displayProperty=fullName>呼び出す必要はありません<xref:System.IDisposable.Dispose%2A>オブジェクトの 1 つ以上の時間。

## <a name="related-rules"></a>関連するルール

- [CA 2000:スコープが失われる前にオブジェクトを破棄します。](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を解決するには、コード パスのことに関係なく実装を変更する<xref:System.IDisposable.Dispose%2A>オブジェクトの 1 つだけの時間と呼びます。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。 場合でも<xref:System.IDisposable.Dispose%2A>オブジェクトには複数回を安全に呼び出すことがわかっていますの場合、実装が、将来変更可能性があります。

## <a name="example"></a>例

入れ子になった`using`ステートメント (`Using` Visual Basic の) ca 2202 警告の違反が発生することができます。 場合、入れ子になった内側の IDisposable のリソース`using`ステートメントは、外部のリソースを含む`using`ステートメントでは、`Dispose`入れ子になったリソースのメソッドが含まれているリソースを解放します。 このような状況が発生したときに、`Dispose`メソッドの外側の`using`ステートメントは、リソースを dispose を 2 回目のしようとしています。

次の例では、<xref:System.IO.Stream>外部で作成されるオブジェクトの Dispose メソッドでステートメントを使用して内部の最後にリリースがステートメントを使用して、<xref:System.IO.StreamWriter>オブジェクトを含む、`stream`オブジェクト。 外側の最後に`using`ステートメントでは、`stream`オブジェクトが 2 番目の時間を解放します。 2 番目のリリースでは、ca 2202 違反です。

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>例

この問題を解決するには、使用、 `try` / `finally`ではなく、外側のブロック`using`ステートメント。 `finally`ことを確認、ブロック、`stream`リソースが null でないです。

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>関連項目

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)