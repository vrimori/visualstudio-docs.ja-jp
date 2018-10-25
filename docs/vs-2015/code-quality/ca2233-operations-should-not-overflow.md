---
title: 'Ca 2233: 操作はオーバーフローできません |Microsoft Docs'
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
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5f6690f6577d936757ae3bbe8b725b4434b6bee1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836659"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: 操作はオーバーフローできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 メソッドは、算術演算を実行して、オーバーフローを防ぐには事前のオペランドは検証されません。

## <a name="rule-description"></a>規則の説明
 最初に関連するデータ型に指定できる値の範囲外操作の結果がないことを確認するオペランドを検証せず、算術演算を実行できません必要があります。 によって実行コンテキストおよび関連するデータ型の場合は、算術オーバーフローにより、いずれかを<xref:System.OverflowException?displayProperty=fullName>または結果の最上位ビットが破棄されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、操作を実行する前にオペランドを検証します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 オペランドに使用できる値は、算術演算のオーバーフローが発生しない場合、この規則による警告を抑制するのには安全です。

## <a name="example-of-a-violation"></a>違反の例

### <a name="description"></a>説明
 次の例のメソッドは、この規則に違反する整数を操作します。 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 必要があります、**削除**整数オーバーフローのオプションを起動するこの無効にします。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>コメント
 この例では、メソッドが渡された場合<xref:System.Int32.MinValue?displayProperty=fullName>操作はアンダー フローが発生します。 これにより、破棄する結果の最上位ビットです。 次のコードは、このしくみを示しています。

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 [VB]

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>出力

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>入力パラメーターの検証を修正します。

### <a name="description"></a>説明
 次の例は、入力の値を検証することで、前の違反を修正します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Checked ブロックと修正します。

### <a name="description"></a>説明
 次の例では、checked ブロックで、操作をラップすることによって前の違反を修正します。 操作、オーバーフローが発生した場合、<xref:System.OverflowException?displayProperty=fullName>がスローされます。

 Checked ブロックがでサポートされていないことに注意してください。[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>チェックされている算術演算のオーバーフローおよびアンダー フローを有効にします。
 チェックされている算術オーバーフローおよびアンダー フロー (C#) を有効にする場合は、checked ブロックですべての整数演算の折り返しと同じです。

 **C# で算術演算のオーバーフローおよびアンダー フローがチェックを有効にするには**

1.  **ソリューション エクスプ ローラー**プロジェクトを右クリックし、選択、**プロパティ**します。

2.  **[ビルド]** タブを選択してから **[詳細設定]** をクリックします。

3.  選択**算術オーバーフローおよびアンダー フローの確認** をクリック**OK**。

## <a name="see-also"></a>関連項目
 <xref:System.OverflowException?displayProperty=fullName> [C# 演算子](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked と Unchecked](http://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)



