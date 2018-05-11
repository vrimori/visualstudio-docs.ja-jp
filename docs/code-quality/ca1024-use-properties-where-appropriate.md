---
title: 'CA1024: 適切な場所にプロパティを使用します'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03318241206b812f4ffb57dddfc6b4f021d600f1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: 適切な場所にプロパティを使用します
|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト メソッドで始まる名前が指定されて`Get`パラメーターを受け取らず、および配列ではない値を返します。

## <a name="rule-description"></a>規則の説明
 ほとんどの場合、プロパティを表すデータとメソッドが操作を実行します。 プロパティを使用しやすいように、フィールドのようにアクセスします。 メソッドは、これらの条件のいずれかが存在する場合、プロパティに適した候補です。

-   引数を使用しないと、オブジェクトの状態情報を返します。

-   オブジェクトの状態の一部を設定する単一の引数を受け入れます。

 プロパティがフィールドはかのように動作する必要があります。メソッドには、することはできません。 プロパティに変更されません必要があります。 メソッドは、次の状況でプロパティより優れています。

-   メソッドでは、時間のかかる操作を実行します。 メソッドでは、フィールドの値を取得または設定する必要がある時間より明らかに長くかかります。

-   メソッドでは、変換を実行します。 フィールドへのアクセスは、格納されるデータの変換後のバージョンは返されません。

-   Get メソッドでは、監視可能な副作用が発生します。 フィールドの値を取得する場合は、副作用は生成されません。

-   実行の順序が重要です。 フィールドの値の設定は、その他の操作が発生するときに依存しません。

-   メソッドを呼び出すこと、2 回連続して、異なる結果を作成します。

-   メソッドは静的だが、呼び出し元が変更可能なオブジェクトを返します。 フィールドの値を取得する場合は、フィールドに格納されるデータを変更する呼び出し元は許可されません。

-   メソッドは、配列を返します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、プロパティに、メソッドを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 メソッドが、上記の条件の少なくとも 1 つを満たしている場合は、この規則による警告を抑制します。

## <a name="controlling-property-expansion-in-the-debugger"></a>デバッガーでのプロパティの展開を制御します。
 プログラマは、プロパティは使用しないでください 1 つの理由を自動展開デバッガーを使用しないためにです。 たとえば、プロパティには、大きなオブジェクトの割り当てや、P/invoke を呼び出すことが含まれますがいる可能性がありますいない実際には、監視可能な副作用です。

 デバッガーは、自動拡張されないようにできますプロパティを適用して<xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>です。 次の例では、インスタンス プロパティに適用されているこの属性を示します。

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>例
 次の例では、いくつかのメソッド、プロパティを変換する必要があり、フィールドと同様に動作しないために必要がありますをいくつか含まれています。

 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]