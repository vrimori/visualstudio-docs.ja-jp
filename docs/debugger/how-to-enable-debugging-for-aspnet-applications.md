---
title: ASP.NET アプリのデバッグの有効化 |Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 09/21/18
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
ms.openlocfilehash: 41da2eb360bac4c50f85bd908f980f5ee3c1d141
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813428"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio での ASP.NET または ASP.NET Core アプリをデバッグします。

Visual Studio で ASP.NET と ASP.NET Core アプリをデバッグすることができます。 ASP.NET と ASP.NET Core では、プロセスとは異なると、IIS Express または IIS サーバーをローカルで実行するかどうか。 

>[!NOTE]
>次の手順と設定は、ローカル サーバー上のアプリのデバッグにのみ適用されます。 サーバーを使用してリモートの IIS でアプリをデバッグ**プロセスにアタッチ**、これらの設定を無視します。 詳細と IIS で ASP.NET アプリのリモート デバッグについては、次を参照してください。 [ASP.NET の IIS コンピューター上のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)または[リモート IIS コンピューター上の ASP.NET Core のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)します。

組み込みの IIS Express サーバーは、Visual Studio に含まれています。 IIS Express は ASP.NET と ASP.NET Core プロジェクトでは、既定のデバッグ サーバーおよびが事前に構成します。 デバッグ、および初期のデバッグとテストに最適に最も簡単な方法です。 

ASP.NET または ASP.NET Core アプリ ローカル IIS サーバー (バージョン 8.0 以降) でアプリを実行するように構成をデバッグすることもできます。 IIS をローカルでデバッグするには、次の要件を満たす必要があります。 

<a name="iis"></a>
- 選択**開発時 IIS サポート**Visual Studio をインストールするときにします。 (必要に応じて、Visual Studio インストーラーを再実行して、選択**変更**、し、このコンポーネントを追加します)。
- 管理者として Visual Studio を実行します。 
- インストールし、適切なバージョンの ASP.NET または ASP.NET Core で IIS が正しく構成します。 詳細と手順については、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)または[IIS と Windows での ASP.NET Core のホスト](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index)します。
- エラーのない、アプリが IIS で実行することを確認します。

## <a name="debug-aspnet-apps"></a>ASP.NET アプリをデバッグします。 

