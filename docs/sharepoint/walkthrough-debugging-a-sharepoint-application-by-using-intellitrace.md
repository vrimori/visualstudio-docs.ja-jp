---
title: "チュートリアル: IntelliTrace を使用した SharePoint アプリケーションのデバッグ"
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
  - "IntelliTrace [Visual Studio での SharePoint 開発]"
  - "スタンドアロン データ コレクター"
  - "Visual Studio での SharePoint 開発、IntelliTrace"
  - "データ コレクター"
  - "IntelliTrace"
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# チュートリアル: IntelliTrace を使用した SharePoint アプリケーションのデバッグ
  IntelliTrace を使用すると、SharePoint ソリューション簡単にデバッグできます。  従来のデバッガーでは、現時点のソリューションを示すスナップショットだけを取得できました。  IntelliTrace を使用すると、ソリューション内で過去に発生したイベントと、そのイベントが発生したコンテキストをレビューし、コードに移動できます。  
  
 このチュートリアルでは、配置済みアプリケーションからの IntelliTrace データの収集に Microsoft Monitoring Agent を使用して、Visual Studio Ultimate で SharePoint 2010 プロジェクトまたは SharePoint 2013 プロジェクトをデバッグする方法について説明します。  このデータを分析するには、Visual Studio Ultimate を使用する必要があります。  このプロジェクトには、フィーチャーがアクティブ化されたときに、タスク リストにタスクを、お知らせリストにお知らせを追加するフィーチャー レシーバーが組み込まれます。  フィーチャーが非アクティブ化されると、タスクは完了とマークされ、次のお知らせがお知らせリストに追加されます。  ただし、このプロシージャには、プロジェクトの正常な実行を妨げる論理エラーが含まれています。  IntelliTrace を使用することで、このエラーを見つけて修正できます。  
  
 **対象:** このトピックの情報は、Visual Studio で作成された SharePoint 2010 ソリューションおよび SharePoint 2013 ソリューションに適用されます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   [フィーチャー レシーバーを作成する](#BKMK_CreateReceiver)  
  
-   [フィーチャー レシーバーにコードを追加する](#BKMK_AddCode)  
  
-   [プロジェクトをテストする](#BKMK_Test1)  
  
-   [Microsoft Monitoring Agent を使用して IntelliTrace データを収集する](#BKMK_CollectDiagnosticData)  
  
-   [SharePoint ソリューションをデバッグして修正する](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows と SharePoint。  「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio Ultimate。  
  
##  <a name="BKMK_CreateReceiver"></a> フィーチャー レシーバーを作成する  
 最初に、フィーチャー レシーバーがある空の SharePoint プロジェクトを作成します。  
  
#### フィーチャー レシーバーを作成するには  
  
1.  SharePoint 2010 ソリューションまたは SharePoint 2013 ソリューションのプロジェクトを作成し、IntelliTraceTest という名前を付けます。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。このウィザードで、プロジェクト用の SharePoint サイトとソリューションの信頼レベルの両方を指定できます。  
  
2.  **\[ファーム ソリューションとして配置する\]** をクリックし、**\[完了\]** をクリックします。  
  
     IntelliTrace は、ファーム ソリューションに対してのみ動作します。  
  
3.  **ソリューション エクスプローラー**で、**\[フィーチャー\]** ノードのショートカット メニューを開き、**\[フィーチャーの追加\]** を選択します。  
  
     Feature1.feature が表示されます。  
  
4.  Feature1.feature のショートカット メニューを開き、**\[イベント レシーバーの追加\]** を選択して、コード モジュールをフィーチャーに追加します。  
  
##  <a name="BKMK_AddCode"></a> フィーチャー レシーバーにコードを追加する  
 次に、フィーチャー レシーバー内の 2 つのメソッド \(`FeatureActivated` と `FeatureDeactivating`\) にコードを追加します。  これらのメソッドは、SharePoint でフィーチャーがアクティブ化または非アクティブ化されたときにトリガーされます。  
  
#### フィーチャー レシーバーにコードを追加するには  
  
1.  `Feature1EventReceiver` クラスの一番上に次のコードを追加します。このコードは、SharePoint サイトとサブサイトを指定する変数を宣言します。  
  
    ```vb  
    ' SharePoint site and subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site and subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
2.  `FeatureActivated` メソッドを次のコードで置き換えます。  
  
    ```vb  
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
                    Dim taskList As SPList = web.Lists("Tasks")  
  
                    ' Add an announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Add a task to the Task list.  
                    Dim newTask As SPListItem = taskList.Items.Add()  
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    newTask.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
                    SPList taskList = web.Lists["Tasks"];  
  
                    // Add an announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Add a task to the Task list.  
                    SPListItem newTask = taskList.Items.Add();  
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;  
                    newTask.Update();  
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
  
    }  
    ```  
  
3.  `FeatureDeactivating` メソッドを次のコードで置き換えます。  
  
    ```vb  
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)  
        ' The following line induces an error to demonstrate debugging.  
        ' Remove this line later for proper operation.  
        Throw New System.InvalidOperationException("Serious error occurred!")  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim taskList As SPList = web.Lists("Tasks")  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add an announcement that the feature was deactivated.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Find the task that the feature receiver added to the Task list when the  
                    ' feature was activated.  
                    Dim qry As New SPQuery()  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"  
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)  
  
                    For Each taskItem As SPListItem In taskItems  
                        ' Mark the task as complete.  
                        taskItem("PercentComplete") = 1  
                        taskItem("Status") = "Completed"  
                        taskItem.Update()  
                    Next  
                End Using  
  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)  
    {  
        // The following line induces an error to demonstrate debugging.  
        // Remove this line later for proper operation.  
        throw new System.InvalidOperationException("A serious error occurred!");   
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList taskList = web.Lists["Tasks"];  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add an announcement that the feature was deactivated.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Find the task that the feature receiver added to the Task list when the  
                    // feature was activated.  
                    SPQuery qry = new SPQuery();  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";  
                    SPListItemCollection taskItems = taskList.GetItems(qry);  
  
                    foreach (SPListItem taskItem in taskItems)  
                    {  
                        // Mark the task as complete.  
                        taskItem["PercentComplete"] = 1;  
                        taskItem["Status"] = "Completed";  
                        taskItem.Update();  
                    }  
                }  
            }  
  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
