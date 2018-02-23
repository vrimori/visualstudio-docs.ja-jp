---
title: "チュートリアル: IntelliTrace を使用して SharePoint アプリケーションのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: d9f3e5ae5997f7ae4f7c7f94bc61dc526404f144
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2018
---
# <a name="walkthrough-debugging-a-sharepoint-application-by-using-intellitrace"></a>チュートリアル: IntelliTrace を使用した SharePoint アプリケーションのデバッグ

IntelliTrace を使用すると、SharePoint ソリューション簡単にデバッグできます。 従来のデバッガーでは、現時点のソリューションを示すスナップショットだけを取得できました。 IntelliTrace を使用すると、ソリューション内で過去に発生したイベントと、そのイベントが発生したコンテキストをレビューし、コードに移動できます。

 このチュートリアルでは、展開済みのアプリケーションから IntelliTrace データを収集する Microsoft Monitoring Agent を使用して Visual Studio での SharePoint 2010 または SharePoint 2013 プロジェクトをデバッグする方法を示します。 そのデータを分析するには、Visual Studio Enterprise を使用する必要があります。 このプロジェクトには、フィーチャーがアクティブ化されたときに、タスク リストにタスクを、お知らせリストにお知らせを追加するフィーチャー レシーバーが組み込まれます。 フィーチャーが非アクティブ化されると、タスクは完了とマークされ、次のお知らせがお知らせリストに追加されます。 ただし、このプロシージャには、プロジェクトの正常な実行を妨げる論理エラーが含まれています。 IntelliTrace を使用することで、このエラーを見つけて修正できます。

 **適用されます:**このトピックの情報が Visual Studio で作成された SharePoint 2010 および SharePoint 2013 ソリューションに適用されます。

 このチュートリアルでは、次の作業について説明します。

