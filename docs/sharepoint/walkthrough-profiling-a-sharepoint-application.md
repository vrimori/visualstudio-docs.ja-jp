---
title: "Walkthrough: Profiling a SharePoint Application | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, profiling"
  - "performance testing [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, performance testing"
  - "profiling [SharePoint development in Visual Studio]"
ms.assetid: 0b19d4b7-5fcc-42a2-b411-96eccd00137f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Walkthrough: Profiling a SharePoint Application
  このチュートリアルでは、Visual Studio のプロファイル ツールを使用し、SharePoint アプリケーションのパフォーマンスを最適化する方法について説明します。  アプリケーション例は SharePoint フィーチャー イベント レシーバーで、これにはフィーチャー イベント レシーバーのパフォーマンスを低下させるアイドル ループが含まれています。  Visual Studio プロファイラーを使用すると、*ホット パス*とも呼ばれるプロジェクトの最も負荷のかかる \(実行速度が最も遅い\) 部分を特定し、取り除くことができます。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   [機能とフィーチャー イベント レシーバーの追加](#BKMK_AddFtrandFtrEvntReceiver)。  
  
-   [SharePoint アプリケーションの構成と配置](#BKMK_ConfigSharePointApp)。  
  
-   [SharePoint アプリケーションの実行](#BKMK_RunSPApp)。  
  
-   [プロファイル結果の表示と解釈](#BKMK_ViewResults)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]。  
  
## SharePoint プロジェクトを作成する  
 まずは、SharePoint プロジェクトを作成します。  
  
#### SharePoint プロジェクトを作成するには  
  
1.  メニュー バーで **\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順に選択して、**\[新しいプロジェクト\]** ダイアログ ボックスを表示します。  
  
2.  **\[Visual C\#\]** または **\[Visual Basic\]** の **\[SharePoint\]** ノードを展開し、**\[2010\]** ノードをクリックします。  
  
3.  \[テンプレート\] ペインで、**\[SharePoint 2010 プロジェクト\]** テンプレートをクリックします。  
  
4.  **\[名前\]** ボックスに「ProfileTest」と入力し、**\[OK\]** をクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **\[デバッグのサイトとセキュリティ レベルの指定\]** ページで、サイト定義をデバッグする SharePoint サーバー サイトの URL を入力するか、既定の場所 \(http:\/\/*システム名*\/\) を使用します。  
  
6.  **\[この SharePoint ソリューションの信頼レベル\]** セクションで **\[ファーム ソリューションとして配置する\]** を選択します。  
  
     現時点では、ファーム ソリューションのプロファイルのみを実行できます。  サンドボックス ソリューションとファーム ソリューションの比較の詳細については、「[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)」を参照してください。  
  
7.  **\[完了\]** をクリックします。  **ソリューション エクスプローラー**にプロジェクトが表示されます。  
  
##  <a name="BKMK_AddFtrandFtrEvntReceiver"></a> 機能とフィーチャー イベント レシーバーの追加  
 次に、機能を、そのイベント レシーバーと共にプロジェクトに追加します。  このイベント レシーバーには、プロファイル対象のコードが含まれます。  
  
#### 機能とフィーチャー イベント レシーバーを追加するには  
  
1.  **ソリューション エクスプローラー**で **\[フィーチャー\]** ノードのショートカット メニューを開き、**\[フィーチャーの追加\]** をクリックします。名前は既定値の **\[Feature1\]** のままにします。  
  
2.  **ソリューション エクスプローラー**で **\[Feature1\]** のショートカット メニューを開き、**\[イベント レシーバーの追加\]** をクリックします。  
  
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
  
5.  次のプロシージャを `FeatureActivated` プロシージャの下に追加します。  
  
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
  
6.  **ソリューション エクスプローラー**で、プロジェクト \(**ProfileTest**\) のショートカット メニューを開き、**\[プロパティ\]** をクリックします。  
  
7.  **\[プロパティ\]** ダイアログ ボックスで、**\[SharePoint\]** タブをクリックします。  
  
8.  **\[アクティブな配置構成\]** ボックスの一覧の **\[アクティブ化なし\]** をクリックします。  
  
     この配置構成を選択することにより、後で SharePoint 内から手動で機能をアクティブ化できます。  
  
9. プロジェクトを保存します。  
  
##  <a name="BKMK_ConfigSharePointApp"></a> SharePoint アプリケーションの構成と配置  
 SharePoint プロジェクトの準備ができたので、それを構成し、SharePoint サーバーに配置します。  
  
#### SharePoint アプリケーションを構成し、配置するには  
  
1.  **\[分析\]** メニューの **\[パフォーマンス ウィザードの起動\]** をクリックします。  
  
2.  **パフォーマンス ウィザード**の最初のページで、プロファイル方法を **\[CPU サンプリング\]** のままにし、**\[次へ\]** をクリックします。  
  
     他のプロファイル方法は、より高度なプロファイルを行う場合に使用できます。  詳細については、「[プロファイル方法について](../profiling/understanding-performance-collection-methods.md)」を参照してください。  
  
3.  **パフォーマンス ウィザード**の 2 ページ目で、プロファイルのターゲットを **\[ProfileTest\]** のままにし、**\[次へ\]** をクリックします。  
  
     ソリューションに複数のプロジェクトがある場合は、この一覧に表示されます。  
  
4.  **パフォーマンス ウィザード**の 3 ページ目で、**\[階層の相互作用のプロファイルを有効にする\]** チェック ボックスをオフにし、**\[次へ\]** をクリックします。  
  
     階層の相互作用のプロファイル \(TIP\) 機能は、データベースを照会するアプリケーションのパフォーマンスの測定や、Web ページが要求された回数の表示に便利です。  そのようなデータはこの例では不要なため、この機能は有効にしません。  
  
5.  **パフォーマンス ウィザード**の 4 ページ目で、**\[ウィザードの完了後にプロファイルを起動する\]** チェック ボックスをオンのままにし、**\[完了\]** をクリックします。  
  
     ウィザードによって、サーバーでのアプリケーションのプロファイルが有効になり、**\[パフォーマンス エクスプローラー\]** ウィンドウが表示され、SharePoint アプリケーションのビルド、配置、および実行が行われます。  
  
##  <a name="BKMK_RunSPApp"></a> SharePoint アプリケーションの実行  
 `FeatureActivation` イベント コードの実行をトリガーし、SharePoint 内の機能をアクティブ化します。  
  
#### SharePoint アプリケーションを実行するには  
  
1.  SharePoint で、**\[サイトの操作\]** メニューを開き、**\[サイトの設定\]** をクリックします。  
  
2.  **\[サイトの操作\]** ボックスの一覧の **\[サイト機能の管理\]** をクリックします。  
  
3.  **\[機能\]** の一覧で、**ProfileTest Feature1** の横にある **\[アクティブ化\]** をクリックします。  
  
     この操作を実行すると、`FeatureActivated` 関数内でアイドル ループが呼び出されることによって一時停止が発生します。  
  
4.  **\[サイド リンク バー\]** の **\[リスト\]** をクリックし、**\[リスト\]** ボックスの一覧の **\[お知らせ\]** をクリックします。  
  
     機能がアクティブになったことを示す新しいお知らせが一覧に追加されていることを確認します。  
  
5.  SharePoint サイトを閉じます。  
  
     SharePoint を閉じると、プロファイラーによってサンプル プロファイル レポートが作成されて表示され、.vsp ファイルとして **ProfileTest** プロジェクトのフォルダーに保存されます。  
  
##  <a name="BKMK_ViewResults"></a> プロファイル結果の表示と解釈  
 SharePoint アプリケーションを実行してプロファイルを行ったので、次はテスト結果を表示します。  
  
#### プロファイル結果を表示し、解釈するには  
  
1.  サンプル プロファイル レポートの **\[最も頻繁に個別の作業を実行している関数\]** セクションでは、`TimeCounter` が一覧の最上部近くにあります。  
  
     この場所は、`TimeCounter` がサンプル数の最も多い関数の 1 つ、つまり、アプリケーション内で最大のパフォーマンス ボトルネックの 1 つであることを示しています。  ただし、これは驚くような状況はではありません。デモンストレーションのために、意図してこのようにデザインされたものであるからです。  
  
2.  **\[最も頻繁に個別の作業を実行している関数\]** セクションで `ProcessRequest` をクリックし、`ProcessRequest` 関数のコスト配分を表示します。  
  
     `ProcessRequest` の **\[呼び出される関数\]** セクションに、**FeatureActiviated** 関数が最も負荷の高い、呼び出される関数として表示されます。  
  
3.  **\[呼び出される関数\]** セクションで、**\[FeatureActivated\]** をクリックします。  
  
     **FeatureActivated** の **\[呼び出される関数\]** セクションに、`TimeCounter` 関数が最も負荷の高い、呼び出される関数として表示されます。  **\[関数コード ビュー\]** ペインの強調表示されたコード \(`TimeCounter`\) はホットスポットであり、修正が必要な場所を示しています。  
  
4.  サンプル プロファイル レポートを閉じます。  
  
     レポートは、**\[パフォーマンス エクスプローラー\]** ウィンドウの .vsp ファイルを開くと、いつでも再確認できます。  
  
## コードの修正とアプリケーションの再プロファイル  
 SharePoint アプリケーション内のホットスポット関数を特定したので、次はこれを修正します。  
  
#### コードを修正し、アプリケーションを再プロファイルするには  
  
1.  フィーチャー イベント レシーバーのコード内で、`FeatureActivated` の `TimeCounter` メソッドの呼び出しをコメント アウトし、これが呼び出されないようにします。  
  
2.  プロジェクトを保存します。  
  
3.  **\[パフォーマンス エクスプローラー\]** で \[ターゲット\] フォルダーを開き、**\[ProfileTest\]** ノードをクリックします。  
  
4.  **\[アクション\]** タブの **\[パフォーマンス エクスプローラー\]** ツール バーで、**\[プロファイルの開始\]** をクリックします。  
  
     アプリケーションの再プロファイル前にいずれかのプロファイル プロパティを変更する場合は、代わりに **\[パフォーマンス ウィザードの起動\]** をクリックします。  
  
5.  このトピックで前述した「**SharePoint アプリケーションの実行**」セクションの手順に従います。  
  
     これで、アイドル ループへの呼び出しが削除されたため、機能のアクティブ化がより高速になりました。  このことは、サンプル プロファイル レポートに反映されます。  
  
## 参照  
 [プロファイリング ツールの使用](../profiling/performance-explorer.md)   
 [プロファイリング ツールのパフォーマンス セッションの概要](../profiling/performance-session-overview.md)   
 [パフォーマンス プロファイリングのビギナーズ ガイド](../profiling/beginners-guide-to-performance-profiling.md)   
 [Visual Studio プロファイラーでアプリケーションのボトルネックを見つける](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
  