##  <a name="BKMK_Test1"></a> プロジェクトをテストする  
 コードがフィーチャー レシーバーに追加され、データ コレクターが実行されているので、SharePoint ソリューションを配置して実行し、それが正常に動作するかどうかをテストします。  
  
> [!IMPORTANT]  
>  この例では、FeatureDeactivating イベント ハンドラーでエラーがスローされます。  このチュートリアルの後半で、データ コレクターが作成した .iTrace ファイルを使用してこのエラーを特定します。  
  
#### プロジェクトをテストするには  
  
1.  ソリューションを SharePoint に配置し、ブラウザーで SharePoint サイトを開きます。  
  
     フィーチャーは自動的にアクティブ化され、フィーチャー レシーバーによってお知らせとタスクが自動的に追加されます。  
  
2.  お知らせリストとタスク一覧の内容を表示します。  
  
     お知らせリストには **Activated feature: IntelliTraceTest\_Feature1** という名前の新しいお知らせがあり、タスク一覧には **Deactivate feature: IntelliTraceTest\_Feature1** という名前の新しいタスクがあります。  このいずれかがない場合は、フィーチャーがアクティブになっているかどうかを確認します。  アクティブになっていない場合は、アクティブにします。  
  
3.  次の手順を実行して、フィーチャーを非アクティブにします。  
  
    1.  SharePoint の **\[サイトの操作\]** メニューで、**\[サイトの設定\]** を選択します。  
  
    2.  **\[サイトの操作\]** で、**\[サイトのフィーチャーの管理\]** リンクをクリックします。  
  
    3.  **\[IntelliTraceTest Feature1\]** の横にある **\[非アクティブ化\]** をクリックします。  
  
    4.  警告ページで、**\[この機能を非アクティブ化\]** リンクをクリックします。  
  
     FeatureDeactivating\(\) イベント ハンドラーによってエラーがスローされます。  
  