- [フィーチャー レシーバーを作成します。](#BKMK_CreateReceiver)

- [フィーチャー レシーバーにコードを追加します。](#BKMK_AddCode)

- [プロジェクトをテストします。](#BKMK_Test1)

- [Microsoft Monitoring Agent を使用して IntelliTrace データを収集します。](#BKMK_CollectDiagnosticData)

- [デバッグおよび SharePoint ソリューションを修正](#BKMK_DebugSolution)

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- サポート対象エディションの Windows と SharePoint 参照してください[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。

- Visual Studio Enterprise.

## <a name="BKMK_CreateReceiver">フィーチャー レシーバーを作成します。</a>

最初に、フィーチャー レシーバーがある空の SharePoint プロジェクトを作成します。

1. SharePoint 2010 または SharePoint 2013 ソリューション プロジェクトを作成し、名前を付けます**IntelliTraceTest**です。

     **SharePoint カスタマイズ ウィザード**が表示されたら、プロジェクトとソリューションの信頼レベルの SharePoint サイトを指定できます。

2. 選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックします。

     IntelliTrace は、ファーム ソリューションに対してのみ動作します。

3. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**機能** ノードを選択し**フィーチャーの追加**です。

     Feature1.feature が表示されます。

4. クリックして、Feature1.feature のショートカット メニューを開き**イベント レシーバーの追加**コード モジュールをフィーチャーに追加します。

## <a name="BKMK_AddCode">フィーチャー レシーバーにコードを追加します。</a>

次に、フィーチャー レシーバー内の 2 つのメソッド (`FeatureActivated` と `FeatureDeactivating`) にコードを追加します。 これらのメソッドは、SharePoint でフィーチャーがアクティブ化または非アクティブ化されたときにトリガーされます。

1. `Feature1EventReceiver` クラスの一番上に次のコードを追加します。このコードは、SharePoint サイトとサブサイトを指定する変数を宣言します。

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

2. `FeatureActivated` メソッドを次のコードで置き換えます。

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

3. `FeatureDeactivating` メソッドを次のコードで置き換えます。

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

## <a name="BKMK_Test1">プロジェクトをテストします。</a>

コードがフィーチャー レシーバーに追加され、データ コレクターが実行されているので、SharePoint ソリューションを配置して実行し、それが正常に動作するかどうかをテストします。

> [!IMPORTANT]
> この例では、FeatureDeactivating イベント ハンドラーでエラーがスローされます。 このチュートリアルの後半で、データ コレクターが作成した .iTrace ファイルを使用してこのエラーを特定します。

1. ソリューションを SharePoint に配置し、ブラウザーで SharePoint サイトを開きます。

     フィーチャーは自動的にアクティブ化され、フィーチャー レシーバーによってお知らせとタスクが自動的に追加されます。

2. お知らせリストとタスク一覧の内容を表示します。

     という名前の新しいお知らせがお知らせリストに必要**Activated feature: IntelliTraceTest_Feature1**、タスク一覧、新しいタスクがという名前と**Deactivate feature: IntelliTraceTest_Feature1**です。 このいずれかがない場合は、フィーチャーがアクティブになっているかどうかを確認します。 アクティブになっていない場合は、アクティブにします。

3. 次の手順を実行して、フィーチャーを非アクティブにします。

    1. **サイトの操作**メニューを SharePoint では、**サイト設定**です。

    2. **サイトの操作**、選択、**サイト機能の管理**リンクします。

    3. 横に**IntelliTraceTest Feature1**、選択、 **Deactivate**ボタンをクリックします。

    4. [警告] ページで、選択、**このフィーチャーを非アクティブ**リンクします。

     FeatureDeactivating() イベント ハンドラーによってエラーがスローされます。

## <a name="BKMK_CollectDiagnosticData">Microsoft Monitoring Agent を使用して IntelliTrace データを収集します。</a>

SharePoint を実行しているシステムに Microsoft Monitoring Agent をインストールする場合は、IntelliTrace から返されるジェネリック情報よりも限定的なデータを使用して SharePoint ソリューションをデバッグすることができます。 エージェントは、PowerShell コマンドレットを使用して Visual Studio 外で動作し、SharePoint ソリューションの実行中にデバッグ情報をキャプチャします。

> [!NOTE]
> このセクションの構成情報は、この例に固有です。 その他の構成オプションの詳細については、次を参照してください。 [IntelliTrace スタンドアロン コレクターを使用して](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)です。

1. SharePoint を実行しているコンピューターで[Microsoft Monitoring Agent を設定し、ソリューションの監視を開始](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)です。

2. フィーチャーを非アクティブ化します。

    1. **サイトの操作**メニューを SharePoint では、**サイト設定**です。

    2. **サイトの操作**、選択、**サイト機能の管理**リンクします。

    3. 横に**IntelliTraceTest Feature1**、選択、 **Deactivate**ボタンをクリックします。

    4. [警告] ページで、選択、**このフィーチャーを非アクティブ**リンクします。

     エラーが発生します (この場合は、FeatureDeactivating() イベント ハンドラーでスローされたエラーが原因)。

3. PowerShell ウィンドウで、実行、 [Stop-webapplicationmonitoring](http://go.microsoft.com/fwlink/?LinkID=313687)コマンド .iTrace ファイルを作成、監視を停止し、SharePoint ソリューションを再起動します。

     **Stop-WebApplicationMonitoring**  *"\<SharePointSite>\\<SharePointAppName\>"*

## <a name="BKMK_DebugSolution">デバッグおよび SharePoint ソリューションを修正</a>

この時点で、Visual Studio で IntelliTrace ログ ファイルを表示し、SharePoint ソリューションのエラーを見つけて修正することができます。

1. Visual Studio で、\IntelliTraceLogs フォルダーにある .iTrace ファイルを開きます。

     **IntelliTrace の概要**ページが表示されます。 未処理の例外の領域で、SharePoint 相関 ID (GUID) が表示されます、エラーは処理されなかったため、 **Analysis**セクションです。 選択、**呼び出し履歴**場合は、エラーが発生した呼び出し履歴を表示するボタンをクリックします。

2. 選択、**例外のデバッグ**ボタンをクリックします。

     プロンプトが表示されたら、シンボル ファイルを読み込みます。 **IntelliTrace**ウィンドウで、この例外として強調表示されます。"スロー: 重大なエラーが発生しました!"です。

     [IntelliTrace] ウィンドウで、例外を選択して失敗したコードを表示します。

3. SharePoint ソリューションを開くと、コメント アウトまたは削除してエラーを修正、**スロー** featuredeactivating () プロシージャの上部にあるステートメントです。

4. Visual Studio でソリューションをリビルドし、SharePoint に再配置します。

5. 次の手順を実行して、フィーチャーを非アクティブにします。

    1. **サイトの操作**メニューを SharePoint では、**サイト設定**です。

    2. **サイトの操作**、選択、**サイト機能の管理**リンクします。

    3. 横に**IntelliTraceTest Feature1**、選択、 **Deactivate**ボタンをクリックします。

    4. [警告] ページで、選択、**このフィーチャーを非アクティブ**リンクします。

6. タスクの一覧を開き、いることを確認、**ステータス**の非アクティブ化タスクの値が「完了」とその**達成率**値は 100% です。

     コードは、適切に実行されています。

## <a name="see-also"></a>関連項目

[SharePoint コードの検証およびデバッグ](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[チュートリアル: 単体テストを使用した SharePoint コードの確認します。](https://msdn.microsoft.com/library/gg599006(v=vs.100).aspx)
