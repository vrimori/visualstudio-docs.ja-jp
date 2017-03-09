---
title: "&#39;&lt;nullconstant&gt;&#39; は宣言されていません | Microsoft Docs"
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
  - "bc30822"
  - "vbc30822"
helpviewer_keywords: 
  - "BC30822"
ms.assetid: dda0e2c1-46a3-4cc4-b36c-0858a5259bac
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nullconstant&gt;&#39; は宣言されていません
'\<nullconstant\>' が宣言されていません。 Null 定数は現在サポートされていません。代わりに System.DBNull を使用してください。  
  
 ステートメントが `Null` キーワードを使用していますが、このキーワードは Visual Basic でサポートされなくなりました。  
  
 **エラー ID:** BC30822  
  
### このエラーを解決するには  
  
1.  <xref:System.DBNull> の代わりに `Null` を使用します。 次に例を示します。  
  
    ```  
    Sub TestDBNull() Dim t As DataTable ' Assume the DataGrid is bound to a DataTable. t = CType(DataGrid1.DataSource, DataTable) Dim r As DataRow r = t.Rows(datagrid1.CurrentCell.RowNumber) r.BeginEdit r(1) = System.DBNull.Value ' Assign DBNull to the record. r.EndEdit r.AcceptChanges If r.IsNull(1) Then MsgBox("") End If End Sub  
    ```  
  
2.  オブジェクト変数を使用するときには、代入と比較に [Nothing](/dotnet/visual-basic/language-reference/nothing) キーワードを使用します。 次に例を示します。  
  
    ```  
    Sub TestNothing() Dim cls As Object ' cls is Nothing if it has not been assigned using the New keyword. If (cls Is Nothing) Then MsgBox("cls is Nothing") End If cls = Nothing ' Assign Nothing to the class variable cls. End Sub  
    ```  
  
## 参照  
 <xref:System.DBNull>   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/ja-jp/0483590a-6309-449c-a2fa-effa26a03b95)