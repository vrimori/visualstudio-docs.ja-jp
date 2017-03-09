---
title: "方法: Visual Studio でデータに WPF コントロールをバインドする | Microsoft Docs"
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
  - "データ [WPF], 表示"
  - "データ バインド, WPF"
  - "表示 (データを), WPF"
  - "WPF [WPF], データ"
  - "WPF データ バインド [Visual Studio]"
  - "WPF デザイナー, データ バインド"
  - "WPF, データ バインド (Visual Studio での)"
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 26
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法: Visual Studio でデータに WPF コントロールをバインドする
データ バインド [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] コントロールを作成するには、**\[データ ソース\]** ウィンドウを使用します。  まず、**\[データ ソース\]** ウィンドウにデータ ソースを追加します。  次に、**\[データ ソース\]** ウィンドウから **WPF デザイナー**に項目をドラッグします。  
  
##  <a name="adding"></a> \[データ ソース\] ウィンドウへのデータ ソースの追加  
 データ バインド コントロールを作成するには、まず、**\[データ ソース\]** ウィンドウにデータ ソースを追加する必要があります。  
  
#### \[データ ソース\] ウィンドウにデータ ソースを追加するには  
  
1.  **\[表示\]** メニューの **\[その他のウィンドウ\]** をポイントし、**\[データ ソース\]** をクリックします。  
  
2.  **\[新しいデータ ソースの追加\]** をクリックして、**データ ソース構成**ウィザードの操作を完了します。  
  
