---
title: ASP.NET アプリケーションのデバッグを有効にする |Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 438e5a96ef07faf399d06ae517afe313a44673b4
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057851"
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Visual Studio で ASP.NET アプリケーションをデバッグします。

Visual Studio から ASP.NET アプリケーションをデバッグすることができます。

## <a name="requirements"></a>必要条件

このトピックの手順を以下にする必要があります。

- IIS Express、既定では Visual Studio 2012 以降に含まれています

    - または -

- ローカル IIS の web サーバー (バージョン 8.0 以降) が正しく構成され、エラーのない ASP.NET アプリケーションを実行します。

サーバーがリモートでの場合は、リモート コンピューターでリモート デバッガーを実行する必要があります。 リモートの IIS サーバーでデバッグするを参照してください。[リモート IIS コンピューター上の ASP.NET のデバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)します。 

## <a name="configure-debug-settings"></a>デバッグの設定を構成します。

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>プロジェクトのプロパティで ASP.NET のデバッグを有効にします。

1. Visual Studio での ASP.NET プロジェクトを開きます。

2. プロジェクトを右クリックして**ソリューション エクスプ ローラー**、選択**プロパティ**、 をクリックし、 **Web**タブ。

    プロジェクトの種類によっては、次のように選択します。**プロパティ > デバッグ**代わりにします。 Web フォームの ASP.NET プロジェクトの場合は、プロジェクトを右クリックして**プロパティ ページ > 開始オプション**します。
  
3.  **[デバッガー]** の下で、 **[ASP.NET]** チェック ボックスをオンにします。

    ![デバッガーの設定](../debugger/media/dbg-aspnet-enable-debugging.png "デバッガーの設定")

> [!NOTE]
> 新しい ASP.NET プロジェクトを作成する場合 (**ファイル > 新しいプロジェクト**)、デバッグの設定が正しく構成されて既にします。

### <a name="enable-debugging-in-the-webconfig-file"></a>Web.config ファイルでデバッグを有効にします。  

Web アプリをデバッグするには、アプリケーションの web.config ファイルを正しく構成する必要があります。 IIS または Iis-express でアプリをホストしている場合、web.config ファイルが必要です。

ASP.NET Core での web.config ファイルは (それが存在しない) 場合、アプリの展開時に自動的に作成されます。

> [!TIP]
> 展開プロセスは、web.config の設定は更新できます。 これをデバッグしようとすると、前に、サーバーの web.config 設定を確認します。
  
1.  Visual Studio でプロジェクトの web.config ファイルを開きます。  
  
    > [!NOTE]  
    > Web ブラウザーを使用して、web.config ファイルをリモートでアクセスすることはできません。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] では、セキュリティ上の理由から、ブラウザーが直接 Web.config ファイルにアクセスできないように Microsoft IIS を設定しています。 ブラウザーを使用して構成ファイルにアクセスしようとする場合は、HTTP アクセス エラー 403 (forbidden) を取得します。  
  
2.  `configuration/system.web/compilation` 要素を探します。 compilation 要素が存在しない場合は、その要素を作成します。

    Web.config は XML ファイルなので、タグでマークされた入れ子のセクションが含まれます。
  
3.  `compilation` 要素内に `debug` 属性がない場合は、その属性を要素に追加します。  
  
4.  `debug` 属性の値が `true` に設定されていることを確認します。  
  
Web.config ファイルは、次の例のようになります。

> [!NOTE]
> この例では、部分的な web.config ファイルです。 追加の XML セクションがある通常の構成と system.web 要素との間。 Compilation 要素が他の属性と要素にも含まれます。
  
#### <a name="example"></a>例  
  
```xml
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```

既定の IIS Express サーバーではなく、外部のサーバーを使用する場合をする必要がありますもことを確認、`targetFramework`属性値に一致するサーバーで構成します。

> [!IMPORTANT]
> 最適なパフォーマンスを運用アプリを設定`debug=false`をビルドして、アプリを発行すると、リリース ビルドを指定します。

## <a name="configure-project-settings-for-the-server"></a>サーバーのプロジェクト設定を構成します。

ローカル web サーバーでのデバッグ、プロジェクトのプロパティを設定します。 リモート サーバーでデバッグは、次のより包括的な手順で説明されている[Remote Debugging ASP.NET on IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)代わりにします。

