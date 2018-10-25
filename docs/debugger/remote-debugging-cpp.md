---
title: Visual C プロジェクトのリモート デバッグ |Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 4677380081aaa0ac79f589ea7594f19f78750613
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844108"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>リモート Visual Studio での Visual C プロジェクトのデバッグ
別のコンピューター上の Visual Studio アプリケーションをデバッグ、インストールして、アプリを展開するコンピューターでリモート ツールを実行、Visual Studio からリモート コンピューターに接続して、デプロイして、アプリを実行するプロジェクトを構成します。

![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

リモート デバッグのユニバーサル Windows アプリ (UWP) の詳細については、次を参照してください。[インストール済みのアプリ パッケージをデバッグ](debug-installed-app-package.md)します。

## <a name="requirements"></a>必要条件

リモート デバッガーは Windows 7 でサポートされている以降 (phone ではありません) と Windows Server の Windows Server 2008 Service Pack 2 以降のバージョン。 要件の完全な一覧を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)します。

> [!NOTE]
> プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での高待機時間またはダイヤルアップ、インターネットなどの低帯域幅接続経由またはインターネット経由でのデバッグは使用しないでと失敗は、ある非常に遅く。
  
## <a name="download-and-install-the-remote-tools"></a>ダウンロードして、リモート ツールのインストール

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
> [!TIP]
> 一部のシナリオでは、ファイル共有からリモート デバッガーを実行する最も効率的なができます。 詳細については、次を参照してください。[ファイル共有からリモート デバッガーを実行](../debugger/remote-debugging.md#fileshare_msvsmon)します。
  
## <a name="BKMK_setup"></a> リモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 必要がある追加のユーザーのアクセス許可を追加または変更した場合、認証モード、リモート デバッガーのポート番号を参照してください。[リモート デバッガーを構成する](../debugger/remote-debugging.md#configure_msvsmon)します。

## <a name="remote_cplusplus"></a> Visual C プロジェクトのリモート デバッグ  
 次の手順で名前と、プロジェクトのパスは C:\remotetemp\MyMfc、およびリモート コンピューターの名前は**MJO DL**します。  
  
1. という名前の MFC アプリケーションの作成**mymfc します。**  
  
2. 例では、簡単に到達したアプリケーションのどこかにブレークポイントを設定**MainFrm.cpp**、先頭の`CMainFrame::OnCreate`します。  
  
3. ソリューション エクスプ ローラーでクリックし、プロジェクトを右クリックして**プロパティ**します。 開く、**デバッグ**タブ。  
  
4. 設定、**起動するデバッガー**に**リモート Windows デバッガー**します。  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. プロパティに次の変更を適用します。  
  
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
  
6. ソリューション エクスプ ローラーでソリューションを右クリックし、選択**Configuration Manager**します。  
  
7. **デバッグ**構成では、選択、**デプロイ**チェック ボックスをオンします。  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. デバッグを開始 (**デバッグ > [デバッグ開始]**、または**F5**)。  
  
9. 実行可能ファイルが、リモート コンピューターに自動的に配置されます。  
  
10. メッセージが表示されたら、リモート マシンに接続するネットワーク資格情報を入力します。  
  
     必要な資格情報は、ネットワークのセキュリティの構成に固有です。 たとえば、ドメインのコンピューターでセキュリティ証明書を選択または、ドメイン名とパスワードを入力します。 非ドメイン コンピューターで、可能性がありますを入力する、マシン名と有効なユーザー アカウント名では、このような<strong>MJO-DL\name@something.com</strong>、正しいパスワードと共にします。  
  
11. Visual Studio コンピューターで、実行がブレークポイントで停止したことを確認できるはずです。  
  
    > [!TIP]
    >  また、これらのファイルは別の手順でも配置できます。 **ソリューション エクスプ ローラー**を右クリックし、 **mymfc**ノード選び、**デプロイ**します。  
  
    アプリケーションで使用する必要がある、コード以外のファイルがある場合は、Visual Studio プロジェクトに含める必要があります。 追加ファイル用のプロジェクト フォルダーの作成 (で、**ソリューション エクスプ ローラー**、 をクリックして**追加 > 新しいフォルダー**)。フォルダーにファイルを追加して (で、**ソリューション エクスプ ローラー**、 をクリックして**追加 > 既存項目の**のファイルを選択します)。 **プロパティ**ファイルごとに ページで、設定**出力ディレクトリにコピー**に**常にコピー**します。
  
## <a name="set-up-debugging-with-remote-symbols"></a>リモート シンボルを使用したデバッグのセットアップ 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)   
 [リモート デバッグ用の Windows ファイアウォールを構成します。](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [リモートの IIS コンピューター上の ASP.NET のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)