---
title: "例外のトラブルシューティング : System.IndexOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "IndexOutOfRangeException クラス"
ms.assetid: 9e28623c-93fc-4111-a0cb-c380e0b5de0c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.IndexOutOfRangeException
<xref:System.IndexOutOfRangeException> 例外は、配列の境界外または 0 よりも小さいインデックスを持つ配列またはコレクションの要素にアクセスしようとするとスローされます。  
  
## 関連するヒント  
 **リスト上の最大インデックスがリスト サイズよりも小さいことを確認します。**  
 リスト上の最大インデックスは、リスト サイズよりも小さくする必要があります。  
  
 **インデックスが負の数でないことを確認します。**  
 この例外は、インデックスが 0 よりも小さい場合にスローされます。  
  
 **データ列名が適切であることを確認します。**  
 この例外は、<xref:System.Data.DataView.Sort%2A?displayProperty=fullName> プロパティに指定されているデータ列名が有効でない場合にスローされます。 詳細については、<xref:System.Data.DataView> クラスを参照してください。  
  
## 例  
  
### 説明  
 インデックス `Try…Catch` が配列の範囲 \(0 ～ 3\) の外にある場合に `IndexOutOfRangeException` ブロックを使用して `i` をトラップする方法を次の例に示します。 この例では、次のように表示されます。  
  
 `Element at index 0: 3`  
  
 `Element at index 2: 5`  
  
 `Element at index -1: IndexOutOfRangeException caught`  
  
 `Element at index 4: IndexOutOfRangeException caught`  
  
### コード  
  
```vb#  
Module Module1 Sub Main() ' The first two tests will display the value of the array element. IndexTest(0) IndexTest(2) ' The following two calls will display the information that ' an IndexOutOfRangeException was caught. IndexTest(-1) IndexTest(4) End Sub Sub IndexTest(ByVal i As Integer) Dim testArray() As Integer = {3, 4, 5, 6} Console.Write("Element at index {0}: ", i) Try Console.WriteLine(testArray(i)) Catch ex As IndexOutOfRangeException Console.WriteLine("IndexOutOfRangeException caught") End Try End Sub End Module  
```  
  
## 参照  
 <xref:System.IndexOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)