##  <a name="BKMK_CollectDiagnosticData"></a> Microsoft Monitoring Agent を使用して IntelliTrace データを収集する  
 SharePoint が実行されているシステムに Microsoft Monitoring Agent をインストールすると、IntelliTrace から返されるジェネリック情報よりも具体的なデータを使用して、SharePoint ソリューションをデバッグできます。  エージェントは、PowerShell コマンドレットを使用して Visual Studio 外で動作し、SharePoint ソリューションの実行中にデバッグ情報をキャプチャします。  
  
> [!NOTE]  
>  このセクションの構成情報は、この例に固有です。  その他の構成オプションの詳細については、「[IntelliTrace スタンドアロン コレクターを使用する](../debugger/using-the-intellitrace-stand-alone-collector.md)」を参照してください。  
  
1.  SharePoint を実行しているコンピューターで、[Microsoft Monitoring Agent を設定し、ソリューションの監視を開始します](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
2.  フィーチャーを非アクティブ化します。  
  
    1.  SharePoint の **\[サイトの操作\]** メニューで、**\[サイトの設定\]** を選択します。  
  
    2.  **\[サイトの操作\]** で、**\[サイトのフィーチャーの管理\]** リンクをクリックします。  
  
    3.  **\[IntelliTraceTest Feature1\]** の横にある **\[非アクティブ化\]** をクリックします。  
  
    4.  警告ページで、**\[この機能を非アクティブ化\]** リンクをクリックします。  
  
     エラーが発生します \(この場合は、FeatureDeactivating\(\) イベント ハンドラーでスローされたエラーが原因\)。  
  
3.  PowerShell ウィンドウで [Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) コマンドを実行することにより、.iTrace ファイルを作成し、監視を停止して、SharePoint ソリューションを再起動します。  
  
     **Stop\-WebApplicationMonitoring**  *"\<SharePointSite\>\\\<SharePointAppName\>"*  
  
##  <a name="BKMK_DebugSolution"></a> SharePoint ソリューションをデバッグして修正する  
 この時点で、Visual Studio で IntelliTrace ログ ファイルを表示し、SharePoint ソリューションのエラーを見つけて修正することができます。  
  
#### SharePoint ソリューションをデバッグして修正するには  
  
1.  Visual Studio で、\\IntelliTraceLogs フォルダーにある .iTrace ファイルを開きます。  
  
     **\[IntelliTrace の概要\]** ページが表示されます。  エラーは処理されなかったので、SharePoint の相関 ID \(GUID\) が **\[分析\]** セクションのハンドルされない例外領域に表示されます。  エラーが発生した呼び出し履歴を表示するには、**\[呼び出し履歴\]** をクリックします。  
  
2.  **\[例外のデバッグ\]** をクリックします。  
  
     プロンプトが表示されたら、シンボル ファイルを読み込みます。  **\[IntelliTrace\]** ウィンドウで、例外が "スロー: 重大なエラーが発生しました" というテキストで強調表示されます。  
  
     \[IntelliTrace\] ウィンドウで、例外を選択して失敗したコードを表示します。  
  
3.  SharePoint ソリューションを開き、FeatureDeactivating \(\) プロシージャの一番上にある **throw** ステートメントをコメント アウトまたは削除してエラーを修正します。  
  
4.  Visual Studio でソリューションをリビルドし、SharePoint に再配置します。  
  
5.  次の手順を実行して、フィーチャーを非アクティブにします。  
  
    1.  SharePoint の **\[サイトの操作\]** メニューで、**\[サイトの設定\]** を選択します。  
  
    2.  **\[サイトの操作\]** で、**\[サイトのフィーチャーの管理\]** リンクをクリックします。  
  
    3.  **\[IntelliTraceTest Feature1\]** の横にある **\[非アクティブ化\]** をクリックします。  
  
    4.  警告ページで、**\[この機能を非アクティブ化\]** リンクをクリックします。  
  
6.  タスク一覧を開き、非アクティブ化タスクの **\[ステータス\]** が \[完了\] で、**\[達成率\]** が \[100%\] であることを確認します。  
  
     コードは、適切に実行されています。  
  
## 参照  
 [SharePoint コードの検証およびデバッグ](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [IntelliTrace の使用](../debugger/intellitrace.md)   
 [チュートリアル: 単体テストを使用して SharePoint コードを検証する](http://msdn.microsoft.com/ja-jp/3d2c4aaf-3cb5-4825-b21b-f10222abe818)  
  
  