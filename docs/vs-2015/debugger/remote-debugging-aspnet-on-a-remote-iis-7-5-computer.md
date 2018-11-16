---
title: ASP.NET のリモートの IIS 7.5 でリモート デバッグ コンピューター |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d249571830ac608bef12c4a47d0243de1859a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764074"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>ASP.NET のリモート IIS コンピューター上でリモート デバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Iis および Windows Server コンピューターに ASP.NET Web アプリケーションを展開し、リモート デバッグ用に設定できます。 このガイドでは、設定、Visual Studio 2015 の MVC 4.5.2 アプリケーションを構成して、IIS にデプロイ、および Visual Studio からリモート デバッガーをアタッチする方法について説明します。

これらの手順は、これらのサーバー構成でテストされています。
* Windows Server 2012 R2 と IIS 10
* Windows Server 2008 R2 と IIS 7.5

この記事の情報の大部分は、リモート デバッグ、ASP.NET Core アプリケーションの ASP.NET core アプリの展開が異なると、余分な手順が必要ですにも適用されます。 を IIS に ASP.NET Core アプリを展開するすべてのセクションを完了する必要があります[今回](https://docs.asp.net/en/latest/publishing/iis.html)します。

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>前提条件: Windows Server コンピューターでリモート デバッガーをインストールします。

Windows Server コンピューターにリモート デバッガーをダウンロードする方法については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)します。

ASP.NET アプリケーションのリモート デバッグを行うには、管理者としてリモート デバッガー アプリケーションを実行するか、サービスとしてリモート デバッガーを起動します。 リモート デバッガーをサービスとして実行する方法の詳細については、「 [Remote Debugging](../debugger/remote-debugging.md)」を参照してください。

インストールが完了したら、ターゲット コンピューターでリモート デバッガーが実行されているかどうかを確認します。 (そうでない場合は検索**リモート デバッガー**で、**開始**メニュー。 ) 次のようなリモート デバッガーのウィンドウが表示されます。 (4020 は既定のポート番号)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Visual Studio コンピューターでアプリケーションを作成する  
  
1. MVC の ASP.NET アプリケーションを新規作成します。 (**[ファイル] / [新規作成] / [プロジェクト]** の順に選択してから、 **[Visual C#] / [Web] / [ASP.NET Web アプリケーション]** の順に選択します。 **[ASP.NET 4.5.2** テンプレート] セクションで、 **[MVC]** を選択します。 必ず**クラウド内のホスト**[Azure] セクションが選択されていません。 プロジェクトに名前を**MyMVC**)。
1. HomeController.cs ファイルを開き、 `About()` メソッドにブレークポイントを設定します。
1. **ソリューション エクスプローラー**で、プロジェクト ノードを右クリックして **[公開]** を選択します。
1. **[発行先を選択します]** で、 **[カスタム]** を選択し、プロファイルに「 **MyMVC**」と名前を付けます。 **[次へ]** をクリックします。
1. **[接続]** タブで、 **[発行方法]** フィールドを **[ファイル システム]** に、 **[ターゲットの場所]** フィールドをローカル ディレクトリに設定します。 **[次へ]** をクリックします。

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. 構成を **[デバッグ]** に設定します。 **[発行]** をクリックします。

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    アプリケーションがローカル ディレクトリに発行されるはずです。

## <a name="BKMK_deploy_asp_net"></a> Windows Server のリモート コンピューター上の ASP.NET アプリケーションをデプロイします。

 このセクションでは、Windows Server コンピューターで既に IIS が有効になっていることを前提としています。 Windows Server 2012 R2 では、次を参照してください。 [IIS 構成](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration)IIS を有効にします。 (進んで他のセクションではこの記事の ASP.NET Core アプリをデプロイしようとしている場合を除き、します。 ASP.NET Core での手順に従ってここで説明されている手順ではなくアプリをデプロイする記事では。)
1. ASP.NET の使用に ASP.NET 4.5 をインストールする Web プラットフォーム コンポーネントをインストール (Windows Server 2012 R2 で、サーバー ノードから次のように選択します**Web プラットフォームの新しいコンポーネントの取得**、ASP.NET の検索)。

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    Windows Server 2008 R2 では、代わりにこのコマンドを使用して ASP.NET 4 をインストール: **C:\Windows\Microsoft.NET\Framework (64) の \v4.0.30319\aspnet_regiis.exe ir**
1. ASP.NET プロジェクト ディレクトリを Visual Studio コンピューターから Windows Server コンピューター上のローカル ディレクトリ (ここでは、 **C:\Publish**と呼びます) にコピーします。 プロジェクトを手動でコピー、Xcopy、Web Deploy、Robocopy、Powershell、またはその他のオプションを使用できます。

    > [!CAUTION]
    >  コードまたは再構築を変更する必要がある場合を再発行し、この手順を繰り返す必要があります。 リモート コンピューターにコピーした実行可能ファイルは、ローカルのソースとシンボルに正確に一致している必要があります。
1. web.config ファイルに .NET Framework の正しいバージョンが示されていることを確認します。  たとえば、既定では Windows Server 2008 R2 にインストールされている .NET Framework バージョン 4.0.30319 が ASP.NET 4.5.2 を作成したバージョン。 ASP.NET 4.0 アプリケーションが Windows Server コンピューターで実行している場合は、バージョンを変更する必要があります。
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```
1. **インターネット インフォメーション サービス (IIS) マネージャー** を開き、 **[サイト]** に移動します。
1. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。
1. 設定、**エイリアス**フィールドを**MyMVC**と、アプリケーション プール フィールドを**ASP.NET v4.0** (ASP.NET 4.5 は、アプリケーション プールのオプションではありません)。 **[物理パス]** を「 **C:\Publish** 」 (ASP.NET プロジェクト ディレクトリをコピーしたディレクトリ) に設定します。

    >[!NOTE] 
    > ASP.NET Core アプリの場合に、アプリケーション プール フィールドを設定**マネージ コードなし**します。
1. 右クリックし、デプロイをテスト**既定の Web サイト**選択**参照**します。
    アプリを正常にデプロイした場合は、web ページが表示されます。

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Visual Studio コンピューターから ASP.NET アプリケーションにアタッチする

1. Visual Studio コンピューターで、 **MyMVC** ソリューションを開きます。
1. Visual Studio で、次のようにクリックします。**デバッグ]/[プロセスにアタッチ**(**Ctrl + Alt + P**)。
1. 修飾子のフィールドに設定**\<リモート コンピューター名 >: 4020**します。
1. クリックして**更新**します。
    **[選択可能なプロセス]** ウィンドウにプロセスがいくつか表示されます。

    すべてのプロセスが表示されない場合は、(ポートが必要です)、リモート コンピューター名ではなく IP アドレスを使用してください。 使用`ipconfig`IPv4 アドレスを取得するコマンド ラインでします。
1. **[すべてのユーザーからのプロセスを表示する]** をオンにします。
1. **w3wp.exe** を見つけて **[アタッチ]** をクリックします。

     プロセス名をすばやく見つけるには、プロセスの最初の文字を入力します。
     
    >[!NOTE]
    > ASP.NET Core アプリの場合は、w3wp.exe ではなく dnx.exe プロセスを選択します。 (このプロセスの名前は、今後のリリースで変更可能性があります)。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. リモート コンピューターの Web サイトを開きます。 ブラウザーに移動します。 **http://\<リモート コンピューター名 >** します。
    
    ASP.NET の Web ページが表示されるはずです。
1. ASP.NET web ページで、リンクをクリックして、**について**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。



