---
title: 'CA1024: 適切な場所にプロパティを使用します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5677604505bf21b8f14a2f3ef6ca1341fc9ff191
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551676"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: 適切な場所にプロパティを使用します

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

パブリックまたはプロテクト メソッドで始まる名前を持つ`Get`パラメーターは、配列でない値を返します。

## <a name="rule-description"></a>規則の説明

ほとんどの場合、プロパティは、データを表すし、メソッドがアクションを実行します。 プロパティは、それらを使いやすく、フィールドのようにアクセスします。 メソッドは、これらの条件のいずれかが存在する場合、プロパティに適した候補です。

- 引数を受け取らないし、オブジェクトの状態情報を返します。

- オブジェクトの状態の一部を設定する 1 つの引数を受け取ります。

プロパティがフィールドが表示されるかのように動作する必要があります。メソッドには、することはできません。 プロパティを変更しない必要があります。 メソッドは、次の状況でのプロパティよりも優れています。

- メソッドは、時間のかかる操作を実行します。 メソッドでは、フィールドの値を取得または設定するために必要な時間よりも明らかに長くかかります。

- メソッドは、変換を実行します。 フィールドへのアクセス、保存されるデータの変換後のバージョンは返されません。

- Get メソッドでは、監視可能な副作用が発生します。 フィールドの値を取得する場合は、副作用は生成されません。

- 実行の順序が重要です。 フィールドの値の設定は、その他の操作が発生するときに依存しません。

- 連続して 2 回のメソッドを呼び出すには、異なる結果が作成されます。

- メソッドは静的だが、呼び出し元によって変更可能なオブジェクトを返します。 フィールドの値を取得するフィールドが格納されているデータを変更する呼び出し元を許可しません。

- メソッドでは、配列を返します。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を解決するには、プロパティに、メソッドを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

メソッドが上記の条件の少なくとも 1 つを満たしている場合は、この規則による警告を抑制します。

## <a name="controlling-property-expansion-in-the-debugger"></a>デバッガーでのプロパティの展開を制御します。

1 つの理由がプログラマは、プロパティを使用しないようにデバッガーを自動拡張をしないためにです。 たとえば、大きなオブジェクトの割り当てや、P/invoke を呼び出し、プロパティを伴う可能性が観測可能な副作用が実際に必要がありますいません。

デバッガーが自動拡張ようにプロパティを適用することで<xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>します。 次の例では、インスタンス プロパティに適用されているこの属性を示します。

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
}
```

## <a name="example"></a>例

次の例では、いくつかの方法ですが、プロパティに変換され、フィールドのように動作しないためではなく必要がありますをいくつか含まれています。

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]