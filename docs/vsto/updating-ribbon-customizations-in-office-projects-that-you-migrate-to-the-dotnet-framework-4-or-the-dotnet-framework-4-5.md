---
title: ".NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズの更新 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office プロジェクト [Visual Studio での Office 開発], 移行 (.NET Framework 4 への)"
ms.assetid: 3b7c8ad4-a616-4b42-9d62-9658fdefe6a3
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# .NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズの更新
  **\[リボン \(ビジュアル デザイナー\)\]** プロジェクト項目を使用して作成したリボンのカスタマイズを含むプロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、プロジェクト コードに対して次の変更を行う必要があります。  
  
-   生成されたリボン コードを変更する。  
  
-   実行時にリボン コントロールをインスタンス化するコード、リボン イベントを処理するコード、またはリボン コンポーネントの位置をプログラムによって設定するコードをすべて変更する。  
  
## 生成されたリボン コードの更新  
 プロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、次の手順を実行して、リボン項目に対して生成されたコードを変更する必要があります。  更新する必要があるコード ファイルは、プログラミング言語の種類とプロジェクトの作成方法に応じて次のように異なります。  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] または [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] のいずれかで作成した Visual Basic プロジェクトまたは Visual C\# プロジェクトの場合は、リボンの分離コード ファイル \(*YourRibbonItem*.Designer.cs または *YourRibbonItem*.Designer.vb\) ですべての手順を実行します。  Visual Basic プロジェクトで分離コード ファイルを確認するには、**ソリューション エクスプローラー**の **\[すべてのファイルの表示\]** をクリックします。  
  
-   Visual Studio 2008 で作成してから [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] にアップグレードした Visual C\# プロジェクトの場合は、リボンのコード ファイル \(*YourRibbonItem*.cs または *YourRibbonItem*.vb\) で最初の 2 つの手順を実行し、リボンの分離コード ファイルで残りの手順を実行します。  
  
#### 生成されたリボン コードを変更するには  
  
1.  <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> の代わりに Microsoft.Office.Tools.Ribbon.OfficeRibbon から派生するように、リボン クラスの宣言を変更します。  
  
