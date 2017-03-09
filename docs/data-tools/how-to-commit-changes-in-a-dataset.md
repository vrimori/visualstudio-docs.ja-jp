---
title: "方法 : データセットの変更をコミットする | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データセット [Visual Basic], コミット (変更を)"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : データセットの変更をコミットする
レコードの更新、挿入、および削除によってデータセットのレコードを変更すると、データセットはレコードの元のバージョンおよび現在のバージョンを保持します。  さらに、各行の <xref:System.Data.DataRow.RowState%2A> プロパティは、レコードが元の状態にあるかどうか、つまりレコードへの更新、挿入、または削除が行われたかどうかを追跡します。  この情報は、行の特定のバージョンを見つける必要がある場合に役立ちます。  通常は、すべての変更されたレコードのサブセットを取得し、別のプロセスに送ります。  詳細については、「[方法 : 変更された行を取得する](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)」を参照してください。  変更された行をすべて処理した後で、<xref:System.Data.DataSet>、<xref:System.Data.DataTable>、または <xref:System.Data.DataRow> の `AcceptChanges` メソッドを呼び出すことにより変更をコミットできます。  `AcceptChanges` メソッドは、[TableAdapter](../data-tools/tableadapter-overview.md) またはデータ アダプターの Update メソッドを呼び出すと自動的に呼び出されます。  変更をデータベースに送信した後で、`AcceptChanges` を呼び出します。  
  
 <xref:System.Data.DataSet> の <xref:System.Data.DataSet.AcceptChanges%2A> を呼び出した時点でまだ編集モードにあった <xref:System.Data.DataRow> オブジェクトは、正常に編集を終了します。  各<xref:System.Data.DataRow> の<xref:System.Data.DataRow.RowState%2A> プロパティも変わります。<xref:System.Data.DataRowState> 行と <xref:System.Data.DataRowState> 行は <xref:System.Data.DataRowState> になり、<xref:System.Data.DataRowState> 行は削除されます。  
  
 <xref:System.Data.DataSet> に <xref:System.Data.ForeignKeyConstraint> オブジェクトが含まれる場合、<xref:System.Data.DataSet.AcceptChanges%2A> メソッドを呼び出すと、<xref:System.Data.AcceptRejectRule> が適用されます。  
  
### データセットの変更をコミットするには  
  
-   <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、または <xref:System.Data.DataRow> のいずれかに対して `AcceptChanges` メソッドを呼び出し、これらのオブジェクトの変更をコミットします。  
  
     `AcceptChanges` メソッドを呼び出し、データ ソースの更新後に `Customers` テーブルの変更をコミットする方法を次の例に示します。  
  
     [!CODE [VbRaddataEditing#11](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#11)]  
  
## 参照  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [データの保存](../data-tools/saving-data.md)   
 [方法 : 変更された行を取得する](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)