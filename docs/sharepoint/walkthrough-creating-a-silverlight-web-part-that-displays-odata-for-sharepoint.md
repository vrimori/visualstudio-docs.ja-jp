---
title: "チュートリアル: が SharePoint の OData を表示する Silverlight Web パーツを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a6999a7a390c207c184f26d36e0ca5d64d5fef5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>チュートリアル: SharePoint の OData を表示する Silverlight Web パーツの作成
  SharePoint 2010 では、OData を使用して、リスト データを公開します。 SharePoint では、OData サービスは、RESTful サービス ListData.svc によって実装されます。 このチュートリアルでは、Silverlight アプリケーションをホストする SharePoint web パーツを作成する方法を示します。 Silverlight アプリケーションでは、ListData.svc を使用して、SharePoint お知らせリスト情報を表示します。 詳細については、次を参照してください。 [SharePoint Foundation REST インターフェイス](http://go.microsoft.com/fwlink/?LinkId=225999)と[Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000)です。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]。  
  
##  <a name="creating-a-silverlight-application-and-silverlight-web-part"></a>Silverlight アプリケーションと Silverlight Web パーツを作成します。  
 最初に、Visual Studio で Silverlight アプリケーションを作成します。 Silverlight アプリケーションでは、ListData.svc サービスを使用して、SharePoint のお知らせリストからデータを取得します。  
  
> [!NOTE]  
>  Silverlight 4.0 より前に、のバージョンは、SharePoint リストのデータを参照している、必要なインターフェイスをサポートなし。  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight アプリケーションと Silverlight web パーツを作成するには  
  
1.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し、 **2010**ノード。  
  
3.  [テンプレート] ペインで、選択、 **SharePoint 2010 Silverlight Web パーツ**テンプレート。  
  
4.  **名前**ボックスに、入力**SLWebPartTest**を選択し、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード** ダイアログ ボックスが表示されます。  
  
5.  **デバッグのサイトとセキュリティ レベルを指定して**ページで、サイト定義をデバッグする SharePoint サーバー サイトの URL を入力するか、既定の場所を使用して (http://*システム名*/).  
  
6.  **この SharePoint ソリューションの信頼レベルは何ですか?**セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。  
  
     この例では、ファーム ソリューションでは、Silverlight web パーツ プロジェクトは、ファームまたはサンド ボックス ソリューションとして展開できます。 サンド ボックス ソリューションとファーム ソリューションの詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
7.  **Silverlight Web パーツを関連付ける方法**のセクションで、 **Silverlight 構成情報の指定**ページで、選択、**新しい Silverlight プロジェクトを作成し、web パーツに関連付ける**オプション ボタンをクリックします。  
  
8.  変更、**名前**に**SLApplication**設定、**言語**いずれかに**Visual Basic**または**Visual c#**、設定**Silverlight バージョン**に**Silverlight 4.0**です。  
  
9. 選択、**完了**ボタンをクリックします。 プロジェクトが表示される**ソリューション エクスプ ローラー**です。  
  
     2 つのプロジェクトがソリューションに含まれています。 Silverlight アプリケーションと Silverlight web パーツ。 Silverlight アプリケーションを取得し、SharePoint からリスト データを表示し、Silverlight web パーツが SharePoint で表示できるように、Silverlight アプリケーションをホストします。  
  
##  <a name="customizing-the-silverlight-application"></a>Silverlight アプリケーションをカスタマイズします。  
 Silverlight アプリケーション コードと設計の要素を追加します。  
  
#### <a name="to-customize-the-silverlight-application"></a>Silverlight アプリケーションをカスタマイズするには  
  
1.  Silverlight アプリケーションでアセンブリ System.Windows.Data への参照を追加します。 詳細については、次を参照してください。[する方法: 追加または参照の追加 ダイアログ ボックスを使用して参照を削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)です。  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**参照**を選択し**サービス参照の追加**です。  
  
    > [!NOTE]  
    >  Visual Basic を使用している場合を選択してください、 **すべてのファイル**の上部にあるアイコン**ソリューション エクスプ ローラー**を表示する、**参照**ノード。  
  
3.  アドレス ボックスで、**サービス参照の追加** ダイアログ ボックスで、SharePoint サイトの URL を入力します。 **http://MySPSite**、を選択し、**移動**ボタンをクリックします。  
  
     Silverlight は、SharePoint の OData サービス ListData.svc を検索、ときに、完全なサービス URL をアドレスに置き換えます。 この例では、http://myserver http://myserver/_vti_bin/ListData.svc になります。  
  
4.  選択、 **OK**サービス参照をプロジェクトに追加するボタンをクリックし、既定のサービス名、[servicereference1] を使用します。  
  
5.  メニュー バーの **[ビルド]**、 **[ソリューションのビルド]**の順にクリックします。  
  
6.  SharePoint サービスに基づくプロジェクトを新しいデータ ソースを追加します。 メニュー バーで、これには、次のように選択します。**ビュー**、**その他のウィンドウ**、**データソース**です。  
  
     **データソース**ウィンドウは、すべてのタスク、お知らせ、予定表など、使用できる SharePoint リスト データを表示します。  
  
7.  Silverlight アプリケーションへのお知らせリストのデータを追加します。 「お知らせ」をドラッグすることができます、**データソース**ウィンドウから Silverlight デザイナーにします。  
  
     これには、SharePoint サイトのお知らせリストにバインドされているグリッド コントロールが作成されます。  
  
8.  Silverlight のページに合わせて、グリッド コントロールのサイズを変更します。  
  
9. MainPage.xaml のコード ファイル (MainPage.xaml.cs の Visual C# の場合) または Visual basic の MainPage.xaml.vb では、次の名前空間の参照を追加します。  
  
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
  
10. クラスの上部にある次の変数宣言を追加します。  
  
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
   
11. 置換、`UserControl_Loaded`を次の手順です。  
  
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
     置き換えてください、 *ServerName*プレース ホルダーを SharePoint を実行しているサーバーの名前。  
  
12. 次のエラー処理プロシージャを追加します。  
  
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
       
## <a name="modifying-the-silverlight-web-part"></a>Silverlight Web パーツを変更します。  
 Silverlight デバッグを有効にする Silverlight web パーツ プロジェクトでは、プロパティを変更します。  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Silverlight web パーツを変更するには  
  
1.  Silverlight web パーツ プロジェクトのショートカット メニューを開きます (**SLWebPartTest**) を選択し**プロパティ**です。  
  
2.  **プロパティ**ウィンドウで、選択、 **SharePoint**タブです。  
  
3.  選択されていない場合は、選択、 **Silverlight を有効にするには、(スクリプトのデバッグ) ではなくデバッグ**チェック ボックスをオンします。  
  
4.  プロジェクトを保存します。  
  
##  <a name="testing-the-silverlight-web-part"></a>Silverlight Web パーツのテスト  
 SharePoint リスト データは正しく表示されることを確認するように SharePoint では、新しい Silverlight web パーツをテストします。  
  
#### <a name="to-test-the-silverlight-web-part"></a>Silverlight web パーツをテストするには  
  
1.  ビルドおよび SharePoint ソリューションを実行するには、F5 キーを選択します。  
  
2.  SharePoint では、上、**サイトの操作**] メニューの [選択**新しいページ**です。  
  
3.  **新しいページ**ダイアログ ボックスなど、タイトルを入力**SL Web パーツのテスト**を選択し、**作成**ボタンをクリックします。  
  
4.  ページ デザイナー内で、**編集ツール** タブで、選択**挿入**です。  
  
5.  タブ ストリップで次のように選択します。 **Web パーツ**です。  
  
6.  **カテゴリ**ボックスで、選択、**カスタム**フォルダーです。  
  
7.  **Web パーツ**を一覧表示、Silverlight web パーツを選択し、、**追加**をデザイナーに web パーツを追加するボタンをクリックします。  
  
8.  加えた後に、追加機能をすべて使用する web ページに、選択、**ページ** タブをクリックして、**保存して閉じる &**ツール バー ボタンをクリックします。  
  
     Silverlight web パーツは、ここで、SharePoint サイトからのお知らせのデータを表示している必要があります。 既定では、ページは、SharePoint でサイトのページの一覧に格納されます。  
  
    > [!NOTE]  
    >  Silverlight のドメイン間でのデータにアクセスするときに、Silverlight は、web アプリケーションを利用するために使用されるセキュリティの脆弱性を防ぐ。 Silverlight でのリモート データにアクセスするときに問題が発生した場合は、次を参照してください。 [、サービス利用可能なドメインの境界を越えてを行う](http://go.microsoft.com/fwlink/?LinkId=223276)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [SharePoint ソリューションのパッケージの配置、発行、アップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
