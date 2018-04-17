---
title: ASP.NET アプリケーションのデバッグを有効にする |Microsoft ドキュメント
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 397dbe26aafd7ec385e6afeb11b3ca19155dfbcc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Visual Studio での ASP.NET アプリケーションをデバッグします。

Visual Studio から ASP.NET アプリケーションをデバッグすることができます。

## <a name="requirements"></a>要件

このトピックの手順に従って操作する必要があります。

- IIS Express で Visual Studio 2012 以降は既定で含まれています

    - または -

- ローカル IIS の web server (バージョン 8.0 以上) が正しく構成されているし、エラーが発生しない ASP.NET アプリケーションを実行できます。

サーバーがリモートの場合、リモート デバッガーはリモート コンピューターで実行されている必要があります。 リモートの IIS サーバーでデバッグするを参照してください。[リモート IIS コンピューター上の ASP.NET のデバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)です。 

## <a name="configure-debug-settings"></a>デバッグ設定を構成します。

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>プロジェクトのプロパティで ASP.NET デバッグを有効にします。

1. Visual Studio での ASP.NET プロジェクトを開きます。

2. プロジェクトを右クリックして**ソリューション エクスプ ローラー**、選択**プロパティ**、をクリックし、 **Web**タブです。

    プロジェクトの種類によっては、選択**プロパティ > デバッグ**代わりにします。 フォームの ASP.NET Web プロジェクトの場合、プロジェクトを右クリックし **プロパティ ページ > 開始オプション**です。
  
3.  **[デバッガー]**の下で、 **[ASP.NET]** チェック ボックスをオンにします。

    ![デバッガーの設定](../debugger/media/dbg-aspnet-enable-debugging.png "デバッガーの設定")

> [!NOTE]
> 新しい ASP.NET プロジェクトを作成する場合 (**ファイル > 新しいプロジェクト**)、デバッグの設定が正しく構成されて既にです。

### <a name="enable-debugging-in-the-webconfig-file"></a>Web.config ファイルでデバッグを有効にします。  

Web アプリをデバッグするには、アプリケーションの web.config ファイルを正しく構成する必要があります。 IIS または IIS Express でアプリをホストしている場合、web.config ファイルが必要です。

ASP.NET Core、web.config ファイルが自動的に作成 (が既に存在しない) 場合、アプリが展開されます。

> [!TIP]
> 展開プロセスでは、web.config の設定を更新できます。 これをデバッグする前に、サーバー上の web.config 設定を確認します。
  
1.  Visual Studio で、プロジェクトの web.config ファイルを開きます。  
  
    > [!NOTE]  
    > Web ブラウザーを使用して、web.config ファイルをリモートでアクセスすることはできません。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] では、セキュリティ上の理由から、ブラウザーが直接 Web.config ファイルにアクセスできないように Microsoft IIS を設定しています。 ブラウザーを使用して構成ファイルにアクセスしようとする場合は、HTTP アクセス エラー 403 (禁止) を取得します。  
  
2.  `configuration/system.web/compilation` 要素を探します。 compilation 要素が存在しない場合は、その要素を作成します。

    Web.config は XML ファイルなので、タグでマークされた入れ子のセクションが含まれます。
  
3.  `compilation` 要素内に `debug` 属性がない場合は、その属性を要素に追加します。  
  
4.  `debug` 属性の値が `true`をクリックします。  
  
Web.config ファイルは、次の例のようになります。

> [!NOTE]
> この例は、部分的な web.config ファイルです。 追加の XML セクションがある通常の構成と system.web 要素との間。 Compilation 要素は他の属性と要素にもあります。
  
#### <a name="example"></a>例  
  
