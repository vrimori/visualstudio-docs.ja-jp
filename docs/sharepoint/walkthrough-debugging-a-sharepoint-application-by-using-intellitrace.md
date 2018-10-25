---
title: 'チュートリアル: IntelliTrace を使用して SharePoint アプリケーションのデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c617bb84a3d7aad10769ef5dbceec657e49aa21
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927347"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>チュートリアル: IntelliTrace を使用して SharePoint アプリケーションをデバッグします。

IntelliTrace を使用すると、SharePoint ソリューション簡単にデバッグできます。 従来のデバッガーでは、現時点のソリューションを示すスナップショットだけを取得できました。 IntelliTrace を使用すると、ソリューション内で過去に発生したイベントと、そのイベントが発生したコンテキストをレビューし、コードに移動できます。

 このチュートリアルでは、デプロイされたアプリケーションから IntelliTrace データを収集する Microsoft Monitoring Agent を使用して Visual Studio で SharePoint 2010 または SharePoint 2013 プロジェクトをデバッグする方法を示します。 そのデータを分析するには、Visual Studio Enterprise を使用する必要があります。 このプロジェクトには、フィーチャーがアクティブ化されたときに、タスク リストにタスクを、お知らせリストにお知らせを追加するフィーチャー レシーバーが組み込まれます。 フィーチャーが非アクティブ化されると、タスクは完了とマークされ、次のお知らせがお知らせリストに追加されます。 ただし、このプロシージャには、プロジェクトの正常な実行を妨げる論理エラーが含まれています。 IntelliTrace を使用することで、このエラーを見つけて修正できます。

 **適用対象:** このトピックの情報は、Visual Studio で作成された SharePoint 2010 および SharePoint 2013 ソリューションに適用されます。

 このチュートリアルでは、次の作業について説明します。

