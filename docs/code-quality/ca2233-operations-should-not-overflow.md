---
title: CA2233:操作はオーバーフローできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 273fb94f4f0b66badef60178635fe3db360f73a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954579"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233:操作はオーバーフローできません

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

メソッドは、算術演算を実行して、オーバーフローを防ぐには事前のオペランドは検証されません。

## <a name="rule-description"></a>規則の説明

最初に関連するデータ型に指定できる値の範囲外操作の結果がないことを確認するオペランドを検証、算術演算を実行しません。 によって実行コンテキストおよび関連するデータ型の場合は、算術オーバーフローにより、いずれかを<xref:System.OverflowException?displayProperty=fullName>または結果の最上位ビットが破棄されます。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、操作を実行する前にオペランドを検証します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

オペランドに使用できる値は、算術演算のオーバーフローが発生しない場合、この規則による警告を抑制するのには安全です。

## <a name="example-of-a-violation"></a>違反の例

次の例のメソッドは、この規則に違反する整数を操作します。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 必要があります、**削除**整数オーバーフローのオプションを起動するこの無効にします。

[!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
[!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]

この例では、メソッドが渡された場合<xref:System.Int32.MinValue?displayProperty=fullName>操作はアンダー フローが発生します。 これにより、破棄する結果の最上位ビットです。 次のコードは、このしくみを示しています。

```csharp
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

```vb
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

Output:

```text
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>入力パラメーターの検証を修正します。

次の例は、入力の値を検証することで、前の違反を修正します。

[!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
[!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]

## <a name="fix-with-a-checked-block"></a>Checked ブロックと修正します。

次の例では、checked ブロックで、操作をラップすることによって前の違反を修正します。 操作、オーバーフローが発生した場合、<xref:System.OverflowException?displayProperty=fullName>がスローされます。

Checked ブロックでサポートされていない[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]します。

[!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>チェックされている算術演算のオーバーフローおよびアンダー フローを有効にします。

チェックされている算術オーバーフローおよびアンダー フロー (C#) を有効にする場合は、checked ブロックですべての整数演算の折り返しと同じです。

有効にするには、c# で算術演算のオーバーフローおよびアンダー フローをチェックしました。

1.  **ソリューション エクスプ ローラー**プロジェクトを右クリックし、選択、**プロパティ**します。

2.  **[ビルド]** タブを選択してから **[詳細設定]** をクリックします。

3.  選択**算術オーバーフローおよびアンダー フローの確認** をクリック**OK**。

## <a name="see-also"></a>関連項目

- <xref:System.OverflowException?displayProperty=fullName>
- [C# 演算子](/dotnet/csharp/language-reference/operators/index)
- [Checked と Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)