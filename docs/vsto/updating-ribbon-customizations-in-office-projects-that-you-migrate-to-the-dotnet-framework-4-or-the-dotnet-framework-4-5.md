---
title: .NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズの更新 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 98c5dee34fd40506289cf4a9f31488c3acc710ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトのリボンのカスタマイズの更新
  リボンのカスタマイズを使用して作成されたが、プロジェクトに含まれているかどうか、**リボン (ビジュアル デザイナー)**プロジェクト項目、ターゲット フレームワークに変更する場合、プロジェクト コードに、次の変更を行う必要があります、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはあとで。  
  
-   生成されたリボン コードを変更する。  
  
-   実行時にリボン コントロールをインスタンス化するコード、リボン イベントを処理するコード、またはリボン コンポーネントの位置をプログラムによって設定するコードをすべて変更する。  
  
## <a name="updating-the-generated-ribbon-code"></a>生成されたリボン コードの更新  
 プロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、次の手順を実行して、リボン項目に対して生成されたコードを変更する必要があります。 更新する必要があるコード ファイルは、プログラミング言語の種類とプロジェクトの作成方法に応じて次のように異なります。  
  
-   Visual Basic プロジェクトで、またはいずれかで作成した Visual c# プロジェクトで[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]または[!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]リボン分離コード ファイル内のすべてのステップを実行 (*YourRibbonItem*です。Designer.cs または*YourRibbonItem*です。)。 Visual Basic プロジェクトで分離コード ファイルを表示する] をクリックして、 **[すべてのファイル**ボタン**ソリューション エクスプ ローラー**です。  
  
-   Visual Studio 2008 で作成しにアップグレードした Visual c# プロジェクトで[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]、リボン コード ファイル内の最初の 2 つの手順を実行します (*YourRibbonItem*.cs または*YourRibbonItem*.vb)、およびリボンの分離コード ファイルで、残りの手順を実行します。  
  
#### <a name="to-change-the-generated-ribbon-code"></a>生成されたリボン コードを変更するには  
  
1.  派生するように、リボン クラスの宣言を変更<xref:Microsoft.Office.Tools.Ribbon.RibbonBase>Microsoft.Office.Tools.Ribbon.OfficeRibbon の代わりにします。  
  
2.  リボン クラスのコンストラクターを次のように変更します。 コンストラクターに独自のコードを追加している場合は、コードを変更しないでください。 Visual Basic プロジェクトでは、パラメーターなしのコンストラクターのみを変更します。 その他のコンストラクターは無視します。  
  
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
    >  Visual C# プロジェクトでは、`Component Designer generated code` メソッドを表示するために `InitializeComponent` という名前の領域を展開する必要があります。  
  
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
  
     リボン コントロールのヘルパー メソッドの一覧については、次を参照してください。[リボン コントロールのインスタンス化する](#ribboncontrols)です。  
  
4.  Visual C# プロジェクトでは、代わりに特定のリボン デリゲートが使用されるように、`InitializeComponent` デリゲートを使用する <xref:System.EventHandler%601> メソッドのコード行を変更します。  
  
     たとえば、.NET Framework 3.5 を対象とするプロジェクトで、<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> イベントを処理する次のコード行がファイルに含まれていると仮定します。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
     [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、代わりに次のコードを使用する必要があります。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
     リボン デリゲートの一覧については、次を参照してください。[リボン イベントを処理](#ribbonevents)です。  
  
5.  Visual Basic プロジェクトでは、ファイルの最後にある `ThisRibbonCollection` クラスを検索します。 このクラスの宣言を変更して、Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection から継承されないようにします。  
  
##  <a name="ribboncontrols"></a> リボン コントロールをインスタンス化します。  
 リボン コントロールを動的にインスタンス化するすべてのコードを変更する必要があります。 .NET Framework 3.5 を対象とするプロジェクトでは、リボン コントロールは特定のシナリオで直接インスタンス化できるクラスです。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、これらのコントロールはインターフェイスであるため、直接インスタンス化できません。 コントロールを作成するには、<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトが提供するメソッドを使用する必要があります。  
  
 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトにアクセスするには、次の 2 つの方法があります。  
  
-   リボンの工場出荷時のプロパティを使用して次のようにクラスです。 この方法は、リボン クラス内のコードから使用します。  
  
-   Globals.Factory.GetRibbonFactory メソッドを使用します。 この方法は、リボン クラス外のコードから使用します。 Globals クラスの詳細については、次を参照してください。 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)です。  
  
 次のコード例は、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトのリボン クラスで <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> を作成する方法を示しています。  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 次の表は、プログラムによって作成できるコントロールと、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでのコントロールの作成に使用するメソッドを示しています。  
  
|コントロール|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降のプロジェクトで使用する RibbonFactory メソッド|  
|-------------|---------------------------------------------------------------------------------------------------------------|  
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
 リボン コントロールのイベントを処理するすべてのコードを変更する必要があります。 .NET Framework 3.5 を対象とするプロジェクトでは、これらのイベントは汎用の <xref:System.EventHandler%601> デリゲートによって処理されます。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、これらのイベントは他のデリゲートによって処理されるようになりました。  
  
 次の表は、リボンのイベントと、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでこれらのイベントに関連付けられているデリゲートを示しています。  
  
|event|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降のプロジェクトで使用するデリゲート|  
|-----------|---------------------------------------------------------------------------------------------------|  
|生成されたリボン クラスの <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> イベント|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## <a name="setting-the-position-of-a-ribbon-component-programmatically"></a>リボン コンポーネントの位置をプログラムによって設定する  
 リボンのグループ、タブ、またはコントロールの位置を設定するすべてのコードを変更する必要があります。 プロジェクトでは、.NET Framework 3.5 をターゲットとすることができますメソッドを使用する AfterOfficeId と [beforeofficeid] 静的 Microsoft.Office.Tools.Ribbon.RibbonPosition クラスのグループ、タブ、またはコントロールの位置プロパティを割り当てる。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とするプロジェクトでは、<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトが提供する <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> プロパティを使用して、これらのメソッドにアクセスする必要があります。  
  
 <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> オブジェクトにアクセスするには、次の 2 つの方法があります。  
  
-   リボンの工場出荷時のプロパティを使用して次のようにクラスです。 この方法は、リボン クラス内のコードから使用します。  
  
-   Globals.Factory.GetRibbonFactory メソッドを使用します。 この方法は、リボン クラス外のコードから使用します。 Globals クラスの詳細については、次を参照してください。 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)です。  
  
 次のコード例では、.NET Framework 3.5 を対象とするプロジェクトでリボン クラスでのタブの位置プロパティを設定する方法を示します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [.NET Framework 4 以降への Office ソリューションの移行](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)  
  
  