3.  次のいずれかのタスクを実行して、データ バインド コントロールを作成します。  
  
    -   [単一のデータ フィールドにバインドされるコントロールを作成する](#simple)。  
  
    -   [複数のデータ フィールドにバインドされるコントロールを作成する](#complex)。  
  
    -   [複数のデータ フィールドにバインドされるコントロール セットを作成する](#details)。  
  
    -   [デザイナー内の既存のコントロールにデータをバインドする](#existing)。  
  
##  <a name="simple"></a> 単一のデータ フィールドにバインドされるコントロールの作成  
 **\[データ ソース\]** ウィンドウにデータ ソースを追加すると、<xref:System.Windows.Controls.ComboBox> や <xref:System.Windows.Controls.TextBox> など、単一のデータ フィールドを表示する新しいデータ バインド コントロールを作成できます。  
  
#### 単一のデータ フィールドにバインドされるコントロールを作成するには  
  
1.  **\[データ ソース\]** ウィンドウで、テーブルまたはオブジェクトを表す項目を展開します。  バインドする列またはプロパティを表す子項目を検索します。  表示例については、「[ウィンドウ](../Topic/Data%20Sources%20Window.md)」を参照してください。  
  
2.  必要に応じて、作成するコントロールを選択します。  **\[データ ソース\]** ウィンドウの各項目には、デザイナーに項目をドラッグしたときに作成される既定のコントロールが関連付けられています。  既定のコントロールは、項目の基になるデータ型によって異なります。  
  
     既定以外のコントロールを選択するには、項目の横にあるドロップダウン矢印をクリックし、コントロールを選択します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
3.  デザイナーで、<xref:System.Windows.Controls.Grid> などの有効なコンテナーに項目をドラッグします。  有効なコンテナーの詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、新しいデータ バインド コントロールと適切なタイトルの付いた <xref:System.Windows.Controls.Label> がコンテナー内に作成されます。  また、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、データにコントロールをバインドするための [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] とコードが生成されます。  詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
##  <a name="complex"></a> 複数のデータ フィールドにバインドされるコントロールの作成  
 **\[データ ソース\]** ウィンドウにデータ ソースを追加すると、<xref:System.Windows.Controls.DataGrid> や <xref:System.Windows.Controls.ListView> など、複数のデータ フィールドを表示する新しいデータ バインド コントロールを作成できます。  
  
#### 複数のデータ フィールドにバインドされるコントロールを作成するには  
  
1.  **\[データ ソース\]** ウィンドウで、テーブルまたはオブジェクトを表す項目を選択します。  表示例については、「[ウィンドウ](../Topic/Data%20Sources%20Window.md)」を参照してください。  
  
2.  必要に応じて、作成するコントロールを選択します。  既定では、データ テーブルまたはオブジェクトを表す **\[データ ソース\]** ウィンドウ内の各項目が、<xref:System.Windows.Controls.DataGrid> \(プロジェクトの対象が .NET Framework 4 の場合\) または <xref:System.Windows.Controls.ListView> \(旧バージョンの .NET Framework の場合\) を作成するように設定されます。  
  
     既定以外のコントロールを選択するには、項目の横にあるドロップダウン矢印をクリックし、コントロールを選択します。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)」を参照してください。  
  
    > [!NOTE]
    >  特定の列またはプロパティを表示しないようにする場合は、項目を展開してその子を表示します。  表示しない列またはプロパティの横にあるドロップダウン矢印をクリックし、**\[なし\]** をクリックします。  
  
3.  デザイナーで、<xref:System.Windows.Controls.Grid> などの有効なコンテナーに項目をドラッグします。  有効なコンテナーの詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、新しいデータ バインド コントロールがコンテナー内に作成されます。また、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、データにコントロールをバインドするための [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] とコードも生成されます。  詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
##  <a name="details"></a> 複数のデータ フィールドにバインドされるコントロール セットの作成  
 **\[データ ソース\]** ウィンドウにデータ ソースを追加すると、コントロール セットにデータ テーブルまたはオブジェクトをバインドできます。  テーブルまたはオブジェクトの列やプロパティごとに、異なるコントロールが作成されます。  
  
#### 複数のデータ フィールドにバインドされるコントロール セットを作成するには  
  
1.  **\[データ ソース\]** ウィンドウで、テーブルまたはオブジェクトを表す項目を選択します。  表示例については、「[ウィンドウ](../Topic/Data%20Sources%20Window.md)」を参照してください。  
  
2.  項目の横にあるドロップダウン矢印をクリックし、**\[詳細\]** を選択します。  
  
    > [!NOTE]
    >  特定の列またはプロパティを表示しないようにする場合は、項目を展開してその子を表示します。  表示しない列またはプロパティの横にあるドロップダウン矢印をクリックし、**\[なし\]** をクリックします。  
  
3.  デザイナーで、<xref:System.Windows.Controls.Grid> などの有効なコンテナーに項目をドラッグします。  有効なコンテナーの詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、新しいデータ バインド コントロールがコンテナー内に作成されます。  各コントロールは別々の列またはプロパティにバインドされ、適切なタイトルの <xref:System.Windows.Controls.Label> コントロールが追加されます。また、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、データにコントロールをバインドするための [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] とコードも生成されます。  詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
##  <a name="existing"></a> デザイナー内の既存のコントロールへのデータのバインド  
 **\[データ ソース\]** ウィンドウにデータ ソースを追加すると、デザイナー内の既存のコントロールにデータ バインディングを追加できます。  
  
#### デザイナー内の既存のコントロールにデータをバインドするには  
  
1.  **\[データ ソース\]** ウィンドウで、次のいずれかの手順を実行します。  
  
    -   <xref:System.Windows.Controls.DataGrid> や <xref:System.Windows.Controls.ListView> など、複数のデータ フィールドを表示する既存のコントロールにデータ バインディングを追加するには、コントロールにバインドするテーブルまたはオブジェクトを表す項目を選択します。  
  
    -   <xref:System.Windows.Controls.ComboBox> や <xref:System.Windows.Controls.TextBox> など、単一のデータ フィールドを表示する既存のコントロールにデータ バインディングを追加するには、データが格納されているテーブルまたはオブジェクトを表す項目を展開し、コントロールにバインドするデータを表す項目を選択します。  
  
2.  **\[データ ソース\]** ウィンドウから、選択した項目をデザイナー内の既存のコントロールにドラッグします。  コントロールは、有効なドロップ ターゲットである必要があります。  詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、コントロールをデータにバインドする [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] とコードが生成されます。  詳細については、「[Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)」を参照してください。  
  
    > [!NOTE]
    >  コントロールが既にデータにバインドされている場合は、コントロールのデータ バインディングが、最後にコントロールにドラッグされた項目に再設定されます。  
  
## 参照  
 [Visual Studio でのデータへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [方法: WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [方法: WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)   
 [チュートリアル: データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [チュートリアル: WCF Data Service への WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [チュートリアル: WPF アプリケーションでの関連データの表示](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)