- [フィーチャー レシーバーを作成します。](#BKMK_CreateReceiver)

- [フィーチャー レシーバーにコードを追加します。](#BKMK_AddCode)

- [プロジェクトをテストします。](#BKMK_Test1)

- [Microsoft Monitoring Agent を使用して IntelliTrace データを収集します。](#BKMK_CollectDiagnosticData)

- [デバッグし、SharePoint ソリューションを修正](#BKMK_DebugSolution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- サポート対象エディションの Windows と SharePoint

- Visual Studio Enterprise。

## <a name="create-a-feature-receiver"></a>フィーチャー レシーバーを作成します。

最初に、フィーチャー レシーバーがある空の SharePoint プロジェクトを作成します。

1. SharePoint 2010 または SharePoint 2013 ソリューション プロジェクトを作成し、名前**IntelliTraceTest**します。

     **SharePoint カスタマイズ ウィザード**が表示されたら、プロジェクトとソリューションの信頼レベルの SharePoint サイトを指定できます。

2. 選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックします。

     IntelliTrace は、ファーム ソリューションに対してのみ動作します。

3. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**機能**ノードを選び、**機能の追加**します。

     *Feature1.feature*が表示されます。

4. 、Feature1.feature のショートカット メニューを開き、選択し、**イベント レシーバーの追加**機能にコード モジュールを追加します。

## <a name="add-code-to-the-feature-receiver"></a>フィーチャー レシーバーにコードを追加します。

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

## <a name="test-the-project"></a>プロジェクトをテストします。

コードがフィーチャー レシーバーに追加され、データ コレクターが実行されているので、SharePoint ソリューションを配置して実行し、それが正常に動作するかどうかをテストします。

> [!IMPORTANT]
> この例では、FeatureDeactivating イベント ハンドラーでエラーがスローされます。 このチュートリアルの後半で、データ コレクターが作成した .iTrace ファイルを使用してこのエラーを特定します。

1. ソリューションを SharePoint に配置し、ブラウザーで SharePoint サイトを開きます。

     フィーチャーは自動的にアクティブ化され、フィーチャー レシーバーによってお知らせとタスクが自動的に追加されます。

2. お知らせリストとタスク一覧の内容を表示します。

     という新しいお知らせをお知らせリストがあります**Activated feature: IntelliTraceTest_Feature1**、という新しいタスクがタスク一覧**Deactivate feature: IntelliTraceTest_Feature1**します。 このいずれかがない場合は、フィーチャーがアクティブになっているかどうかを確認します。 アクティブになっていない場合は、アクティブにします。

3. 次の手順を実行して、フィーチャーを非アクティブにします。

   1. **サイトの操作**SharePoint では、メニュー**サイト設定**します。

   2. **サイトの操作**、選択、**サイト機能の管理**リンク。

   3. 横に**IntelliTraceTest Feature1**、選択、**非アクティブ化**ボタンをクリックします。

   4. [警告] ページで、選択、**この機能を非アクティブ化**リンク。

      FeatureDeactivating() イベント ハンドラーによってエラーがスローされます。

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Microsoft Monitoring Agent を使用して IntelliTrace データを収集します。

SharePoint を実行しているシステムに Microsoft Monitoring Agent をインストールする場合は、IntelliTrace から返されるジェネリック情報よりも具体的であるデータを使用して SharePoint ソリューションをデバッグできます。 エージェントは、PowerShell コマンドレットを使用して Visual Studio 外で動作し、SharePoint ソリューションの実行中にデバッグ情報をキャプチャします。

> [!NOTE]
> このセクションの構成情報は、この例に固有です。 その他の構成オプションの詳細については、次を参照してください。 [IntelliTrace スタンドアロン コレクターを使用して](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)します。

1. SharePoint を実行しているコンピューターで[Microsoft Monitoring Agent を設定し、ソリューションの監視を開始](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)します。

2. フィーチャーを非アクティブ化します。

   1. **サイトの操作**SharePoint では、メニュー**サイト設定**します。

   2. **サイトの操作**、選択、**サイト機能の管理**リンク。

   3. 横に**IntelliTraceTest Feature1**、選択、**非アクティブ化**ボタンをクリックします。

   4. [警告] ページで、選択、**この機能を非アクティブ化**リンク。

      エラーが発生します (この場合は、FeatureDeactivating() イベント ハンドラーでスローされたエラーが原因)。

3. PowerShell ウィンドウで実行、 [Stop-webapplicationmonitoring](http://go.microsoft.com/fwlink/?LinkID=313687)コマンドを .iTrace ファイルを作成、監視を停止し、SharePoint ソリューションを再起動します。

     **Stop-WebApplicationMonitoring**  *"\<SharePointSite>\\<SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>デバッグし、SharePoint ソリューションを修正

この時点で、Visual Studio で IntelliTrace ログ ファイルを表示し、SharePoint ソリューションのエラーを見つけて修正することができます。

1. Visual Studio で、\IntelliTraceLogs フォルダーにある .iTrace ファイルを開きます。

     **IntelliTrace の概要**ページが表示されます。 ハンドルされない例外領域に SharePoint 相関 ID (GUID) が表示されます、エラーは処理されなかったため、 **Analysis**セクション。 選択、**呼び出し履歴**場合は、エラーが発生した呼び出し履歴を表示するボタンをクリックします。

2. 選択、**例外のデバッグ**ボタンをクリックします。

     プロンプトが表示されたら、シンボル ファイルを読み込みます。 **IntelliTrace**ウィンドウで、例外として強調表示されます。"スロー: 重大なエラーが発生しました!"。

     [IntelliTrace] ウィンドウで、例外を選択して失敗したコードを表示します。

3. SharePoint ソリューションを開くと、コメント アウトまたは削除してエラーを修正、**スロー** featuredeactivating () プロシージャの上部にあるステートメント。

4. Visual Studio でソリューションをリビルドし、SharePoint に再配置します。

5. 次の手順を実行して、フィーチャーを非アクティブにします。

    1. **サイトの操作**SharePoint では、メニュー**サイト設定**します。

    2. **サイトの操作**、選択、**サイト機能の管理**リンク。

    3. 横に**IntelliTraceTest Feature1**、選択、**非アクティブ化**ボタンをクリックします。

    4. [警告] ページで、選択、**この機能を非アクティブ化**リンク。

6. タスクの一覧を開き、いることを確認、**状態**非アクティブ化タスクの値が「完了」とその **% 完了**値は 100% です。

     コードは、適切に実行されています。

## <a name="see-also"></a>関連項目

[検証し、SharePoint コードのデバッグ](../sharepoint/verifying-and-debugging-sharepoint-code.md)  
[IntelliTrace](/visualstudio/debugger/intellitrace)  
[チュートリアル: 単体テストを使用した SharePoint コードの確認します。](https://msdn.microsoft.com/library/gg599006(v=vs.100).aspx)
