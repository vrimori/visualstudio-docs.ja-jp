---
title: "方法 : n 層アプリケーションのデータセットにコードを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "n 層アプリケーション, 拡張 (データセットを)"
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 20
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : n 層アプリケーションのデータセットにコードを追加する
*DatasetName*.Dataset.Designer ファイルにコードを追加する代わりに、データセットの部分クラス ファイルを作成してコードを追加することにより、データセットの機能を拡張できます。  部分クラスによって、特定のクラスのコードを複数の物理ファイルに分割できます。  詳細については、「[Partial](/dotnet/visual-basic/language-reference/modifiers/partial)」または「[部分クラスと部分メソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)」を参照してください。  
  
 データセットを定義するコードは、\([型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)で\) データセット定義に変更が加えられるたびに生成されます。  このコードは、データセットの構成を変更するウィザードの実行中に変更を加えた場合も生成されます。  データセットの再生成中にコードが削除されるのを防ぐには、データセットの部分クラス ファイルにコードを追加します。  
  
 既定では、データセットと `TableAdapter` コードを分離すると、結果としてプロジェクトごとに別個のクラス ファイルが生成されます。  元のプロジェクトには、`TableAdapter` コードを含む *DatasetName*.Designer.vb \(または *DatasetName*.Designer.cs\) というファイルが存在します。  **"DataSet プロジェクト"** プロパティで指定したプロジェクトには、データセット コードを含む *DatasetName*.DataSet.Designer.vb \(または *DatasetName*.DataSet.Designer.cs\) というファイルが存在します。  
  
> [!NOTE]
>  **"DataSet プロジェクト"** プロパティを設定してデータセットと `TableAdapter` を分離する場合でも、プロジェクト内の既存のデータセット部分クラスは自動的には移動されません。  既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
> [!NOTE]
>  [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)には、検証コードを追加する必要がある場合に <xref:System.Data.DataTable.ColumnChanging> イベント ハンドラーおよび <xref:System.Data.DataTable.RowChanging> イベント ハンドラーを生成する機能も備わっています。  詳細については、「[方法 : n 層データセットに検証を追加する](../data-tools/add-validation-to-an-n-tier-dataset.md)」を参照してください。  
  
### n 層アプリケーションのデータセットにコードを追加するには  
  
1.  .xsd ファイルを含むプロジェクト \([型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)\) を見つけます。  
  
2.  **.xsd** ファイルをダブルクリックして、[型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)を開きます。  
  
3.  コードを追加するデータ テーブル \(タイトル バーのテーブル名\) を右クリックし、**\[コードの表示\]** をクリックします。  
  
     部分クラスが作成され、コード エディターが開きます。  
  
4.  部分クラスの宣言内にコードを追加します。  
  
     次の例は、NorthwindDataSet の CustomersDataTable にコードを追加する場所を示しています。  
  
    ```vb#  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```c#  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## 参照  
 [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)   
 [方法 : n 層アプリケーションの TableAdapters にコードを追加する](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapter](../Topic/TableAdapters.md)   
 [TableAdapterManager の概要](../Topic/TableAdapterManager%20Overview.md)   
 [階層更新の概要](../Topic/Hierarchical%20Update%20Overview.md)   
 [データ アプリケーションの作成](../data-tools/creating-data-applications.md)   
 [Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)