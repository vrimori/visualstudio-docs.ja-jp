---
title: "チュートリアル: SharePoint アプリケーションのプロファイリング |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
ms.assetid: 0b19d4b7-5fcc-42a2-b411-96eccd00137f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a3c152640963da1414c34770fff68645e33098ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-profiling-a-sharepoint-application"></a>チュートリアル: SharePoint アプリケーションのプロファイリング
  このチュートリアルでは、Visual Studio のプロファイル ツールを使用し、SharePoint アプリケーションのパフォーマンスを最適化する方法について説明します。 アプリケーション例は SharePoint フィーチャー イベント レシーバーで、これにはフィーチャー イベント レシーバーのパフォーマンスを低下させるアイドル ループが含まれています。 Visual Studio プロファイラーでは、見つけてとも呼ばれる、プロジェクトの最も負荷の高い (最も遅い) 部分を排除することができます、*ホット パス*です。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   [機能とフィーチャー イベント レシーバーの追加](#BKMK_AddFtrandFtrEvntReceiver)です。  
  
-   [構成および SharePoint アプリケーションを展開する](#BKMK_ConfigSharePointApp)です。  
  
-   [SharePoint アプリケーションの実行](#BKMK_RunSPApp)です。  
  
-   [表示とプロファイルの結果を解釈](#BKMK_ViewResults)です。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]。  
  
## <a name="creating-a-sharepoint-project"></a>SharePoint プロジェクトを作成する  
 まずは、SharePoint プロジェクトを作成します。  
  
#### <a name="to-create-a-sharepoint-project"></a>SharePoint プロジェクトを作成するには  
  
1.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し、 **2010**ノード。  
  
3.  [テンプレート] ペインで、選択、 **SharePoint 2010 プロジェクト**テンプレート。  
  
4.  **名前**ボックスに、入力**ProfileTest**を選択し、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **デバッグのサイトとセキュリティ レベルを指定して**ページで、サイト定義をデバッグする SharePoint サーバー サイトの URL を入力するか、既定の場所を使用して (http://*システム名*/).  
  
6.  **この SharePoint ソリューションの信頼レベルは何ですか?**セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。  
  
     現時点では、ファーム ソリューションのプロファイルのみを実行できます。 サンド ボックス ソリューションとファーム ソリューションの詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
7.  選択、**完了**ボタンをクリックします。 プロジェクトが表示されます**ソリューション エクスプ ローラー**です。  
  
##  <a name="BKMK_AddFtrandFtrEvntReceiver"></a>機能とフィーチャー イベント レシーバーの追加  
 次に、フィーチャーを、そのイベント レシーバーと共にプロジェクトに追加します。 このイベント レシーバーには、プロファイル対象のコードが含まれます。  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>機能とフィーチャー イベント レシーバーを追加するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**機能** ノードを選択**フィーチャーの追加**は既定値の名前をそのままと**Feature1**.  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **Feature1**を選択し**イベント レシーバーの追加**です。  
  
     これにより、いくつかのコメント アウトされたイベント ハンドラーを持つコード ファイルが機能に追加され、編集のためにファイルが開かれます。  
  
3.  イベント レシーバー クラスに、次の変数宣言を追加します。  
  
    ```vb  
    ' SharePoint site/subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site/subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
4.  `FeatureActivated` プロシージャを次のコードに置き換えます。  
  
    ```vb  
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add a new announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    ' Waste some time.  
                    TimeCounter()  
                    ' Update the list.  
                    listItem.Update()  
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
  
                    // Add a new announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +   
    DateTime.Now.ToString();  
                    // Waste some time.  
                    TimeCounter();  
                    // Update the list.  
                    listItem.Update();                          
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
5.  次の手順を追加、`FeatureActivated`プロシージャです。  
  
    ```vb  
  
    Public Sub TimeCounter()  
        Dim result As Integer  
        For i As Integer = 0 To 99999  
            For j As Integer = 0 To 9999  
                result = i * j  
            Next j  
        Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void TimeCounter()  
    {  
        for (int i = 0; i < 100000; i++)  
        {  
            for (int j = 0; j < 10000; j++)  
            {  
                int result = i * j;  
            }  
        }  
    }  
    ```  
  
6.  **ソリューション エクスプ ローラー**、プロジェクトのショートカット メニューを開きます (**ProfileTest**) を選択し**プロパティ**です。  
  
7.  **プロパティ** ダイアログ ボックスで、選択、 **SharePoint**タブです。  
  
8.  **アクティブな配置構成**一覧で、選択**アクティブ化しない**です。  
  
     この配置構成を選択することにより、後で SharePoint 内から手動でフィーチャーをアクティブ化できます。  
  
9. プロジェクトを保存します。  
  
##  <a name="BKMK_ConfigSharePointApp"></a>構成および SharePoint アプリケーションを展開します。  
 SharePoint プロジェクトの準備ができたので、それを構成し、SharePoint サーバーに配置します。  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>SharePoint アプリケーションを構成し、配置するには  
  
1.  **分析**] メニューの [選択**パフォーマンス ウィザードの起動**です。  
  
2.  いずれかのページで、**パフォーマンス ウィザード**、プロファイリングは任意のメソッドのままにして**CPU サンプリング**を選択し、 **[次へ]**ボタンをクリックします。  
  
     他のプロファイル方法は、より高度なプロファイルを行う場合に使用できます。 詳細については、「[パフォーマンス収集方法について](/visualstudio/profiling/understanding-performance-collection-methods)」を参照してください。  
  
3.  2 ページ目で、**パフォーマンス ウィザード**、プロファイルをターゲットとしてのままにして**ProfileTest**を選択し、 **[次へ]**ボタンをクリックします。  
  
     ソリューションに複数のプロジェクトがある場合は、この一覧に表示されます。  
  
4.  3 ページ目で、**パフォーマンス ウィザード**チェック ボックスをオフ、**階層相互作用のプロファイリングを有効にする**チェック ボックスをオンにして、 **[次へ]**ボタンをクリックします。  
  
     階層の相互作用のプロファイル (TIP) 機能は、データベースを照会するアプリケーションのパフォーマンスの測定や、Web ページが要求された回数の表示に便利です。 そのようなデータはこの例では不要なため、この機能は有効にしません。  
  
5.  4 ページ目で、**パフォーマンス ウィザード**のままにして、**ウィザードの完了後にプロファイルを起動して**チェック ボックスをオンにして、**完了**ボタンをクリックします。  
  
     ウィザードがサーバーでアプリケーションのプロファイリングを有効に、表示、**パフォーマンス エクスプ ローラー**ウィンドウ、およびビルド、配置、および SharePoint アプリケーションを実行します。  
  
##  <a name="BKMK_RunSPApp"></a>SharePoint アプリケーションの実行  
 `FeatureActivation` イベント コードの実行をトリガーし、SharePoint 内の機能をアクティブ化します。  
  
#### <a name="to-run-the-sharepoint-application"></a>SharePoint アプリケーションを実行するには  
  
1.  SharePoint では、開く、**サイトの操作** メニューを選択し**サイト設定**です。  
  
2.  **サイトの操作**一覧で、選択、**サイト機能の管理**リンクします。  
  
3.  **機能**一覧で、選択、 **Activate**横に**ProfileTest Feature1**です。  
  
     この操作を実行すると、`FeatureActivated` 関数内でアイドル ループが呼び出されることによって一時停止が発生します。  
  
4.  **クイック起動**バーで、**を一覧表示**し、**を一覧表示**一覧で、選択**お知らせ**です。  
  
     機能がアクティブになったことを示す新しいお知らせが一覧に追加されていることを確認します。  
  
5.  SharePoint サイトを閉じます。  
  
     SharePoint を閉じると、プロファイラーによって作成およびサンプル プロファイル レポートを表示され、.vsp ファイルとして保存、 **ProfileTest**プロジェクトのフォルダーです。  
  
##  <a name="BKMK_ViewResults"></a>表示とプロファイルの結果の解釈  
 SharePoint アプリケーションを実行してプロファイルを行ったので、次はテスト結果を表示します。  
  
#### <a name="to-view-and-interpret-the-profiling-results"></a>プロファイル結果を表示し、解釈するには  
  
1.  **個別作業が一番を実行している関数**セクション サンプル プロファイル レポートのことに注意して`TimeCounter`は一覧の先頭付近にあります。  
  
     この場所は、`TimeCounter` がサンプル数の最も多い関数の 1 つ、つまり、アプリケーション内で最大のパフォーマンス ボトルネックの 1 つであることを示しています。 ただし、これは驚くような状況はではありません。デモンストレーションのために、意図してこのようにデザインされたものであるからです。  
  
2.  **個別作業が一番を実行している関数**セクションで、選択、`ProcessRequest`のコスト配分を表示するリンク、`ProcessRequest`関数。  
  
     **関数と呼ばれる**については、「 `ProcessRequest`、ことに注意して、 **FeatureActiviated**関数が表示されている最も高価な関数が呼び出されます。  
  
3.  **関数と呼ばれる**セクションで、選択、 **FeatureActivated**ボタンをクリックします。  
  
     **関数と呼ばれる**については、「 **FeatureActivated**、`TimeCounter`関数が表示されている最も高価な関数が呼び出されます。 **関数コード ビュー**  ウィンドウで、強調表示されたコード (`TimeCounter`) ホット スポットであり、修正が必要なことを示します。  
  
4.  サンプル プロファイル レポートを閉じます。  
  
     レポートを表示する、いつでもでも、.vsp ファイルを開く、**パフォーマンス エクスプ ローラー**ウィンドウです。  
  
## <a name="fixing-the-code-and-reprofiling-the-application"></a>コードの修正とアプリケーションの再プロファイル  
 SharePoint アプリケーション内のホットスポット関数を特定したので、次はこれを修正します。  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>コードを修正し、アプリケーションを再プロファイルするには  
  
1.  フィーチャー イベント レシーバーのコード内で、`FeatureActivated` の `TimeCounter` メソッドの呼び出しをコメント アウトし、これが呼び出されないようにします。  
  
2.  プロジェクトを保存します。  
  
3.  **パフォーマンス エクスプ ローラー**ターゲット フォルダーを開きを選択し、 **ProfileTest**ノード。  
  
4.  **パフォーマンス エクスプ ローラー**ツールバーで、**アクション** タブで、選択、**プロファイリングの開始**ボタンをクリックします。  
  
     任意のアプリケーションを再プロファイル前にプロファイルのプロパティを変更するを選択する場合、**パフォーマンス ウィザードの起動**代わりにボタンをクリックします。  
  
5.  指示に従って、 **SharePoint アプリケーションの実行**このトピックの前のセクションです。  
  
     これで、アイドル ループへの呼び出しが削除されたため、機能のアクティブ化がより高速になりました。 このことは、サンプル プロファイル レポートに反映されます。  
  
## <a name="see-also"></a>参照  
 [パフォーマンス エクスプローラー](/visualstudio/profiling/performance-explorer)   
 [パフォーマンス セッションの概要](/visualstudio/profiling/performance-session-overview)   
 [パフォーマンス プロファイリングのビギナーズ ガイド](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Visual Studio プロファイラーでアプリケーションのボトルネックを見つける](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
  