```  
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

IIS Express の既定のサーバーではなく、外部のサーバーを使用している場合、必要がありますもことを確認、`targetFramework`属性値に一致するサーバーで構成します。

> [!IMPORTANT]
> 最適なパフォーマンスを運用アプリを設定`debug=false`し、ビルドして、アプリを発行すると、リリース ビルドを指定します。

## <a name="configure-project-settings-for-the-server"></a>サーバーのプロジェクトの設定を構成します。

ローカル web サーバーでデバッグすると、プロジェクトのプロパティを設定します。 リモート サーバーでデバッグすると、指示に従ってより包括的な」に記載[リモート IIS での ASP.NET のデバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)代わりにします。

1. **Web**タブ、プロジェクトのプロパティを選択するか**IIS Express**または**外部サーバー**下にある、**サーバー**設定します。 (下のプロジェクトの種類によっては、これらの設定に表示されます、**デバッグ** タブの代わりにします)。

    ![サーバーの設定](../debugger/media/dbg-aspnet-server-settings.png "サーバーの設定")

    IIS Express は、ASP.NET の既定のサーバーと、特別な構成を通常必要ありません。 これは、ASP.NET アプリケーションをデバッグする最も簡単な方法です。

    Web フォームの ASP.NET プロジェクトは、プロジェクトを右クリックし、選択**プロパティ ページ > 開始オプション**、いずれかを選択し、**既定 Web サーバーを使用する**または**カスタム サーバーを使用する**(代わりに**外部サーバー**)。

    ![Web フォーム アプリケーションのサーバー設定](../debugger/media/dbg-aspnet-server-settings-webforms.png "Web フォーム アプリケーションのサーバーの設定")

2. 外部 (カスタム) サーバーを選択する場合の正しい URL を入力、**プロジェクト URL** (または**ベース URL**) フィールドです。

    外部のサーバーがローカルの IIS の場合は、IIS をインストールされているし、正しく構成されている必要があります。 たとえば、正しいバージョンの ASP.NET は IIS で構成する必要があります。 詳細については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。 展開とデバッグをテストする場合を参照してください。[展開をテストする](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis)です。

    外部のサーバーがある場合[リモート](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)、代わりに、プロセスにアタッチして、これらのプロジェクト設定はデバッグは使用されません。

## <a name="local-iis-web-server-configure-iis"></a>(ローカル IIS web サーバー)IIS を構成します。

IIS express、web サーバーを構成する必要はありません (このセクションを省略します)。 IIS Express は、初期テストで使用することをお勧めします。

ローカル IIS web サーバーを使用している場合は次の手順に従います。

1. IIS が正しくインストールされていることを確認します。 詳細については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。

    * サーバーに正しいバージョンの ASP.NET をインストールすることを確認します。 Web Platform Installer (WebPI) を使用して ASP.NET 4.5 をインストールする (Windows Server 2012 R2 で、サーバー ノードから次のように選択します。**新しい Web Platform コンポーネントの取得**、ASP.NET の検索)。 ASP.NET Core をインストールするには、次を参照してください。[を IIS に発行](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration)です。

    > [!NOTE]
    > Windows Server 2008 R2 を使用している場合は、代わりにこのコマンドを使用して ASP.NET 4 をインストールします。

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. 開く、**インターネット インフォメーション サービス (IIS) マネージャー**です。 (サーバー マネージャーの左側のウィンドウで選択**IIS**です。 サーバーを右クリックし **インターネット インフォメーション サービス (IIS) マネージャー**)。

3. **接続**左側のウィンドウに移動**サイト**です。

4. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]**を選択します。

5. 設定、**エイリアス**フィールドを**MyASPApp**、既定のアプリケーション プール (**DefaultAppPool**)、し、設定、**物理パス**に**C:\inetpub\myNewFolder** (アプリ用の新しいフォルダーの作成) します。

6. **接続****アプリケーション プール**です。 開いている**DefaultAppPool**されが正しいことをアプリ (ASP.NET 4.5 用の ASP.NET 4 を使用値に、アプリケーション プール フィールドを設定します。 使用して**マネージ コードがない**ASP.NET core)。

## <a name="local-iis-web-server-deploy-the-app"></a>(ローカル IIS web サーバー)アプリを展開します。

IIS express、web アプリは自動的に展開デバッグを開始するときに (このセクションを省略します)。

ローカル IIS web サーバーを使用している場合は次の手順に従います。 IIS にアプリケーションを発行するさまざまな方法はあります。 次の手順で作成し、発行プロファイルを使用して、ファイル システムを展開するようにする方法を示します。

1. 管理者として Visual Studio を再起動します。

    このメソッドを使用してを展開するには、管理者特権が必要です。

2. Visual Studio でプロジェクトを右クリックして選択**発行**(Web フォームを使用して**Web アプリの発行**)。

3. 選択**IIS、FTP、等** をクリック**発行**です。

    ![IIS への公開](../debugger/media/dbg-aspnet-local-iis.png "IIS への公開")

    アプリについては、Web フォームを選択して**カスタム**発行 ダイアログ ボックスで、プロファイル名を入力し、選択**OK**です。

4. **発行方法**フィールドで選択**ファイル システム**です。

5. **ターゲットの場所**をクリックして、**参照**ボタンをクリックします。

6. (ASP.NET Core)選択**ファイル システム**し、以前に作成したアプリのフォルダーを選択します。

6. (ASP.NET)選択**ローカル IIS**、以前に作成し、をクリックして、web サイトを選択**開く**です。

    ![IIS への公開](../debugger/media/dbg-aspnet-local-iis-select-site.png "IIS への公開")

    > [!TIP]
    > Web サーバーを示すメッセージが正しく構成されていない場合は、IIS の正しいバージョンの ASP.NET がインストールされていることを確認します。

7. をクリックして**次**を選択し、**デバッグ**構成します。

    > [!NOTE]
    > この設定に Release 構成を展開する場合`debug=false`サーバーの web.config ファイルにします。

8. をクリックして**保存**発行設定を保存し、をクリックする**発行**です。

    > [!CAUTION]
    >  コードまたは再構築に変更を加える必要がある場合は再パブリッシュする必要がありますしてこの手順を繰り返します。 リモート コンピューターにコピーした実行可能ファイルは、ローカルのソースとシンボルに正確に一致している必要があります。

## <a name="set-a-breakpoint-and-start-debugging"></a>ブレークポイントを設定し、デバッグの開始

1. Visual Studio でのプロジェクトでは、セットの一部がわかっているコードのブレークポイントが実行されます。

2. キーを押してデバッグを開始する**f5 キーを押して**(**デバッグ > [デバッグ開始]**)。

3. ブレークポイントを含むコードを実行するアクションを実行します。

    デバッガーでは、ブレークポイントを設定するが一時停止します。

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(ローカルの IIS)トラブルシューティング: とブレークポイントにヒットすることはできません。

1. IIS から web アプリを起動し、正しく動作するかどうかを確認します。 Web アプリが実行されているままにします。

2. Visual Studio から、次のように選択します。**デバッグ > プロセスにアタッチする**ASP.NET プロセスに接続し (通常**w3wp.exe**または**dotnet.exe**)。 詳細については、次を参照してください。[プロセスにアタッチする](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)です。

    使用して接続できない場合は**プロセスにアタッチする**と、ブレークポイントにヒットすることができますを使用してデバッグを開始できません**f5 キーを押して**設定がプロジェクトのプロパティで正しくないことと考えられます。 HOSTS ファイルを使用している場合は、正しく構成されていることを確認します。

  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
Web.config ファイルが変更されると、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] が自動的に変更を検出し、新しい構成設定を適用します。 変更を反映させるためにコンピューターまたは IIS サーバーを再起動する必要はありません。  
  
Web サイトには、複数の仮想ディレクトリとサブディレクトリを含めることができ、それぞれに Web.config ファイルを用意できます。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションは、URL パスの上位レベルにある Web.config ファイルの設定を継承します。 階層構造の構成ファイルを利用して、下位の階層にあるすべてのアプリケーションなど、複数の [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションの設定を同時に変更できます。 ただし場合、`debug`設定は、階層内の下位のファイルで、上位の値をオーバーライドします。  
  
たとえば、指定する`debug="true"`www.microsoft.com/aaa/Web.config、およびアプリケーションと、aaa フォルダーまたは aaa の任意のサブフォルダーがその設定を継承します。 場合、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] www.microsoft.com/aaa/bbb のアプリケーションが、継承に設定がすべて[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]www.microsoft.com/aaa/ccc、www.microsoft.com/aaa/ddd、内のアプリケーションです。 唯一の例外は、アプリケーションの 1 つが、より低いレベルにある独自の Web.config ファイルで設定をオーバーライドする場合です。  
  
> [!IMPORTANT]
> パフォーマンスに影響が大幅にデバッグ モードを有効にすると、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]アプリケーションです。 リリース バージョンのアプリケーションを配置したり、パフォーマンスの測定を実施したりする前には、デバッグ モードを無効にしてください。  
  
## <a name="see-also"></a>関連項目  
[ASP.NET のデバッグ: システム要件](aspnet-debugging-system-requirements.md)   
[方法: ユーザー アカウントでワーカー プロセスの実行](how-to-run-the-worker-process-under-a-user-account.md)   
[方法: ASP.NET プロセスの名前を見つける](how-to-find-the-name-of-the-aspnet-process.md)   
[配置済みの Web アプリケーションをデバッグします。](debugging-deployed-web-applications.md)   
[チュートリアル: Web フォームのデバッグ](walkthrough-debugging-a-web-form.md)   
[方法: ASP.NET の例外のデバッグ](how-to-debug-aspnet-exceptions.md)   
[Web アプリケーションをデバッグする : エラーおよびトラブルシューティング](debugging-web-applications-errors-and-troubleshooting.md)
  