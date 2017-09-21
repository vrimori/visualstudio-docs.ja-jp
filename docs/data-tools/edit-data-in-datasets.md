---
title: "データセットのデータの編集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 編集 (データセットで)"
  - "データセット [Visual Basic], 編集 (データの)"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# データセットのデータの編集
<xref:System.Data.DataSet> のデータ編集は、データセットを形成する個々の <xref:System.Data.DataTable> オブジェクトの実際のデータを操作するプロセスです。  データ テーブルのデータは通常のデータベース テーブルのデータを編集する場合と同様に編集でき、このプロセスにはテーブルのレコードの挿入、更新、および削除が含まれます。  
  
 実際のデータ変更の他に、<xref:System.Data.DataTable> にクエリを実行し、個別の行、特定のバージョンの行 \(Original、Proposed\)、変更された行のみ、およびエラーが発生した行のみなどの特定のデータ行を返すこともできます。  
  
## データ テーブルの一般的なタスク  
 次の表に、データセットのデータを編集してクエリを実行することに関する一般的なタスクへのリンクを示します。  
  
|タスク|説明|  
|---------|--------|  
|データ テーブルに新規レコードを挿入する|<xref:System.Data.DataRow> を新規作成し、テーブル行のコレクションに追加します。  詳細については、「[方法 : DataTable に行を追加する](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md)」を参照してください。|  
|データ テーブルの既存のレコードを更新する|データ行の特定の列に値を直接代入します。  詳細については、「[方法 : DataTable の行を編集する](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md)」を参照してください。|  
|データ テーブルから既存のレコードを削除する|テーブルから削除するデータ行の <xref:System.Data.DataRow.Delete%2A> メソッドを呼び出します。  詳細については、「[方法 : DataTable の行を削除する](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md)」を参照してください。|  
|データ テーブルの変更されたレコードを特定する|データ テーブルの <xref:System.Data.DataTable.GetChanges%2A> メソッドを呼び出します。  詳細については、「[方法 : 変更された行を取得する](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)」を参照してください。|  
|データ テーブルの行の異なるバージョンにアクセスする|参照する <xref:System.Data.DataRowVersion> を渡してデータ行の個々の列にアクセスします。  詳細については、「[方法 : 特定のバージョンの DataRow を取得する](../Topic/How%20to:%20Get%20Specific%20Versions%20of%20a%20DataRow.md)」を参照してください。|  
|データ テーブルでエラーがある行を特定する|データ テーブルの <xref:System.Data.DataTable.HasErrors%2A> プロパティを確認します。  詳細については、「[方法 : エラーが発生している行を探す](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md)」を参照してください。|  
  
## 参照  
 [DataTable](../Topic/DataTables.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [DataTable](../Topic/DataTables.md)   
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)