1. **Web**タブ プロジェクトのプロパティは、いずれかを選択**IIS Express**または**外部サーバー**下、**サーバー**設定します。 (これらの設定をプロジェクトの種類によっては、下に表示されます、**デバッグ** タブの代わりにします)。

    ![サーバーの設定](../debugger/media/dbg-aspnet-server-settings.png "サーバーの設定")

    IIS Express は ASP.NET の既定のサーバーし、特別な構成を通常必要ありません。 これは、ASP.NET アプリケーションをデバッグする最も簡単な方法です。

    Web フォームの ASP.NET プロジェクトの場合、プロジェクトを右クリックし、選択**プロパティ ページ > 開始オプション**、いずれかを選択して**既定 Web サーバーを使用**または**カスタム サーバーを使用する**(代わりに**外部サーバー**)。

    ![Web フォーム アプリケーションのサーバー設定](../debugger/media/dbg-aspnet-server-settings-webforms.png "Web フォーム アプリケーションのサーバー設定")

2. 外部の (カスタム) サーバーを選択する場合で正しい URL を入力、**プロジェクト URL** (または**ベース URL**) フィールド。

    外部のサーバーがローカルの IIS の場合は、IIS をインストールされ正しく構成されている必要があります。 たとえば、正しいバージョンの ASP.NET は、IIS で構成する必要があります。 詳細については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)します。 デプロイとデバッグをテストする場合を参照してください。[展開をテストする](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis)します。

    外部のサーバーがある場合[リモート](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)、代わりに、プロセスにアタッチして、これらのプロジェクト設定は、デバッグは使用されません。

## <a name="local-iis-web-server-configure-iis"></a>(ローカル IIS web サーバー)IIS を構成します。

IIS express の場合は、web サーバーを構成する必要はありません (このセクションを省略します)。 IIS Express は、初期テストで使用することをお勧めします。

ローカル IIS web サーバーを使用している場合は次の手順に従います。

1. IIS が正しくインストールされていることを確認します。 詳細については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)します。

    * サーバーの正しいバージョンの ASP.NET をインストールすることを確認します。 Web Platform Installer (WebPI) を使用して ASP.NET 4.5 をインストールする (Windows Server 2012 R2 で、サーバー ノードから次のように選択します。 **Web プラットフォームの新しいコンポーネントの取得**、ASP.NET の検索)。 ASP.NET Core をインストールするを参照してください。 [IIS への発行](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration)します。

    > [!NOTE]
    > Windows Server 2008 R2 を使用している場合は、代わりにこのコマンドを使用して ASP.NET 4 をインストールします。

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. 開く、**インターネット インフォメーション サービス (IIS) マネージャー**します。 (サーバー マネージャーの左側のウィンドウで次のように選択します。 **IIS**します。 サーバーを右クリックして**インターネット インフォメーション サービス (IIS) マネージャー**)。

3. **接続**で左側のウィンドウに移動**サイト**します。

4. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。

5. 設定、**エイリアス**フィールドを**MyASPApp**、アプリケーション プールの既定値を受け入れます (**DefaultAppPool**)、設定、**物理パス**に**C:\inetpub\myNewFolder** (アプリの新しいフォルダーを作成) します。

6. **接続**、**アプリケーション プール**します。 開いている**DefaultAppPool**と、(ASP.NET 4.5 用の ASP.NET 4 を使用アプリケーションに適した値に、アプリケーション プール フィールドを設定します。 使用して、**マネージ コードがない**ASP.NET Core 用)。

## <a name="local-iis-web-server-deploy-the-app"></a>(ローカル IIS web サーバー)アプリを展開します。

IIS express の場合、web アプリがデプロイに自動的にデバッグを開始するときに (このセクションを省略します)。

ローカル IIS web サーバーを使用している場合は次の手順に従います。 アプリケーションを IIS に発行するさまざまな方法はあります。 次の手順では、作成して、ファイル システムをデプロイできるように、発行プロファイルを使用する方法を説明します。

1. 管理者として Visual Studio を再起動します。

    をこのメソッドを使用してデプロイするには、管理者特権が必要です。

2. Visual Studio でプロジェクトを右クリックし、選択**発行**(Web フォームを使用して**Web アプリの発行**)。

3. 選択**IIS、FTP など**クリック**発行**します。

    ![IIS に発行](../debugger/media/dbg-aspnet-local-iis.png "IIS への公開")

    Web フォーム アプリでは、次のように選択します。**カスタム**発行 ダイアログ ボックスで、プロファイル名を入力し、選択**OK**します。

4. **メソッドを公開**フィールドで選択**ファイル システム**します。

5. **ターゲットの場所**、クリックして、**参照**ボタンをクリックします。

6. (ASP.NET Core)選択**ファイル システム**作成した後で、アプリのフォルダーを選択します。

