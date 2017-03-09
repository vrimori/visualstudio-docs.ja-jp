---
title: "例外のトラブルシューティング : System.Data.NoNullAllowedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "NoNullAllowedException クラス"
ms.assetid: 1ab87572-007f-4b84-bb13-c3626e7f89cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Data.NoNullAllowedException
<xref:System.Data.NoNullAllowedException> が <xref:System.Data.DataColumn.AllowDBNull%2A> に設定されている列に null 値を挿入しようとすると、`false` 例外がスローされます。  
  
## 関連するヒント  
 **値を列に追加する前に、その値が DBNull であるかどうかを確認します。**  
 <xref:System.Data.DataColumn.AllowDBNull%2A> が `false` に設定されている場合は、null 値を挿入できません。 詳細については、「<xref:System.DBNull>」を参照してください。  
  
 **AllowDBNull を true に設定します。**  
 このプロパティを `true` に設定すると、null 値を挿入できるようになります。 詳細については、「<xref:System.Data.DataColumn.AllowDBNull%2A>」を参照してください。  
  
## コメント  
 データ フォームで、ナビゲーション ボタンを使ってデータベース テーブルのレコード内を移動すると、この例外がスローされ、"列 '列' に Null を使用することはできません。" というエラー メッセージが表示される場合があります。 この動作が発生するのは、データベース テーブルの主キーまたは "not NULL" 列がデータ フォーム ウィザードで選択されていないことに原因があります。 データ フォームの作成時にデータベースの主キーまたは "not NULL" 列がデータ フォーム ウィザードで選択されていない場合は、**\[追加　\- 新規レコードを作成します\]** オプションが無効になります。 この問題に対処するには、データ フォームを追加するときに選択したテーブルの主キー列と NULL を許可しない列を、データ フォーム ウィザードを使って選択します。  
  
## 参照  
 <xref:System.Data.NoNullAllowedException>   
 <xref:System.Data.DataRowCollection.Add%2A>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 <xref:System.Data.DataTable.LoadDataRow%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)