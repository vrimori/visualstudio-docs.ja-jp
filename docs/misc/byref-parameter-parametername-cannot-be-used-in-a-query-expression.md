---
title: "&#39;ByRef&#39; パラメーター &lt;parametername&gt; をクエリ式で使用することはできません | Microsoft Docs"
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
  - "vbc36533"
  - "bc36533"
helpviewer_keywords: 
  - "BC36533"
ms.assetid: 8067ac87-dd6b-4869-87d0-8a4ce272de41
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ByRef&#39; パラメーター &lt;parametername&gt; をクエリ式で使用することはできません
LINQ クエリに含まれるパラメーターがポインター型です。 クエリ式に使用するパラメーターを参照渡しで渡すことはできません。  
  
 **エラー ID:** BC36533  
  
### このエラーを解決するには  
  
1.  新しい変数を宣言し、参照で渡される値のコピーにその新しい変数の値を割り当てます。 コピーした変数を LINQ クエリで使用します。 次に例を示します。  
  
    ```vb#  
    Sub RunQuery(ByVal collection As List(Of Integer), _  
                 ByRef filterValue As Integer)  
        Dim fv = filterValue  
        Dim queryResult = From num In collection _  
                          Where num < fv  
    End Sub  
    ```  
  
### このエラーを解決するには  
  
1.  `ByRef` キーワードを、クエリで使用するパラメーターの `ByVal` キーワードに置き換えます。  
  
## 参照  
 [Differences Between Passing an Argument By Value and By Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)