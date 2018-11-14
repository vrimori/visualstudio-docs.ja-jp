---
title: '方法: 特定のロケールがあるプロジェクトの発行 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca121a8f8a68ca7a036b14c0f0c2bd6d1a84ff00
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607589"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>方法: プロジェクトが特定のロケールを発行します。
1 つのアプリケーションに、ロケールの異なる複数のコンポーネントが含まれることも少なくありません。 その場合、複数のプロジェクトを持つソリューションを作成し、ロケールごとに個別のプロジェクトを発行することになります。 以降の手順では、マクロを使用して、ソリューションの 1 つ目のプロジェクトを 'en' ロケールを使用して発行する方法について説明しています。 この手順を 'en' 以外のロケールで実行する場合は、マクロ内の `localeString` を、使用するロケール ('de' や 'de-DE' など) に設定してください。  
  
> [!NOTE]
>  このマクロを使用するには、[発行場所] に有効な URL または UNC (Universal Naming Convention) 共有を指定する必要があります。 また、コンピューターにインターネット インフォメーション サービス (IIS: Internet Information Service) がインストールされている必要があります。 IIS をインストールする、**開始**] メニューのをクリックして**コントロール パネルの [** します。 ダブルクリック**を追加または削除プログラム**します。 **プログラム追加と削除**、 をクリックして**Windows コンポーネントの追加/削除**します。 **Windows コンポーネント ウィザード**を選択、**インターネット インフォメーション サービス (IIS)**  チェック ボックス、**コンポーネント**一覧。 をクリックし、**完了**ウィザードを閉じます。  
  
### <a name="to-create-the-publishing-macro"></a>発行マクロを作成するには  
  
1.  マクロ エクスプ ローラーを開く、**ツール**メニューで、**マクロ**、 をクリックし、**マクロ エクスプ ローラー**。  
  
2.  新しいマクロ モジュールを作成します。 マクロ エクスプ ローラーで選択 **[mymacros]** します。 **ツール**メニューで、**マクロ**、 をクリックし、**新しいマクロ モジュール**します。 モジュールの名前を付けます**PublishSpecificCulture**します。  
  
3.  マクロ エクスプ ローラーで、 **mymacros**ノード、および順に開いて、 **PublishAllProjects**モジュールをダブルクリックして (またはから、**ツール**に**マクロ**、 をクリックし、**マクロ IDE**)。  
  
4.  マクロ IDE で、モジュールの `Import` ステートメントに続けて次のコードを追加します。  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certificate and the   
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
  
5.  マクロ IDE を閉じます。 フォーカスが Visual Studio に戻ります。  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>特定のロケールのプロジェクトを発行するには  
  
1.  Visual Basic Windows アプリケーション プロジェクトを作成する、**ファイル**メニューで、**新規**、 をクリックし、**プロジェクト**します。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、 **Windows アプリケーション**から、 **Visual Basic**ノード。 プロジェクトに名前を*PublishLocales*します。  
  
3.  Form1 をクリックします。 **プロパティ**ウィンドウで、**デザイン**、変更、**言語**プロパティから **(既定)** に**英語**. 変更、**テキスト**プロパティをフォームの**MyForm**します。  
  
     ローカライズされたリソース DLL は必要になるまで作成されません。 たとえば、新しいロケールを指定した後で、フォームやそのコントロールのテキストを変更した場合などに作成されます。  
  
4.  発行*PublishLocales* Visual Studio IDE を使用しています。  
  
     **ソリューション エクスプ ローラー**、 *PublishLocales*します。 **プロジェクト**メニューの **プロパティ**します。 プロジェクト デザイナーで、**発行**の発行場所の指定 ページで、 **http://localhost/PublishLocales**、順にクリックします**今すぐ発行**します。  
  
     発行 Web ページが表示されたら、そのページを終了します。 (この手順では、プロジェクトを発行するだけで、インストールする必要はありません。)  
  
5.  発行*PublishLocales* Visual Studio コマンド プロンプト ウィンドウでマクロを呼び出し、もう一度です。 コマンド プロンプト ウィンドウを表示する、**ビュー**メニューで、**その他の Windows**順にクリックします**コマンド ウィンドウ**、またはキーを押します**Ctrl** +**Alt**+**A**します。 コマンド プロンプト ウィンドウで次のように入力します。`macros`がオートコンプリートによって使用可能なマクロの一覧が表示されます。 次のマクロを選択し、Enter キーを押します。  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  発行プロセスが成功すると、というメッセージが生成されます"が正常に発行*\publishlocales.vbproj*します。 発行の言語は 'en' です。" というメッセージが表示されます。クリックして**OK**メッセージ ボックスにします。 発行 Web ページが表示されたら、クリックして**インストール**します。  
  
7.  検索対象*C:\Inetpub\wwwroot\PublishLocales\en*します。 インストールされたファイル、マニフェストなどがわかります*setup.exe*、およびローカライズされたリソース DLL のほか、発行 Web ページのファイル。 (既定では、ClickOnce が付加されます、 *.deploy* Exe および Dll; での拡張機能配置後にこの拡張機能を削除することができます)。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションを発行します。](../deployment/publishing-clickonce-applications.md)   
 [開発環境のマクロ](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))   
 [マクロ エクスプ ローラー ウィンドウ](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))   
 [方法: 編集およびマクロをプログラムで作成](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))