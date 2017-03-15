---
title: "方法: データ テーブルを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VSDesigner.DataSource.DesignTable"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 作成 (データ テーブルを)"
  - "データセット デザイナー, 作成 (データ テーブルを)"
  - "テーブル [Visual Studio], 作成"
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法: データ テーブルを作成する
データは、<xref:System.Data.DataTable> オブジェクトのメモリに格納できます \(データセットは <xref:System.Data.DataTable> オブジェクトで構成されます\)。通常、新しいデータ テーブルは、[TableAdapter 構成ウィザード](../Topic/TableAdapter%20Configuration%20Wizard.md)を使用して TableAdapter で作成するか、**サーバー エクスプローラー**から**データセット デザイナー**にデータベース オブジェクトをドラッグして作成します。  
  
 データ テーブルは新しい TableAdapter を作成する際に副産物として [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png) で作成されますが、個別に作成することもできます。  **ツールボックス**の **\[データセット\]** タブから**データセット デザイナー**に <xref:System.Data.DataTable> オブジェクトをドラッグして、スタンドアロンのデータ テーブルを作成します。  
  
> [!NOTE]
>  プログラムでデータ テーブルを作成する方法については、「[DataTable の作成](../Topic/Creating%20a%20DataTable.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## TableAdapter を使用するデータ テーブルの作成  
 TableAdapter を使用するデータ テーブルには、テーブルにデータを格納し、変更内容をデータベースに書き戻すメソッドが含まれます。  **TableAdapter 構成ウィザード**を実行するか、**サーバー エクスプローラー**から**データセット デザイナー**にデータベース オブジェクトをドラッグして、TableAdapter を作成します。  
  
#### TableAdapter を使用する新しいデータ テーブルを作成するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  
  
2.  **ツールボックス**の **\[データセット\]** タブから**データセット デザイナー**に、**\[TableAdapter\]** をドラッグします。  
  
     **TableAdapter 構成ウィザード**が開きます。  
  
3.  ウィザードの指示に従います。  詳細については、「[TableAdapter 構成ウィザード](../Topic/TableAdapter%20Configuration%20Wizard.md)」を参照してください。  
  
#### サーバー エクスプローラーで TableAdapter を使用する新しいデータ テーブルを作成するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  
  
2.  **サーバー エクスプローラー**から**データセット デザイナー**にデータベース オブジェクト \(たとえば、テーブル\) をドラッグします。  
  
## スタンドアロン DataTable の作成  
 スタンドアロン テーブルには、データを格納するために実装される `Fill` ロジックが必要です。  スタンドアロン データ テーブルにデータを格納する方法については、「[DataAdapter からの DataSet の読み込み](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)」を参照してください。  
  
#### 新しいスタンドアロンのデータ テーブルを作成するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  
  
2.  **ツールボックス**の **\[データセット\]** タブから <xref:System.Data.DataTable> を**データセット デザイナー**にドラッグします。  
  
3.  列を追加してデータ テーブルを定義します。  詳細については、「[方法 : DataTable に列を追加する](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)」を参照してください。  
  
## 参照  
 <xref:System.Data.DataTable>   
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [ウィンドウ](../Topic/Data%20Sources%20Window.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](../Topic/Validating%20Data.md)