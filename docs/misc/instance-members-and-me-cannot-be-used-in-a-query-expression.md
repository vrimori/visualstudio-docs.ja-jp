---
title: "インスタンス メンバーおよび &#39;Me&#39; をクエリ式内で使用することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36535"
  - "bc36535"
helpviewer_keywords: 
  - "BC36535"
ms.assetid: afb5281b-70a7-48c7-a46d-39522b96b1ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# インスタンス メンバーおよび &#39;Me&#39; をクエリ式内で使用することはできません
`Structure` 内の LINQ クエリに、`Me` またはその構造体のインスタンス メンバーへの参照が含まれています。`Structure` 内のクエリ式では、`Me` またはインスタンス メンバーへの参照を使用できません。  
  
 **エラー ID:** BC36535  
  
### このエラーを解決するには  
  
1.  インスタンス メンバーのコピー、または `Me` への参照から返される値のコピーを作成し、それをクエリ式の中で使用します。次に例を示します。  
  
    ```vb#  
    Structure SampleStructure Public SearchValue As Integer Public Sub SetSearchValue(ByVal number As Integer) SearchValue = number End Sub Public Sub GetData() Dim sv = SearchValue Dim SampleData = New Integer() {1, 2, 3, 4} Dim query = From number In SampleData _ Where number < sv End Sub End Structure  
    ```  
  
## 参照  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Me](http://msdn.microsoft.com/ja-jp/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)