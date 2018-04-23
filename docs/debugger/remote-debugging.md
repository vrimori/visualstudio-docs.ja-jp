---
title: Visual Studio でのリモート デバッグ |Microsoft ドキュメント
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 422714c1180ef94d32d8d323c796ed2c84258bf3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="remote-debugging"></a>Remote Debugging
別のコンピューターに配置されている Visual Studio アプリケーションをデバッグすることができます。 このデバッグを行うには、Visual Studio リモート デバッガーを使用します。

リモート デバッグの詳細な手順については、これらのトピックを参照してください。

|シナリオ|リンク|
|-|-|-|
|Azure App Service|[デバッガーをスナップショット](../debugger/debug-live-azure-applications.md)または[リモート Azure 上の ASP.NET のデバッグ](../debugger/remote-debugging-azure.md)|
|Azure 仮想マシン|[Azure での ASP.NET のリモート デバッグ](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Azure Service Fabric アプリケーションをデバッグします。](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[リモート デバッグの ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)または[リモート デバッグの ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# または Visual Basic|[C# プロジェクトまたは Visual Basic プロジェクトのリモート デバッグ](../debugger/remote-debugging-csharp.md)|
|C++|[C++ Project プロジェクトのリモート デバッグ](../debugger/remote-debugging-cpp.md)|
|ユニバーサル Windows アプリ (UWP)|[リモート コンピューターでの UWP アプリの実行](../debugger/run-windows-store-apps-on-a-remote-machine.md)または[インストール済みのアプリ パッケージのデバッグ](../debugger/debug-installed-app-package.md)|

だけをダウンロードし、リモート デバッガーをインストールして、シナリオで、追加の手順は必要ないはこの記事の手順に従います。
  
## <a name="download-and-install-the-remote-tools"></a>ダウンロードして、リモート ツールのインストール  

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="fileshare_msvsmon"></a> (省略可能)ファイル共有から、リモート デバッガーを実行するには

リモート デバッガーを見つけることができます (**msvsmon.exe**) Visual Studio Community、Professional、または Enterprise が既にインストール済みのコンピューターでします。 一部のシナリオでは、ファイル共有からリモート デバッガー (msvsmon.exe) を実行するはリモート デバッグをセットアップする最も簡単な方法です。 使用法の制限は、リモート デバッガーのヘルプ ページを参照してください (**ヘルプ > 使用状況**リモート デバッガーで)。

1. 検索**msvsmon.exe** Visual Studio のバージョンと一致するディレクトリにします。 For Visual Studio Enterprise 2017。

      **プログラム ファイル (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **プログラム ファイル (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. 共有、**リモート デバッガー** Visual Studio コンピューター上のフォルダーです。

3. リモート コンピューターで実行して**msvsmon.exe**です。 以下の[セットアップ手順](#bkmk_setup)です。

> [!TIP] 
> コマンド ライン インストールとコマンド ライン リファレンスでは、ヘルプ ページを参照してください**msvsmon.exe** 」と入力して``msvsmon.exe /?``with Visual Studio がインストールされているコンピューター上のコマンドラインで (に移動または**ヘルプ > 使用状況**リモート デバッガーで)。
  
## <a name="requirements_msvsmon"></a> 必要条件

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]
  
## <a name="set-up-the-remote-debugger"></a>リモート デバッガーのセットアップ  

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> リモート デバッガーを構成します。  
リモート デバッガーを初めて起動した後、リモート デバッガーの構成の一部を変更できます。
  
-   リモート デバッガーへの接続を選択するには、他のユーザーのアクセス許可を追加する必要がある場合**ツール > のアクセス許可**です。 アクセス許可を付与または拒否するには、管理者特権が必要です。

     > [!IMPORTANT] 
     > Visual Studio コンピューターを使用しているユーザー アカウントからユーザー アカウントとは異なるリモート デバッガーを実行することができますが、別のユーザー アカウントをリモート デバッガーのアクセス許可を追加する必要があります。 

     使用してコマンドラインからリモート デバッガーを開始する代わりに、 **/allow\<ユーザー名 >**パラメーター: **msvsmon/allow \< username@computer>**です。
  
-   認証モードやポート番号を変更したり、リモート ツールのタイムアウト値を指定する必要がある場合: 選択**ツール > オプション**です。  
  
     既定で使用されるポート番号の一覧については、次を参照してください。[リモート デバッガーのポート割り当て](../debugger/remote-debugger-port-assignments.md)です。  
  
     > [!WARNING]
     >  リモート ツールを [認証なし] モードで実行することも選択できますが、このモードの使用は避けることを強く推奨します。 このモードで実行した場合、ネットワーク セキュリティはまったく提供されません。 [認証なし] モードは、ネットワークに悪意のあるコードや悪意のあるトラフィックのリスクがないことが確実である場合にのみ選択してください。

##  <a name="bkmk_configureService"></a> (省略可能)サービスとしてリモート デバッガーを構成します。
ASP.NET および他のサーバー環境でデバッグは、管理者としてリモート デバッガーを実行か、常に実行する場合は、サービスとしてリモート デバッガーを実行します。
  
 リモート デバッガーをサービスとして構成する場合は、以下の手順を実行します。  
  
1.  **リモート デバッガー構成ウィザード** (rdbgwiz.exe) を見つけます (このアプリケーションは、リモート デバッガーとは別のアプリケーションです)。このアプリケーションは、リモート ツールをインストールした場合にのみ入手でき、 Visual Studio と共にはインストールされません。  
  
2.  構成ウィザードの実行を開始します。 最初のページが表示されたら、 **[次へ]**をクリックします。  
  
3.  **[Visual Studio 2015 リモート デバッガー サービスを実行する]** チェック ボックスをオンにします。  
  
4.  ユーザー アカウントの名前とパスワードを追加します。  
  
     追加する必要があります、**サービスとしてログオン**権利をこのアカウントのユーザー (検索**ローカル セキュリティ ポリシー** (secpol.msc) で、**開始**ページまたはウィンドウ (または型**secpol**コマンド プロンプトで)。 ウィンドウが表示されたら、 **[ユーザー権利の割り当て]**をダブルクリックし、右ペインで **[サービスとしてログオン]** を見つけます。 これをダブルクリックします。 ユーザー アカウントを追加、**プロパティ**ウィンドウをクリック**OK**)。 **[次へ]**をクリックします。  
  
5.  リモート ツールが通信するネットワークの種類を選択します。 少なくとも 1 つのネットワークの種類を選択する必要があります。 コンピューターがドメインを介して接続されている場合は、最初の項目を選択する必要があります。 コンピューターがワークグループまたはホーム グループを介して接続されている場合は、2 番目または 3 番目の項目を選択する必要があります。 **[次へ]**をクリックします。  
  
6.  サービスを開始できた場合は、「 **Visual Studio リモート デバッガー構成ウィザードは正常に完了しました**」と表示されます。 サービスを開始できなかった場合は、「 **Visual Studio リモート デバッガー構成ウィザードを完了できませんでした**」と表示されます。 このページには、サービスを開始するために従う必要があるヒントもいくつか提供されます。  
  
7.  **[完了]**をクリックします。  
  
 この時点で、リモート デバッガーはサービスとして実行されています。 これに移動して確認することができます**コントロール パネル > サービス**を探すこと**Visual Studio 2015 リモート デバッガー**です。  
  
 停止してから、リモート デバッガー サービスを再開**コントロール パネル > サービス**です。

## <a name="set-up-debugging-with-remote-symbols"></a>リモート シンボルを使用したデバッグのセットアップ 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]
  
## <a name="see-also"></a>関連項目  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)   
 [リモート デバッグ用に Windows ファイアウォールを構成します。](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [リモート デバッガーのポートの割り当て](../debugger/remote-debugger-port-assignments.md)   
 [リモートの IIS のリモート コンピューター上の ASP.NET Core のデバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)