6. (ASP.NET)選択**ローカル IIS**、以前に作成し、をクリックし、web サイトを選択します。**オープン**します。

    ![IIS に発行](../debugger/media/dbg-aspnet-local-iis-select-site.png "IIS への公開")

    > [!TIP]
    > Web サーバーを示すメッセージが正しく構成されていない場合は、IIS の正しいバージョンの ASP.NET がインストールされていることを確認します。

7. をクリックして**次**を選択し、**デバッグ**構成します。

    > [!NOTE]
    > この設定は、リリース構成で展開する場合`debug=false`サーバーの web.config ファイルにします。

8. をクリックして**保存**発行の設定を保存し**発行**します。

    > [!CAUTION]
    >  コードまたは再構築を変更する必要がある場合を再発行し、この手順を繰り返す必要があります。 リモート コンピューターにコピーした実行可能ファイルは、ローカルのソースとシンボルに正確に一致している必要があります。

## <a name="set-a-breakpoint-and-start-debugging"></a>ブレークポイントを設定し、デバッグを開始

1. Visual Studio でプロジェクトには、いくつかがわかっているコードにブレークポイントを設定が実行されます。

2. キーを押してデバッグを開始する**F5** (**デバッグ > [デバッグ開始]**)。

3. ブレークポイントを含むコードを実行するアクションを実行します。

    デバッガーでは、ブレークポイントを設定したが一時停止します。

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(ローカル IIS)トラブルシューティング: とブレークポイントにヒットすることはできません。

1. IIS から web アプリを起動し、正しく動作するかどうかを確認します。 Web アプリが実行されているままにします。

2. Visual studio で、次のように選択します。**デバッグ > プロセスにアタッチ**ASP.NET プロセスに接続し (通常**w3wp.exe**または**dotnet.exe**)。 詳細については、次を参照してください。[プロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。

    使用して接続できない場合は**プロセスにアタッチ**と、ブレークポイントにヒットすることができますを使用してデバッグを開始できません**F5**設定がプロジェクトのプロパティで正しくないことと考えられます。 ホスト ファイルを使用している場合は、正しく構成されていることを確認します。

  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
Web.config ファイルが変更されると、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] が自動的に変更を検出し、新しい構成設定を適用します。 変更を反映させるためにコンピューターまたは IIS サーバーを再起動する必要はありません。  
  
Web サイトには、複数の仮想ディレクトリとサブディレクトリを含めることができ、それぞれに Web.config ファイルを用意できます。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションは、URL パスの上位レベルにある Web.config ファイルの設定を継承します。 階層構造の構成ファイルを利用して、下位の階層にあるすべてのアプリケーションなど、複数の [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションの設定を同時に変更できます。 ただし場合、`debug`設定は、階層内の下位のファイルで、上位の値をオーバーライドします。  
  
たとえば、指定する`debug="true"`www.microsoft.com/aaa/Web.config、および任意のアプリケーション、aaa フォルダーまたは aaa の任意のサブフォルダーがその設定を継承します。 したがって、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] www.microsoft.com/aaa/bbb のアプリケーションは、継承設定がそのいずれかが[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]www.microsoft.com/aaa/ccc、www.microsoft.com/aaa/ddd、内のアプリケーション。 唯一の例外は、アプリケーションの 1 つが、より低いレベルにある独自の Web.config ファイルで設定をオーバーライドする場合です。  
  
> [!IMPORTANT]
> パフォーマンスに影響が大幅にデバッグ モードを有効にすると、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]アプリケーション。 リリース バージョンのアプリケーションを配置したり、パフォーマンスの測定を実施したりする前には、デバッグ モードを無効にしてください。  
  
## <a name="see-also"></a>関連項目  
[ASP.NET のデバッグ: システム要件](aspnet-debugging-system-requirements.md)   
[方法: ユーザー アカウントでワーカー プロセスの実行](how-to-run-the-worker-process-under-a-user-account.md)   
[方法: ASP.NET プロセスの名前を見つける](how-to-find-the-name-of-the-aspnet-process.md)   
[デプロイされた Web アプリケーションをデバッグします。](debugging-deployed-web-applications.md)   
[チュートリアル: Web フォームのデバッグ](walkthrough-debugging-a-web-form.md)   
[方法: ASP.NET の例外のデバッグ](how-to-debug-aspnet-exceptions.md)   
[Web アプリケーションをデバッグする : エラーおよびトラブルシューティング](debugging-web-applications-errors-and-troubleshooting.md)
  
