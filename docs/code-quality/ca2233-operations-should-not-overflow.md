---
title: "Ca 2233: 操作はオーバーフローできません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f5d048476997517a835337b568930367f97c2c92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: 操作はオーバーフローできません
|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 メソッドは、算術演算を実行して、オーバーフローを防ぐにはあらかじめオペランドは検証されません。  
  
## <a name="rule-description"></a>規則の説明  
 最初に関連するデータ型で使用可能な値の範囲外の演算の結果がないようにするオペランドを検証せず、算術演算を実行できません必要があります。 実行コンテキストと関連するデータ型では、によって算術オーバーフローがいずれかになることができます、<xref:System.OverflowException?displayProperty=fullName>または結果の最上位ビットが破棄されます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、操作を実行する前にオペランドを検証します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 指定できる値はオペランドの算術演算のオーバーフローが発生しない場合、この規則による警告を抑制する安全です。  
  
## <a name="example-of-a-violation"></a>違反の例  
  
### <a name="description"></a>説明  
 次の例のメソッドは、この規則に違反する整数を操作します。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]必要があります、**削除**これ起動を無効にする整数オーバーフローのオプションです。  
  
### <a name="code"></a>コード  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### <a name="comments"></a>コメント  
 この例では、メソッドが渡された場合<xref:System.Int32.MinValue?displayProperty=fullName>操作はアンダー フローが発生します。 これにより、破棄されるように結果の最上位ビットです。 次のコードは、このしくみを示しています。  
  
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
  
## <a name="fix-with-input-parameter-validation"></a>入力パラメーターの検証を解決します。  
  
### <a name="description"></a>説明  
 次の例では、入力の値を検証することによって上記の違反を修正します。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_2.cs)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_2.vb)]  
  
## <a name="fix-with-a-checked-block"></a>Checked ブロックでの解決します。  
  
### <a name="description"></a>説明  
 次の例は、checked ブロックで、操作をラップすることによって、前の違反を修正します。 操作で、オーバーフローが発生した場合、<xref:System.OverflowException?displayProperty=fullName>がスローされます。  
  
 Checked ブロックがでサポートされていないことに注意してください[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]です。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_3.cs)]  
  
## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>算術オーバーフローまたはアンダー フローのチェックを有効にします。  
 Checked 算術オーバーフローおよびアンダー フロー (C#) を有効にする場合は、checked ブロック内のすべての整数演算の折り返しと同じです。  
  
 **C# では算術演算のオーバーフローおよびアンダー フローがチェックを有効にします。**  
  
1.  **ソリューション エクスプ ローラー**をプロジェクトを右クリックして**プロパティ**です。  
  
2.  **[ビルド]** タブを選択してから **[詳細設定]** をクリックします。  
  
3.  選択**算術オーバーフローおよびアンダー フローのチェック** をクリック**OK**です。  
  
## <a name="see-also"></a>参照  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C# 演算子](/dotnet/csharp/language-reference/operators/index)   
 [Checked と Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)