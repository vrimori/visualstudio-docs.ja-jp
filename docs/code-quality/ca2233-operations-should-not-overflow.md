---
title: "CA2233: 操作はオーバーフローできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2233: 操作はオーバーフローできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドで算術演算が実行され、オーバーフローが発生する前にオペランドの検証が完了しません。  
  
## 規則の説明  
 まずオペランドを検証し、演算結果が関連するデータ型で使用できる値の範囲を超えないことを確認してから、算術演算を実行します。  実行コンテキストおよび関連するデータ型によって変わりますが、算術オーバーフローによって <xref:System.OverflowException?displayProperty=fullName> または結果の最上位ビットが破棄されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、演算を実行する前にオペランドを検証します。  
  
## 警告を抑制する状況  
 オペランドで使用できる値によって算術演算のオーバーフローが発生しない場合、この規則による警告を抑制しても安全です。  
  
## 違反の例  
  
### 説明  
 次の例にあるメソッドは、この規則に違反する整数を操作します。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、これを実行するには **Remove** 整数のオーバーフロー オプションを無効にする必要があります。  
  
### コード  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### コメント  
 この例のメソッドに <xref:System.Int32.MinValue?displayProperty=fullName> が渡される場合、演算はアンダーフローします。  これにより、結果の最上位ビットは破棄されます。  このしくみを次のコードに示します。  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### 出力  
  
```  
2147483647  
```  
  
## 入力パラメーターの検証による修正  
  
### 説明  
 入力の値を検証することによって上記の違反を修正するコード例を次に示します。  
  
### コード  
 [!CODE [FxCop.Usage.OperationOverflowFixed#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed#1)]  
  
## checked ブロックによる修正  
  
### 説明  
 checked ブロックで演算をラップすることによって上記の違反を修正するコード例を次に示します。  演算がオーバーフローする場合は、<xref:System.OverflowException?displayProperty=fullName> がスローされます。  
  
 checked ブロックは、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ではサポートされていません。  
  
### コード  
 [!CODE [FxCop.Usage.OperationOverflowChecked#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked#1)]  
  
## 演算のオーバーフローおよびアンダーフローのチェックの有効化  
 C\# で演算のオーバーフローおよびアンダーフローのチェックを有効にすると、すべての整数演算を checked ブロックでラップしたときと同じ結果が得られます。  
  
 **C\# で演算のオーバーフローおよびアンダーフローのチェックを有効にするには**  
  
1.  **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[ビルド\]** タブをクリックし、**\[詳細設定\]** をクリックします。  
  
3.  **\[演算のオーバーフローおよびアンダーフローのチェック\]** を選択し、**\[OK\]** をクリックします。  
  
## 参照  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C\# 演算子](/dotnet/csharp/language-reference/operators/index)   
 [Checked と Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)