2.  リボン クラスのコンストラクターを次のように変更します。  コンストラクターに独自のコードを追加している場合は、コードを変更しないでください。  Visual Basic プロジェクトでは、パラメーターなしのコンストラクターのみを変更します。  その他のコンストラクターは無視します。  
  
     .NET Framework 3.5 を対象とするプロジェクトのリボン クラスの既定のコンストラクターを次のコード例に示します。  
  
    ```vb  
    Public Sub New()  
        MyBase.New()  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
    {  
        InitializeComponent();  
    }  
    ```  
  
     [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトのリボン クラスの既定のコンストラクターを次のコード例に示します。  
  
    ```vb  
    Public Sub New()  
        MyBase.New(Globals.Factory.GetRibbonFactory())  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
        : base(Globals.Factory.GetRibbonFactory())  
    {  
        InitializeComponent();  
    }  
    ```  
  
3.  `InitializeComponent` メソッドでは、代わりに <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトのいずれかのヘルパー メソッドが使用されるように、リボン コントロールを構築するすべてのコードを変更します。  
  
    > [!NOTE]  
    >  Visual C\# プロジェクトでは、`Component Designer generated code` メソッドを表示するために `InitializeComponent` という名前の領域を展開する必要があります。  
  
     たとえば、.NET Framework 3.5 を対象とするプロジェクトで、<xref:Microsoft.Office.Tools.Ribbon.RibbonButton> という名前の `button1` をインスタンス化する次のコード行がファイルに含まれていると仮定します。  
  
    ```vb  
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();  
    ```  
  
     [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、代わりに次のコードを使用する必要があります。  
  
    ```vb  
    Me.button1 = Me.Factory.CreateRibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = this.Factory.CreateRibbonButton();  
    ```  
  
     リボン コントロールのすべてのヘルパー メソッドの一覧については、「[リボン コントロールのインスタンス化](#ribboncontrols)」を参照してください。  
  
4.  Visual C\# プロジェクトでは、代わりに特定のリボン デリゲートが使用されるように、`InitializeComponent` デリゲートを使用する <xref:System.EventHandler%601> メソッドのコード行を変更します。  
  
     たとえば、.NET Framework 3.5 を対象とするプロジェクトで、<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> イベントを処理する次のコード行がファイルに含まれていると仮定します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler<Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>(  
        this.button1_Click);  
    ```  
  
     [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、代わりに次のコードを使用する必要があります。  
  
    ```csharp  
    this.button1.Click += new Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler(  
        this.button1_Click);  
    ```  
  
     すべてのリボン デリゲートの一覧については、「[リボン イベントの処理](#ribbonevents)」を参照してください。  
  
5.  Visual Basic プロジェクトでは、ファイルの最後にある `ThisRibbonCollection` クラスを検索します。  このクラスが Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection から継承されないように、クラスの宣言を変更します。  
  
##  <a name="ribboncontrols"></a> リボン コントロールのインスタンス化  
 リボン コントロールを動的にインスタンス化するすべてのコードを変更する必要があります。  .NET Framework 3.5 を対象とするプロジェクトでは、リボン コントロールは特定のシナリオで直接インスタンス化できるクラスです。  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、これらのコントロールはインターフェイスであるため、直接インスタンス化できません。  コントロールを作成するには、<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトが提供するメソッドを使用する必要があります。  
  
 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトにアクセスするには、次の 2 つの方法があります。  
  
-   リボン クラスの Factory プロパティの使用。  この方法は、リボン クラス内のコードから使用します。  
  
-   Globals.Factory.GetRibbonFactory メソッドの使用。  この方法は、リボン クラス外のコードから使用します。  Globals クラスの詳細については、「[Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)」を参照してください。  
  
 次のコード例は、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトのリボン クラスで <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> を作成する方法を示しています。  
  
```vb  
Dim button As Microsoft.Office.Tools.Ribbon.RibbonButton =  
    Me.Factory.CreateRibbonButton()  
```  
  
```csharp  
Microsoft.Office.Tools.Ribbon.RibbonButton button =  
    this.Factory.CreateRibbonButton();  
```  
  
 次の表は、プログラムによって作成できるコントロールと、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでのコントロールの作成に使用するメソッドを示しています。  
  
|コントロール|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降のプロジェクトで使用する RibbonFactory メソッド|  
|------------|-----------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|  
  
##  <a name="ribbonevents"></a> リボン イベントの処理  
 リボン コントロールのイベントを処理するすべてのコードを変更する必要があります。  .NET Framework 3.5 を対象とするプロジェクトでは、これらのイベントは汎用の <xref:System.EventHandler%601> デリゲートによって処理されます。  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、これらのイベントは他のデリゲートによって処理されるようになりました。  
  
 次の表は、リボンのイベントと、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでこれらのイベントに関連付けられているデリゲートを示しています。  
  
|イベント|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降のプロジェクトで使用するデリゲート|  
|----------|---------------------------------------------------------------------------------|  
|生成されたリボン クラスの <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> イベント|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## リボン コンポーネントの位置をプログラムによって設定する  
 リボンのグループ、タブ、またはコントロールの位置を設定するすべてのコードを変更する必要があります。  .NET Framework 3.5 を対象とするプロジェクトでは、静的な AfterOfficeId クラスの BeforeOfficeId メソッドと Microsoft.Office.Tools.Ribbon.RibbonPosition メソッドを使用して、グループ、タブ、またはコントロールの Position プロパティを割り当てることができます。  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトが提供する <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> プロパティを使用して、これらのメソッドにアクセスする必要があります。  
  
 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトにアクセスするには、次の 2 つの方法があります。  
  
-   リボン クラスの Factory プロパティの使用。  この方法は、リボン クラス内のコードから使用します。  
  
-   Globals.Factory.GetRibbonFactory メソッドの使用。  この方法は、リボン クラス外のコードから使用します。  Globals クラスの詳細については、「[Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)」を参照してください。  
  
 次のコード例は、.NET Framework 3.5 を対象とするプロジェクトでリボン クラスのタブの Position プロパティを設定する方法を示しています。  
  
```vb  
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");  
```  
  
 次のコード例は、同じ作業を [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とするプロジェクトで行う方法を示しています。  
  
```vb  
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");  
```  
  
## 参照  
 [.NET Framework 4 以降への Office ソリューションの移行](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)  
  
  