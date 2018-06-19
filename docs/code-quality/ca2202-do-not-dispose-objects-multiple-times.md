---
title: 'CA2202: オブジェクトを複数回破棄しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c7eb35e556e8edd6e840f2fbd6701e182895706
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920150"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: オブジェクトを複数回破棄しません
|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 メソッドの実装には、複数の呼び出しを引き起こす可能性のあるコード パスが含まれています。<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>または Dispose と同等の、同じオブジェクトに対して、一部の型に対する Close() メソッドなど、します。

## <a name="rule-description"></a>規則の説明
 正しく実装されて A<xref:System.IDisposable.Dispose%2A>メソッドは、例外をスローせず複数回呼び出すことがあります。 ただし、これとは限りませんが生成されないようにして、<xref:System.ObjectDisposedException?displayProperty=fullName>呼び出す必要はありません<xref:System.IDisposable.Dispose%2A>オブジェクトに対して 1 つ以上の時間。

## <a name="related-rules"></a>関連規則
 [CA2000: スコープが失われる前にオブジェクトを破棄します](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、実装を変更することに関係なく、コード パスの<xref:System.IDisposable.Dispose%2A>は、オブジェクトに対して 1 回だけ呼び出されます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 場合でも<xref:System.IDisposable.Dispose%2A>呼び出せる安全に複数回に既知のオブジェクトは、実装が、今後変更可能性があります。

## <a name="example"></a>例
 入れ子になった`using`ステートメント (`Using` Visual Basic の) ca 2202 警告の違反が発生することができます。 場合、入れ子になった内側の IDisposable リソース`using`ステートメントには、外部のリソースが含まれる`using`ステートメントでは、`Dispose`入れ子になったリソースのメソッドが含まれるリソースを解放します。 このような状況が発生すると、 `Dispose` 、外側のメソッド`using`ステートメントは、2 回目のリソースを破棄しようとしています。

 次の例で、<xref:System.IO.Stream>は外部で作成されるオブジェクトの Dispose メソッド内でステートメントを使用して、内側の最後にリリースがステートメントを使用して、<xref:System.IO.StreamWriter>オブジェクトを含む、`stream`オブジェクト。 外側の最後に`using`ステートメントでは、`stream`オブジェクトが 2 番目の時間を解放します。 2 つ目のリリースでは、ca 2202 の違反です。

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}

```

## <a name="example"></a>例
 この問題を解決するを使用して、 `try` / `finally`ではなく、外側のブロック`using`ステートメントです。 `finally`ブロックは、ことを確認して、`stream`リソースが null ではありません。

```
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
 <xref:System.IDisposable?displayProperty=fullName> [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern)