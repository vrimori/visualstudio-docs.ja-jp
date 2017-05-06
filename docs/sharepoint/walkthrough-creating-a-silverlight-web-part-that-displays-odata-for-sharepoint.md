---
title: "チュートリアル: SharePoint の OData を表示する Silverlight Web パーツの作成"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.SilverlightWebPart"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# チュートリアル: SharePoint の OData を表示する Silverlight Web パーツの作成
  SharePoint 2010 は OData でリスト データを公開します。  SharePoint では、OData サービスは RESTful ListData.svc サービスによって実装されます。  このチュートリアルでは、Silverlight アプリケーションをホストする SharePoint Web パーツを作成する方法を示します。  Silverlight アプリケーションが ListData.svc を使用して、SharePoint のお知らせリスト情報が表示されます。  詳細については、[SharePoint Foundation 他のインターフェイス](http://go.microsoft.com/fwlink/?LinkId=225999) 参照します [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000)。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   [Silverlight Web パーツとの Silverlight アプリケーションの作成](#BKMK_creatingSLApp)。  
  
-   [Silverlight アプリケーションのカスタマイズ](#BKMK_customizeSLApp)。  
  
-   [Silverlight アプリケーションのカスタマイズ](#BKMK_customizeSLApp)。  
  
-   [Silverlight アプリケーションのカスタマイズ](#BKMK_customizeSLApp)。  
  
-   [Silverlight Web パーツのテスト](#BKMK_testSLApp)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="BKMK_creatingSLApp"></a> Silverlight Web パーツとの Silverlight アプリケーションの作成  
 まず、Visual Studio で Silverlight アプリケーションを作成します。  Silverlight アプリケーションで、お知らせが ListData.svc サービスを使用して表示する SharePoint からデータを取得します。  
  
> [!NOTE]  
>  4.0 のサポートの前の Silverlight のバージョンなしの SharePoint リスト データを参照するための要求インターフェイス。  
  
#### Silverlight アプリケーションおよび Silverlight Web プロジェクトを作成するには、パーツ  
  
1.  メニュー バーで、**\[新しいプロジェクト\]** ダイアログ ボックスを表示するには、**\[新規作成\]**、**\[プロジェクト\]\[ファイル\]** をクリックします。  
  
2.  **\[SharePoint\]** ノードを **\[Visual C\#\]** または **\[Visual Basic\]** で展開し、**2010** ノードを選択します。  
  
3.  テンプレート ペインで、**\[SharePoint 2010 Silverlight Web パーツ\]** テンプレートを選択します。  
  
4.  **\[名前\]** ボックスで、SLWebPartTest を入力し、**\[OK\]** ボタンをクリックします。  
  
     **\[SharePoint カスタマイズ ウィザード\]** ダイアログ ボックスが表示されます。  
  
5.  **\[デバッグのサイトとセキュリティ レベルの指定\]** ページで、サイト定義をデバッグすると入力するか、既定の場所 \(http:\/\/*system name*\/\) を使用して、SharePoint サーバー サイトの URL を指定します。  
  
6.  **\[この SharePoint ソリューションの信頼レベル\]** セクションで **\[ファーム ソリューションとして配置する\]** を選択します。  
  
     この例では、ファーム ソリューションを使用すると、Silverlight Web パーツ プロジェクトとは、ファームまたはサンドボックス ソリューション配置できます。  サンドボックス ソリューションとファーム ソリューションの違いの詳細については、「[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)」を参照してください。  
  
7.  **\[Silverlight 構成情報の指定\]** ページの **\[Silverlight Web パーツを関連付ける方法\]** セクションで、**\[新しい Silverlight プロジェクトを作成して Web パーツと関連付ける\]** のオプション ボタンを選択します。  
  
8.  **\[名前\]** を SLApplication に変更し、**\[Visual Basic\]** または **\[Visual C\#\]** に **\[言語\]** を設定し、**\[Microsoft Silverlight 4.0\]** に **\[Silverlight バージョン\]** を設定します。  
  
9. **\[完了\]** をクリックします。  プロジェクトは **\[ソリューション エクスプローラー\]** に表示されます。  
  
     ソリューションは、2 種類のプロジェクトが含まれています: Silverlight アプリケーションおよび Silverlight Web パーツは。  Silverlight アプリケーションが SharePoint リストからデータを取得し、表示し、Silverlight Web パーツは、Silverlight アプリケーションをホストし、SharePoint で調べることができます。  
  
##  <a name="BKMK_customizeSLApp"></a> Silverlight アプリケーションのカスタマイズ  
 Silverlight アプリケーションにコードとデザイン要素を追加します。  
  
#### Silverlight アプリケーションをカスタマイズするには  
  
1.  Silverlight アプリケーションの System.Windows.Data アセンブリへの参照を追加します。  詳細については、「[方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)」を参照してください。  
  
2.  **\[ソリューション エクスプローラー\]** で、**\[参照\]** のショートカット メニューを開き、**\[サービス参照の追加\]** をクリックします。  
  
    > [!NOTE]  
    >  Visual Basic を使用している場合は **\[ソリューション エクスプローラー\]** の上に **\[参照\]** ノードを表示するに **\[すべてのファイルを表示\]** アイコンを選択する必要があります。  
  
3.  **\[サービス参照の追加\]** ダイアログ ボックスのアドレス ボックスに、SharePoint サイトの URL を、**http:\/\/MySPSite**"など\) を入力し、**\[移動\]** ボタンをクリックします。  
  
     Silverlight は、SharePoint OData サービス ListData.svc を検出すると、完全サービス URL でアドレスを置き換えます。  この例では、http:\/\/myserver または http:\/\/myserver\/\_vti\_bin\/ListData.svc になります。  
  
4.  プロジェクトにサービス参照を追加するに **\[OK\]** ボタンをクリックして、既定のサービスの名前、ServiceReference1 を使用します。  
  
5.  メニュー バーの **\[ビルド\]**、**\[ソリューションのビルド\]** の順にクリックします。  
  
6.  SharePoint Services に基づいてプロジェクトに新しいデータ ソースを追加します。  これを行うには、メニュー バーにするには、**\[その他のウィンドウ\]**、**\[データ ソース\]\[表示\]** をクリックします。  
  
     **\[データ ソース\]** ウィンドウはタスク、お知らせと予定表など、SharePoint で使用できるデータがすべて一覧表示されます。  
  
7.  Silverlight アプリケーションでのお知らせリスト データを追加します。  Silverlight デザイナーに **\[データ ソース\]** ウィンドウから「お知らせ」をドラッグできます。  
  
     これは、SharePoint サイトのお知らせリストにバインドされるグリッド コントロールを作成します。  
  
8.  Silverlight ページに合わせてグリッド コントロールのサイズを変更します。  
  
9. MainPage.xaml でファイル \(Visual C\# の MainPage.xaml.cs または Visual Basic の MainPage.xaml.vb\) を追加します。次の名前空間参照をコーディングする必要があります。  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#1](SP_SLWebPart#1)]  -->  
  
10. クラスの先頭に次の変数を追加します。  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#2](SP_SLWebPart#2)]  -->  
  
11. 次の `UserControl_Loaded` プロシージャを置き換えます。  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#3](SP_SLWebPart#3)]  -->  
  
     SharePoint を実行しているサーバーの名前と *ServerName* のプレースホルダーを置き換えることを確認してください。  
  
12. 次のエラー処理手順を追加します。  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#4](SP_SLWebPart#4)]  -->  
  
## Silverlight Web パーツの変更  
 Silverlight のデバッグを可能にする Silverlight Web パーツ プロジェクトのプロパティを変更します。  
  
#### Silverlight Web パーツを変更するには  
  
1.  Silverlight Web パーツ プロジェクト \(**\[SLWebPartTest\]**\) のショートカット メニューを開き、**\[プロパティ\]** をクリックします。  
  
2.  **\[プロパティ\]** ウィンドウで、**\[SharePoint\]** タブをクリックします。  
  
3.  これがまだ選択されていない場合 **\[Script デバッグの代わりに Silverlight デバッグを有効にする\]** チェック ボックスをオンにします。  
  
4.  プロジェクトを保存します。  
  
##  <a name="BKMK_testSLApp"></a> Silverlight Web パーツのテスト  
 SharePoint リスト データが正しく表示されることを確認するために、新しい SharePoint Silverlight Web パーツをテストします。  
  
#### Silverlight Web パーツをテストするには  
  
1.  SharePoint ソリューションをビルドして実行するには、F5 キーを押します。  
  
2.  SharePoint では、**\[サイトの操作\]** メニューで、**\[新しいページ\]** をクリックします。  
  
3.  **\[新しいページ\]** ダイアログにタイトルを、SL Web パーツのテストなど\) を入力し、**\[作成\]** ボタンをクリックします。  
  
4.  ページ デザイナーで、**\[編集ツール\]** タブで、**\[挿入\]** をクリックします。  
  
5.  タブの削除で、**\[Web パーツ\]** をクリックします。  
  
6.  **\[カテゴリ\]** ボックスで、**\[カスタム\]** フォルダーをクリックします。  
  
7.  **\[Web パーツ\]** の一覧で、Silverlight Web パーツを選択し、デザイナーに Web パーツを追加するに **\[追加\]** ボタンをクリックします。  
  
8.  使用する Web ページに加算のすべてを行った後で、**\[ページ\]** タブを選択し、ツール バーの **\[保存して閉じる & \]** ボタンをクリックします。  
  
     Silverlight Web パーツは、SharePoint サイトのお知らせデータが表示されます。  既定では SharePoint サイトにページで、ページ リストが格納されます。  
  
    > [!NOTE]  
    >  ドメイン間で Silverlight、Silverlight データへのアクセスが Web アプリケーションの開発に使用できるセキュリティ上の脆弱性を防止する場合。  Silverlight のリモート データにアクセスするときに問題が発生した場合 [サービスがドメインの境界を越えて使用できるようにします。](http://go.microsoft.com/fwlink/?LinkId=223276)、参照すれば。  
  
## 参照  
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [SharePoint ソリューションのパッケージの配置、発行、アップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  