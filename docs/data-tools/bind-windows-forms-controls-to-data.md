---
title: "方法: Windows フォーム コントロールをデータにバインドする | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "データ [Windows フォーム], 表示"
  - "データ ソース, 表示"
  - "表示 (データを), Windows フォーム コントロール"
  - "Windows フォーム, 表示 (データを)"
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法: Windows フォーム コントロールをデータにバインドする
データを Windows フォーム コントロールにバインドするには、[ウィンドウ](../Topic/Data%20Sources%20Window.md)からオブジェクトをドラッグします。  **\[データ ソース\]** ウィンドウから項目をドラッグする前に、テーブルのコントロールの種類を、個別のコントロールの場合は **\[詳細\]**、<xref:System.Windows.Forms.DataGridView> の場合は **\[DataGridView\]** にそれぞれ設定できます。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
 アプリケーションに必要なコントロールが **\[データ ソース\]** のウィンドウ内から利用できない場合は、コントロールを追加できます。  詳細については、「[\[データ ソース\] ウィンドウにカスタム コントロールを追加する](../Topic/Add%20custom%20controls%20to%20the%20Data%20Sources%20window.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 個々のコントロールにデータのテーブル全体を表示する  
 **\[データ ソース\]** ウィンドウから Windows アプリケーションのフォームにテーブル \(オブジェクト データ ソースを使用している場合はコレクションを表すノード\) をドラッグすることにより、個々のコントロールにデータのテーブル全体を表示できます。  
  
#### データのテーブル全体を表示するには  
  
1.  **\[データ ソース\]** ウィンドウを開きます。  詳細については、「[方法: \[データ ソース\] ウィンドウを開く](../Topic/How%20to:%20Open%20the%20data%20sources%20window.md)」を参照してください。  
  
    > [!NOTE]
    >  **\[データ ソース\]** ウィンドウが空の場合は、そのウィンドウにデータ ソースを追加します。  詳細については、「[データ ソースの概要](../data-tools/add-new-data-sources.md)」を参照してください。  
  
2.  **Windows フォーム デザイナー**でフォームを開きます。  
  
3.  **\[データ ソース\]** ウィンドウでテーブルを選択し、ドロップダウン矢印をクリックして、**\[詳細\]** をクリックします。  
  
4.  **\[データ ソース\]** ウィンドウからフォームにテーブルをドラッグします。  
  
     適切なタイトルが付けられたラベル コントロールと共に、各列またはプロパティの個々のデータ バインド コントロールがフォーム上に作成されます。  
  
## 個々のコントロールにデータの選択した列を表示する  
 **\[データ ソース\]** ウィンドウから Windows アプリケーションのフォームに個々の列 \(オブジェクト データ ソースを使用している場合はプロパティ\) をドラッグして、個々のコントロールにデータの個々の列を表示します。  
  
#### データの選択した列を表示するには  
  
1.  **\[データ ソース\]** ウィンドウを開きます。  詳細については、「[方法: \[データ ソース\] ウィンドウを開く](../Topic/How%20to:%20Open%20the%20data%20sources%20window.md)」を参照してください。  
  
    > [!NOTE]
    >  **\[データ ソース\]** ウィンドウが空の場合は、そのウィンドウにデータ ソースを追加します。  詳細については、「[データ ソースの概要](../data-tools/add-new-data-sources.md)」を参照してください。  
  
2.  テーブルを展開して、個々の列を表示します。  
  
    > [!TIP]
    >  各列に作成されたコントロールを設定するには、**\[データ ソース\]** ウィンドウで列を選択し、ドロップダウン矢印をクリックして、利用可能なコントロールの一覧からコントロールを選択します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
3.  **Windows フォーム デザイナー**でフォームを開きます。  
  
4.  **\[データ ソース\]** ウィンドウからフォームに目的の列をドラッグします。  
  
     ドラッグしたそれぞれの列またはプロパティについて、適切なタイトルが付けられたラベル コントロールと共に、個々のデータ バインド コントロールがフォーム上に作成されます。  
  
 また、**\[データ ソース\]** ウィンドウから既存のコントロール \(既にフォーム上に存在するコントロール\) に項目をドラッグして、コントロールをデータにバインドすることもできます。  コントロールが既にデータにバインドしている場合は、そのデータ バインディングがリセットされて、最後にドラッグされた項目にバインドします。  
  
> [!NOTE]
>  有効なドロップ ターゲットは、**\[データ ソース\]** ウィンドウからドラッグされた項目の基になるデータ型を表示できるコントロールです。  たとえば、データ型 <xref:System.DateTime> の項目を <xref:System.Windows.Forms.CheckBox> にドラッグしようとしても、<xref:System.Windows.Forms.CheckBox> は日付を表示できないので、有効ではありません。  
  
#### 既存のコントロールをデータにバインドするには  
  
1.  **\[データ ソース\]** ウィンドウを開きます。  詳細については、「[方法: \[データ ソース\] ウィンドウを開く](../Topic/How%20to:%20Open%20the%20data%20sources%20window.md)」を参照してください。  
  
2.  [Windows Forms Designer](http://msdn.microsoft.com/ja-jp/3c3d61f8-f36c-4d41-b9c3-398376fabb15)でフォームを開きます。  
  
3.  **\[データ ソース\]** ウィンドウでテーブルまたはオブジェクトを展開し、各列または各プロパティを表示します。  
  
4.  **\[データ ソース\]** ウィンドウから既存のコントロールに目的の項目をドラッグします。  
  
     これで、選択した項目にコントロールがバインドされます。  
  
## DataGridView コントロールへのデータの表示  
  
#### 新しい Windows フォームの DataGridView コントロールにデータを表示するには  
  
1.  **\[データ ソース\]** ウィンドウを開きます。  詳細については、「[方法: \[データ ソース\] ウィンドウを開く](../Topic/How%20to:%20Open%20the%20data%20sources%20window.md)」を参照してください。  
  
    > [!NOTE]
    >  **\[データ ソース\]** ウィンドウが空の場合は、そのウィンドウにデータ ソースを追加します。  詳細については、「[データ ソースの概要](../data-tools/add-new-data-sources.md)」を参照してください。  
  
2.  **Windows フォーム デザイナー**でフォームを開きます。  
  
3.  **\[データ ソース\]** ウィンドウでテーブルを選択し、ドロップダウン矢印をクリックして、**\[DataGridView\]** をクリックします。  
  
4.  **\[データ ソース\]** ウィンドウからフォームにテーブルをドラッグします。  
  
     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ \(<xref:System.Windows.Forms.BindingNavigator>\) がフォームに表示されます。  [DataSet](../data-tools/dataset-tools-in-visual-studio.md)、[TableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource>、および <xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
#### 既存の Windows フォームの DataGridView コントロールにデータを表示するには  
  
1.  **\[データ ソース\]** ウィンドウを開きます。  詳細については、「[方法: \[データ ソース\] ウィンドウを開く](../Topic/How%20to:%20Open%20the%20data%20sources%20window.md)」を参照してください。  
  
    > [!NOTE]
    >  **\[データ ソース\]** ウィンドウが空の場合は、そのウィンドウにデータ ソースを追加します。  詳細については、「[データ ソースの概要](../data-tools/add-new-data-sources.md)」を参照してください。  
  
2.  **Windows フォーム デザイナー**でフォームを開きます。  
  
3.  **\[データ ソース\]** ウィンドウでテーブルを選択し、ドロップダウン矢印をクリックして、**\[DataGridView\]** をクリックします。  
  
4.  **\[データ ソース\]** ウィンドウからフォームの <xref:System.Windows.Forms.DataGridView> にテーブルをドラッグします。  
  
     <xref:System.Windows.Forms.DataGridView> コントロールは、ドラッグしたテーブルにバインドされます。  [DataSet](../data-tools/dataset-tools-in-visual-studio.md)、[TableAdapter](../data-tools/tableadapter-overview.md)、および <xref:System.Windows.Forms.BindingSource> がコンポーネント トレイに表示されます。  
  
## 参照  
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)   
 [BindingNavigator コントロールの概要](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)   
 [Visual Studio でデータ ソースを操作するためのツール](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)