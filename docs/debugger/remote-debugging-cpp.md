---
title: リモート Visual C プロジェクトのデバッグ |Microsoft ドキュメント
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: df0caacf8d3d99117208ce197e075f20f6df8b5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>リモート Visual Studio での Visual C プロジェクトのデバッグ
別のコンピューターに Visual Studio アプリケーションをデバッグ、インストールして、アプリを展開するコンピューターでリモート ツールを実行、Visual Studio からリモート コンピューターに接続しと展開、アプリを実行するプロジェクトを構成します。

![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

リモート ユニバーサル Windows アプリ (UWP) をデバッグする方法については、次を参照してください。[インストール済みのアプリ パッケージをデバッグ](debug-installed-app-package.md)です。

## <a name="requirements"></a>要件

リモート デバッガーは、Windows 7 でサポートされていると新しい (phone ではない) と Windows Server の Windows Server 2008 Service Pack 2 以降のバージョン。 要件の一覧については、次を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)です。

> [!NOTE]
> プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での待機時間の長いまたはダイヤルアップ、インターネットなどの低帯域幅接続またはインターネット経由でのデバッグはお勧めしませんが失敗することも非常に遅くします。
  
## <a name="download-and-install-the-remote-tools"></a>ダウンロードして、リモート ツールのインストール

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
> [!TIP]
> 一部のシナリオでは、ファイル共有から、リモート デバッガーを実行する最も効率的なができます。 詳細については、次を参照してください。[ファイル共有からのリモート デバッガーの実行](../debugger/remote-debugging.md#fileshare_msvsmon)です。
  
## <a name="BKMK_setup"></a> リモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 必要があるその他のユーザーのアクセス許可を追加または変更した場合、認証モード リモート デバッガーのポート番号を参照してください。[リモート デバッガーを構成する](../debugger/remote-debugging.md#configure_msvsmon)です。

## <a name="remote_cplusplus"></a> リモート デバッグ、Visual C プロジェクト  
 次の手順で名前とプロジェクトのパスは C:\remotetemp\MyMfc、およびリモート コンピューターの名前は**MJO DL**です。  
  
1.  という名前の MFC アプリケーションを作成する**mymfc です。**  
  
2.  簡単に達するの例の場合、アプリケーションのどこかにブレークポイントを設定**MainFrm.cpp**、先頭の`CMainFrame::OnCreate`します。  
  
3.  ソリューション エクスプ ローラーでクリックし、プロジェクトを右クリックして**プロパティ**です。 開く、**デバッグ**タブです。  
  
4.  設定、**起動するデバッガー**に**リモート Windows デバッガー**です。  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  プロパティに次の変更を適用します。  
  
    |設定|[値]|
    |-|-|  
    |リモート コマンド|C:\remotetemp\mymfc.exe|  
    |作業ディレクトリ|C:\remotetemp|  
    |リモート サーバー名|MJO DL:*portnumber*|  
    |接続|Windows 認証でリモート接続する|  
    |デバッガーの種類|ネイティブのみ|  
    |配置ディレクトリ|C:\remotetemp|  
    |追加の配置ファイル|C:\data\mymfcdata.txt|  
  
     (省略可能) 追加のファイルを展開する場合、両方のコンピューターでフォルダーが存在する必要があります。  
  
6.  ソリューション エクスプ ローラーでソリューションを右クリックして選択**Configuration Manager**です。  
  
7.  **デバッグ**構成では、select、**展開**チェック ボックスをオンします。  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  デバッグを開始 (**デバッグ > [デバッグ開始]**、または**f5 キーを押して**)。  
  
9. 実行可能ファイルが、リモート コンピューターに自動的に配置されます。  
  
10. メッセージが表示されたら、リモート コンピューターに接続するネットワーク資格情報を入力します。  
  
     必要な資格情報は、ネットワークのセキュリティの構成に固有です。 たとえば、ドメインのコンピューターにセキュリティ証明書を選択または、ドメイン名とパスワードを入力します。 非ドメイン コンピューターでは、可能性がありますを入力するマシン名と有効なユーザー アカウント名では、like **MJO-DL\name@something.com**、正しいパスワードとします。  
  
11. Visual Studio コンピューターで、実行がブレークポイントで停止したことを確認できるはずです。  
  
    > [!TIP]
    >  また、これらのファイルは別の手順でも配置できます。 **ソリューション エクスプ ローラーで、**を右クリックし、 **mymfc**ノードを選択し**展開**です。  
  
 アプリケーションで使用する必要がある、コード以外のファイルがある場合は、Visual Studio プロジェクトに含める必要があります。 追加のファイル用のプロジェクト フォルダーを作成 (で、**ソリューション エクスプ ローラー**をクリックして**追加 > 新しいフォルダー**)。フォルダーにファイルを追加 (で、**ソリューション エクスプ ローラー**をクリックして**追加 > 既存項目の**、してファイルを選択) します。 **プロパティ**ファイルごとに ページで、設定**出力ディレクトリにコピー**に**常にコピー**です。
  
## <a name="set-up-debugging-with-remote-symbols"></a>リモート シンボルを使用したデバッグのセットアップ 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)   
 [リモート デバッグ用に Windows ファイアウォールを構成します。](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [リモート デバッガーのポートの割り当て](../debugger/remote-debugger-port-assignments.md)   
 [リモートの IIS コンピューター上の ASP.NET のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)