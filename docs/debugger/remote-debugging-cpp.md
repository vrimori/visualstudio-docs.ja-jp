---
title: Visual C プロジェクトのリモート デバッグ |Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
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
ms.openlocfilehash: 2778148c8762c74d1c836a6f5a1b1fd8c9387e12
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53884585"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>リモート Visual Studio での Visual C プロジェクトのデバッグ
別のコンピューター上の Visual Studio アプリケーションをデバッグ、インストールして、アプリを展開するコンピューターでリモート ツールを実行、Visual Studio からリモート コンピューターに接続して、デプロイして、アプリを実行するプロジェクトを構成します。

![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

リモート デバッグのユニバーサル Windows アプリ (UWP) の詳細については、次を参照してください。[インストール済みのアプリ パッケージをデバッグ](debug-installed-app-package.md)します。

## <a name="requirements"></a>要件

リモート デバッガーは Windows 7 でサポートされている以降 (phone ではありません) と Windows Server の Windows Server 2008 Service Pack 2 以降のバージョン。 要件の完全な一覧を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)します。

> [!NOTE]
> プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での高待機時間またはダイヤルアップ、インターネットなどの低帯域幅接続経由またはインターネット経由でのデバッグは使用しないでと失敗は、ある非常に遅く。
  
## <a name="download-and-install-the-remote-tools"></a>リモート ツールのダウンロードおよびインストール

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
> [!TIP]
> 一部のシナリオでは、ファイル共有からリモート デバッガーを実行する最も効率的なができます。 詳細については、次を参照してください。[ファイル共有からリモート デバッガーを実行](../debugger/remote-debugging.md#fileshare_msvsmon)します。
  
## <a name="BKMK_setup"></a> リモート デバッガーのセットアップ

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 必要がある追加のユーザーのアクセス許可を追加または変更した場合、認証モード、リモート デバッガーのポート番号を参照してください。[リモート デバッガーを構成する](../debugger/remote-debugging.md#configure_msvsmon)します。

## <a name="remote_cplusplus"></a> Visual C++ プロジェクトのリモート デバッグ  
 次の手順で名前と、プロジェクトのパスは C:\remotetemp\MyMfc、およびリモート コンピューターの名前は**MJO DL**します。  
  
1. **mymfc** という名前の MFC アプリケーションを作成します。  
  
2. ブレークポイントを、アプリケーション内の達しやすい任意の箇所 (たとえば、`CMainFrame::OnCreate` の開始時の **MainFrm.cpp**) に設定します。  
  
3. ソリューション エクスプ ローラーでクリックし、プロジェクトを右クリックして**プロパティ**します。 **[デバッグ]** タブを開きます。  
  
4. **[起動するデバッガー]** を **[リモート Windows デバッガー]** に設定します。  
  
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
  
7. **[デバッグ]** 構成の **[配置]** チェック ボックスをオンにします。  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. デバッグを開始します (**[デバッグ] > [デバッグの開始]**、または **F5** キー)。  
  
9. 実行可能ファイルが、リモート コンピューターに自動的に配置されます。  
  
10. メッセージが表示されたら、リモート マシンに接続するネットワーク資格情報を入力します。  
  
     必要な資格情報は、ネットワークのセキュリティの構成に固有です。 たとえば、ドメインのコンピューターでセキュリティ証明書を選択または、ドメイン名とパスワードを入力します。 非ドメイン コンピューターで、可能性がありますを入力する、マシン名と有効なユーザー アカウント名では、このような<strong>MJO-DL\name@something.com</strong>、正しいパスワードと共にします。  
  
11. Visual Studio コンピューターで、実行がブレークポイントで停止したことを確認できるはずです。  
  
    > [!TIP]
    >  また、これらのファイルは別の手順でも配置できます。 **ソリューション エクスプローラー**で、**[mymfc]** ノードを右クリックして **[配置]** を選択します。  
  
    アプリケーションで使用する必要がある、コード以外のファイルがある場合は、Visual Studio プロジェクトに含める必要があります。 追加のファイル用のプロジェクト フォルダーを作成します (**ソリューション エクスプローラー**で、**[追加] > [新しいフォルダー]** をクリックします)。次にファイルをそのフォルダーに追加します (**ソリューション エクスプローラー**で、**[追加] > [既存の項目]** の順にクリックしてからファイルを選択します)。 ファイルごとの **[プロパティ]** ページで、**[出力ディレクトリにコピー]** を **[常にコピーする]** に設定します。
  
## <a name="set-up-debugging-with-remote-symbols"></a>リモート シンボルを使用したデバッグのセットアップ 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>「  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)   
 [Windows ファイアウォールをリモート デバッグ用に構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [リモートの IIS コンピューター上の ASP.NET のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)