IIS Express は、既定値は、およびが事前に構成します。 をローカルの IIS でデバッグしている場合は、を満たしていることを確認してください、[ローカル IIS のデバッグの要件](#iis)します。 

1. Visual Studio で ASP.NET プロジェクトを選択**ソリューション エクスプ ローラー**  をクリックし、**プロパティ**アイコン、キーを押して**Alt**+**」と入力**、または右クリックし、選択**プロパティ**します。
   
1. 選択、 **Web**タブ。
   
1. **プロパティ** ウィンドウで、**サーバー**、 
   - IIS express の場合は、選択**IIS Express**ドロップダウン リストから。
   - ローカルの IIS
     1. 選択**ローカル IIS**ドロップダウン リストから。
     1. 次に、**プロジェクト URL**フィールドで、**仮想ディレクトリの作成**IIS でのアプリをまだ設定していない場合は。
   
1. **デバッガー**、 **ASP.NET**します。
   
   ![ASP.NET デバッガー設定](media/dbg-aspnet-enable-debugging2.png "ASP.NET デバッガーの設定")
   
1. 使用**ファイル** > **選択した項目の保存**または**Ctrl**+**S**変更を保存します。 
   
1. プロジェクトで、アプリをデバッグするには、いくつかのコードにブレークポイントを設定します。 Visual Studio のツールバーで、構成に設定を確認します**デバッグ**に必要なブラウザーが表示されますおよび**IIS Express (\<ブラウザー名 >)** または**ローカル IIS (\<ブラウザー名 >)** エミュレーター フィールドにします。 
   
1. デバッグを開始する次のように選択します**IIS Express (\<ブラウザー名 >)** または**ローカル IIS (\<ブラウザー名 >)** ツールバーで、次のように選択します。 **[デバッグ開始]**。から、**デバッグ**メニューのまたはキーを押して**F5**します。 デバッガーがブレークポイントで一時停止します。 デバッガーがブレークポイントにヒットできない場合は、次を参照してください。[トラブルシューティング デバッグ](#troubleshoot-debugging)します。

## <a name="debug-aspnet-core-apps"></a>ASP.NET Core アプリをデバッグします。 

IIS Express は、既定値は、およびが事前に構成します。 をローカルの IIS でデバッグしている場合は、を満たしていることを確認してください、[ローカル IIS のデバッグの要件](#iis)します。 

1. Visual Studio で ASP.NET Core プロジェクトを選択**ソリューション エクスプ ローラー**  をクリックし、**プロパティ**アイコン、キーを押して**Alt**+**」と入力**、または右クリックし、選択**プロパティ**します。

1. **[デバッグ]** タブを選択します。
   
1. **プロパティ** ウィンドウで、次へ を**プロファイル**、 
   - IIS express の場合は、選択**IIS Express**ドロップダウン リストから。
   - ローカル IIS ドロップダウン リストからアプリ名を選択または選択**新規**新しいプロファイル名を作成し、選択**OK**します。
   
1. 横に**起動**、いずれかを選択**IIS Express**または**IIS**ドロップダウン リストから。 
   
1. 必ず**起動ブラウザー**が選択されています。
   
1. **環境変数**、ことを確認します**ASPNETCORE_ENVIRONMENT**の値が存在**開発**します。 そうでない場合は、選択**追加**し追加します。
   
   ![ASP.NET Core デバッガー設定](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core デバッガーの設定")
   
1. 使用**ファイル** > **選択した項目の保存**または**Ctrl**+**S**変更を保存します。 
   
1. プロジェクトで、アプリをデバッグするには、いくつかのコードにブレークポイントを設定します。 Visual Studio のツールバーで、構成に設定を確認します**デバッグ**、いずれかと**IIS Express**、またはエミュレーター フィールドで、新しい IIS プロファイル名が表示されます。 
   
1. デバッグを開始する次のように選択します**IIS Express**または **\<IIS プロファイル名 >** ツールバーで、次のように選択します。**デバッグの開始**から、 **のデバッグ。** メニューのまたはキーを押して**F5**します。 デバッガーがブレークポイントで一時停止します。 デバッガーがブレークポイントにヒットできない場合は、次を参照してください。[トラブルシューティング デバッグ](#troubleshoot-debugging)します。

## <a name="troubleshoot-debugging"></a>デバッグをトラブルシューティングします。

ローカル IIS のデバッグは、ブレークポイントに進むことはできない場合、は、以下の手順を実行のトラブルシューティングを行う。 

1. IIS から web アプリを起動し、正しく動作するかどうかを確認します。 Web アプリが実行されているままにします。
   
2. Visual studio で、次のように選択します**デバッグ > プロセスにアタッチ**またはキーを押します**Ctrl**+**Alt**+**P**、と。ASP.NET または ASP.NET Core のプロセスへの接続 (通常**w3wp.exe**または**dotnet.exe**)。 詳細については、次を参照してください。[プロセスにアタッチ](attach-to-running-processes-with-the-visual-studio-debugger.md)と[ASP.NET プロセスの名前を見つける方法](how-to-find-the-name-of-the-aspnet-process.md)します。

かどうかは、接続し、使用して、ブレークポイントにヒット、**プロセスにアタッチ**を使用していませんが、**デバッグ** > **デバッグの開始**または**F5**、設定がプロジェクトのプロパティで正しくないです。 ホスト ファイルを使用する場合は、正しく構成されてもを確認します。

## <a name="configure-debugging-in-the-webconfig-file"></a>Web.config ファイルでデバッグを構成します。  

ASP.NET プロジェクトが*web.config*両方アプリの構成と起動については、デバッグの設定などが含まれるファイルが既定では、します。 *Web.config*デバッグ用に、ファイルを正しく構成する必要があります。 **プロパティ**前のセクションでは更新プログラムの設定、 *web.config*ファイルもに手動で構成できます。 

> [!NOTE]
> ASP.NET Core プロジェクトが最初に*web.config*が、ファイル、 *appsettings.json*と*launchSettings.json*ファイルをアプリの構成および起動情報。 アプリのデプロイを作成、 *web.config*ファイルまたはファイルをプロジェクトで、デバッグ情報を通常は含まれません。

> [!TIP]
> デプロイ プロセスは更新、 *web.config*設定、デバッグする前に、ようにして、 *web.config*デバッグ用に構成します。
  
**手動で構成する、 *web.config*デバッグ用のファイル。**

1. Visual Studio で開き、ASP.NET プロジェクトの*web.config*ファイル。  
  
2. *Web.config* XML ファイルは、タグでマークされた入れ子のセクションを格納するためです。 検索、`configuration/system.web/compilation`セクション。 (場合、`compilation`要素の存在は作成しません)。
  
3. 確認、`debug`属性、`compilation`要素に設定されて`true`します。 (場合、`compilation`要素が含まれていない、`debug`属性、追加しに設定`true`)。 
  
   既定の IIS Express サーバーではなくローカルの IIS を使用する場合、以下のことを確認、`targetFramework`属性の値、`compilation`要素が、IIS サーバー上のフレームワークに一致します。
  
   `compilation`の要素、 *web.config*ファイルは、次の例のようになります。

   > [!NOTE]
   > この例は、部分的な*web.config*ファイル。 通常は追加の XML セクションがある、`configuration`と`system.web`要素、および`compilation`他の属性と要素が、要素に含めることも可能性があります。
  
   ```xml
   <configuration>  
      ...  
      <system.web>  
          <compilation  debug="true"  targetFramework="4.6.1" ... > 
             ...  
          </compilation>  
      </system.web>  
   </configuration>  
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 変更を自動的に検出*web.config*ファイルし、新しい構成設定が適用されます。 コンピューターや変更を有効にする IIS サーバーを再起動する必要はありません。  
  
Web サイトで複数の仮想ディレクトリとサブディレクトリを含めることができます*web.config*それぞれファイル。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリから構成設定を継承する*web.config*上位レベルの URL パスにあるファイル。 階層*web.config*ファイルの設定すべてに適用[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]かや、階層内のアプリ。 別の構成を設定、 *web.config*ファイル階層内の下位に高いファイル設定が上書きされます。  
  
例では、指定した場合の`debug="true"`で<em>www.microsoft.com/aaa/web.config</em>、任意のアプリ、 *aaa*フォルダーまたはサブフォルダーの*aaa* 、その設定を継承これらのアプリのいずれか、独自の設定をオーバーライドする場合を除く*web.config*ファイル。  
  
## <a name="publish-in-debug-mode-using-the-file-system"></a>ファイル システムを使用してデバッグ モードでの発行します。

IIS にアプリを発行するさまざまな方法はあります。 次の手順では、作成およびデバッグ ファイル システムを使用して発行プロファイルを展開する方法を示します。 これを行うは、管理者として Visual Studio する実行する必要があります。 

> [!IMPORTANT]
> コードまたは再構築を変更する場合は、再パブリッシュする手順を繰り返す必要があります。 

1. Visual Studio でプロジェクトを右クリックし、選択**発行**します。

3. 選択**IIS、FTP など**クリック**発行**します。

    ![IIS に発行](media/dbg-aspnet-local-iis.png "IIS への公開")

4. **CustomProfile**ダイアログ ボックスの**メソッドを公開**、選択**ファイル システム**します。

5. **ターゲットの場所**、**参照**(**.**).
   
   - ASP.NET では、選択**ローカル IIS**、アプリでは、作成した web サイトを選択し、**オープン**します。
     
     ![Asp.net IIS に発行](media/dbg-aspnet-local-iis1.png "ASP.NET を IIS に発行します。")
     
   - ASP.NET Core, 選択**ファイル システム**、アプリでは、セットアップし、フォルダーを選択します**オープン**します。

1. **[次へ]** を選択します。 

1. **構成**を選択します**デバッグ**ドロップダウン リストから。

1. **[保存]** を選択します。

1. **発行**ダイアログ ボックスで、必ず**CustomProfile** (または作成したプロファイルの名前) が表示されたらと**LastUsedBuildConfiguration**に設定されている**デバッグ**します。 

1. **[発行]** を選びます。

    ![IIS に発行](media/dbg-aspnet-local-iis-select-site.png "IIS への公開")

> [!IMPORTANT]
> デバッグ モードは、アプリのパフォーマンスを大幅に低下します。 最適なパフォーマンスを次のように設定します。`debug="false"`で、 *web.config*運用アプリを展開またはパフォーマンスの測定を実施するときに、リリース ビルドを指定します。  

## <a name="see-also"></a>関連項目  
[ASP.NET のデバッグ: システム要件](aspnet-debugging-system-requirements.md)   
[方法: ユーザー アカウントでワーカー プロセスの実行](how-to-run-the-worker-process-under-a-user-account.md)   
[方法: ASP.NET プロセスの名前を見つける](how-to-find-the-name-of-the-aspnet-process.md)   
[デプロイされた web アプリケーションをデバッグします。](debugging-deployed-web-applications.md)   
[チュートリアル: web フォームのデバッグ](walkthrough-debugging-a-web-form.md)   
[方法: ASP.NET の例外のデバッグ](how-to-debug-aspnet-exceptions.md)   
[Web アプリケーションのデバッグ: エラーおよびトラブルシューティング](debugging-web-applications-errors-and-troubleshooting.md)
  
