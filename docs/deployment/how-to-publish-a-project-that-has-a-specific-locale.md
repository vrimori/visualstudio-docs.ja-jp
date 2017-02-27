---
title: "方法 : 特定のロケールを持つプロジェクトを発行する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "配置 (アプリケーションを) [ClickOnce], ローカライズされたプロジェクト"
  - "ロケール, 対応した配置"
  - "ロケール, 対応した発行"
  - "マクロ, 配置"
  - "マクロ, 発行"
  - "発行 (ローカライズされたプロジェクトを)"
  - "発行, ローカライズされたプロジェクト"
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 特定のロケールを持つプロジェクトを発行する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

1 つのアプリケーションに、ロケールの異なる複数のコンポーネントが含まれることも少なくありません。  その場合、複数のプロジェクトを持つソリューションを作成し、ロケールごとに個別のプロジェクトを発行することになります。  以降の手順では、マクロを使用して、ソリューションの 1 つ目のプロジェクトを 'en' ロケールを使用して発行する方法について説明しています。  この手順を 'en' 以外のロケールで実行する場合は、マクロ内の `localeString` を、使用するロケール \('de' や 'de\-DE' など\) に設定してください。  
  
> [!NOTE]
>  このマクロを使用するには、\[発行場所\] に有効な URL または UNC \(Universal Naming Convention\) 共有を指定する必要があります。  また、コンピューターにインターネット インフォメーション サービス \(IIS: Internet Information Service\) がインストールされている必要があります。  IIS をインストールするには、**\[スタート\]** メニューの **\[コントロール パネル\]** をクリックします。  **\[プログラムの追加と削除\]** をダブルクリックします。  **\[プログラムの追加と削除\]** で **\[Windows コンポーネントの追加と削除\]** をクリックします。  **Windows コンポーネント ウィザード**に表示される **\[コンポーネント\]** の一覧で、**\[インターネット インフォメーション サービス \(IIS\)\]** チェック ボックスをオンにします。  次に、**\[完了\]** をクリックして、ウィザードを閉じます。  
  
### 発行マクロを作成するには  
  
1.  マクロ エクスプローラーを開くには、**\[ツール\]** メニューの **\[マクロ\]** をポイントし、**\[マクロ エクスプローラー\]** をクリックします。  
  
2.  新しいマクロ モジュールを作成します。  マクロ エクスプローラーで **\[MyMacros\]** を選択します。  **\[ツール\]** メニューの **\[マクロ\]** をポイントし、**\[新しいマクロ モジュール\]** をクリックします。  モジュールに "PublishSpecificCulture" という名前を付けます。  
  
3.  マクロ エクスプローラーで **\[MyMacros\]** ノードを展開し、**\[PublishAllProjects\]** モジュールをダブルクリックして開きます。**\[ツール\]** メニューの **\[マクロ\]** をポイントし、**\[マクロ IDE\]** をクリックしてもかまいません。  
  
4.  マクロ IDE で、モジュールの `Import` ステートメントに続けて次のコードを追加します。  
  
    ```vb#  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certficate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  マクロ IDE を閉じます。  フォーカスが Visual Studio に戻ります。  
  
### 特定のロケールのプロジェクトを発行するには  
  
1.  Visual Basic Windows アプリケーション プロジェクトを作成するには、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[Visual Basic\]** ノードで、**\[Windows アプリケーション\]** をクリックします。  プロジェクトに "PublishLocales" という名前を付けます。  
  
3.  Form1 をクリックします。  **\[プロパティ\]** ウィンドウの **\[デザイン\]** で、**\[Language\]** プロパティを **\[\(既定値\)\]** から **\[英語\]** に変更します。  フォームの **\[Text\]** プロパティを MyForm に変更します。  
  
     ローカライズされたリソース DLL は必要になるまで作成されません。  たとえば、新しいロケールを指定した後で、フォームやそのコントロールのテキストを変更した場合などに作成されます。  
  
4.  Visual Studio IDE を使用して、PublishLocales を発行します。  
  
     **ソリューション エクスプローラー** で PublishLocales を選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  プロジェクト デザイナーの **\[発行\]** ページで、発行場所として「http:\/\/localhost\/PublishLocales」を指定し、**\[今すぐ発行\]** をクリックします。  
  
     発行 Web ページが表示されたら、そのページを終了します。  \(この手順では、プロジェクトを発行するだけで、インストールする必要はありません。\)  
  
5.  \[Visual Studio コマンド プロンプト\] ウィンドウでマクロを呼び出し、PublishLocales をもう一度発行します。  コマンド プロンプト ウィンドウを表示するには、**\[表示\]** メニューの **\[その他のウィンドウ\]** をクリックし、**\[コマンド ウィンドウ\]** をクリックするか、Ctrl キーと Alt キーを押しながら A キーを押します。  コマンド プロンプト ウィンドウで「`macros`」と入力すると、使用可能なマクロがオートコンプリートによって一覧表示されます。  次のマクロを選択し、Enter キーを押します。  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  発行プロセスが正常に完了すると、"PublishLocales\\PublishLocales.vbproj の発行は成功しました。  発行の言語は 'en' です。" というメッセージが表示されます。メッセージ ボックスの **\[OK\]** をクリックします。  発行 Web ページが表示されたら、**\[インストール\]** をクリックします。  
  
7.  C:\\Inetpub\\wwwroot\\PublishLocales\\en にアクセスします。  ローカライズされたリソース DLL のほかに、マニフェスト、setup.exe、発行 Web ページ ファイルなどのインストールされたファイルがあるはずです。  \(既定では、ClickOnce は EXE ファイルおよび DLL ファイルに .deploy という拡張子を追加します。この拡張子は展開後に削除できます。\)  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [Macros Development Environment](http://msdn.microsoft.com/ja-jp/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Macro Explorer Window](http://msdn.microsoft.com/ja-jp/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [How to: Edit and Programmatically Create Macros](http://msdn.microsoft.com/ja-jp/6716f820-1feb-48ad-a718-27eb6b473c5a)