---
title: "型指定されたデータセットの作成と編集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner"
  - "vs.data.adddataset"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], データセット デザイナー"
  - "データセット デザイナー"
  - "データセット [Visual Basic], ビジュアルなデザイナー"
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 型指定されたデータセットの作成と編集
**データセット デザイナー**は、型指定されたデータセットおよびそれに含まれる各項目の作成および編集を行うためのビジュアル ツール一式です。  
  
 **データセット デザイナー**では、型指定されたデータセットに含まれるオブジェクトがビジュアル表示されます。  **データセット デザイナー**で、[TableAdapter](../data-tools/tableadapter-overview.md)、[TableAdapter のクエリ](../data-tools/how-to-create-tableadapter-queries.md)、<xref:System.Data.DataTable>、<xref:System.Data.DataColumn>、および <xref:System.Data.DataRelation> の作成と変更を行います。  
  
 **データセット デザイナー**を開くには、**ソリューション エクスプローラー**でデータセットをダブルクリックするか、**\[データ ソース\]** ウィンドウでデータセットを右クリックし、**\[デザイナーで DataSet を編集\]** をクリックします。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  **\[新しい項目の追加\]** ダイアログ ボックスで新しい <xref:System.Data.DataSet> 項目を追加した場合には、**データセット デザイナー**が開き、空のデータセットを編集できます。  
  
> [!NOTE]
>  **データセット デザイナー**を使用すると、データセットの機能を拡張できます。  デザイン サーフェイスをダブルクリックするか、右クリックしてから **\[コードの表示\]** をクリックすると、部分クラス ファイルが作成され、そこでデータセットにコードを追加できます。これはデザイナーによって変更されたり削除されたりしません。  TableAdapter の機能を拡張する方法については、「[方法 : TableAdapter の機能を拡張する](../data-tools/extend-the-functionality-of-a-tableadapter.md)」を参照してください。  
  
 **データセット デザイナー**で実行できる共通のタスクを次の表に示します。  
  
|目的|参照項目|  
|--------|----------|  
|TableAdapter の作成|[方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)|  
|TableAdapter の編集|[方法 : TableAdapter を編集する](../Topic/How%20to:%20Edit%20TableAdapters.md)|  
|TableAdapter クエリの作成|[方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)|  
|TableAdapter クエリの編集|[方法 : TableAdapter クエリを編集する](../data-tools/how-to-edit-tableadapter-queries.md)|  
|<xref:System.Data.DataTable> の作成|[方法: データ テーブルを作成する](../data-tools/how-to-create-data-tables.md)|  
|<xref:System.Data.DataTable> の編集|[DataTable のデザイン](../data-tools/designing-datatables.md)|  
|<xref:System.Data.DataColumn> の作成|[方法 : DataTable に列を追加する](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)|  
|2 つの <xref:System.Data.DataTable> 間のリレーションシップの作成|[方法 : データセット デザイナーで DataRelation を作成する](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)|  
|データセットの機能の拡張|[方法 : データセットの機能を拡張する](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|  
|データ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントへの検証の追加|[方法 : 列の変更時にデータを検証する](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)|  
|データ テーブルの <xref:System.Data.DataTable.RowChanging> イベントへの検証の追加|[方法 : 行の変更時にデータを検証する](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)|  
  
## デザイン サーフェイスでのオブジェクトの作成  
 データセットを構成する各オブジェクトを追加したり編集したりして、データセットを作成できます。  **ツールボックス**の **\[データセット\]** タブからデザイン サーフェイスにドラッグできる各種オブジェクトについて、以下の表に示します。  
  
|オブジェクト|説明|  
|------------|--------|  
|TableAdapter|基になるデータベースとの通信およびデータ テーブルへのデータの格納に使用する、データ コマンドのコレクションおよびデータ接続が含まれます。  詳細については、「[TableAdapter の概要](../data-tools/tableadapter-overview.md)」および「[方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)」を参照してください。|  
|クエリ|TableAdapter のクエリは、SQL ステートメントとストアド プロシージャを実行する、厳密に型指定されたメソッドです。  TableAdapter クエリを実行すると、データ テーブルにデータが格納されたり、他のデータベース タスクが実行されたりします。  詳細については、「[方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)」を参照してください。  テーブルにクエリをドラッグすると、そのテーブルにクエリが追加されますが、**データセット デザイナー**の空の領域にクエリをドラッグした場合は、グローバル クエリが作成されます。  詳細については、「[方法 : データセットにグローバル クエリを追加する](../data-tools/how-to-add-global-queries-to-a-tableadapter.md)」を参照してください。|  
|<xref:System.Data.DataTable>|データベースから返された行のメモリ内コレクションを示します。|  
|リレーションシップ \(<xref:System.Data.DataRelation>\)|2 つの <xref:System.Data.DataTable> 間の親子のリレーションシップを表します。  詳細については、「[DataRelation オブジェクトの概要](../Topic/Introduction%20to%20DataRelation%20Objects.md)」および「[チュートリアル : データ テーブル間のリレーションシップの作成](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)」を参照してください。|  
  
> [!NOTE]
>  **データセット デザイナー**は、データセットが作成されたときにのみ、基になるデータベースに接続します。デザイナーはデータベースに対してその後に行われた変更を自動的に検出しません。  既存の .xsd を更新するには、**構成ウィザード**を再実行します。  テーブルのリレーションシップが変更された場合は、.xsd に関連するテーブルを削除し、再度追加します。  
  
## LINQ to DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] を使用すれば、<xref:System.Data.DataSet> オブジェクトのデータを対象に [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) を実行することが可能になります。  詳細については、「[LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)」を参照してください。  
  
## 参照  
 [チュートリアル : データセット デザイナーでのデータセットの作成](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [チュートリアル : 複数のクエリによる TableAdapter の作成](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [チュートリアル : データセット デザイナーでの DataTable の作成](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [チュートリアル : データ テーブル間のリレーションシップの作成](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [ウィンドウ](../Topic/Data%20Sources%20Window.md)   
 [Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)