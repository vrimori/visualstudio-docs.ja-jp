---
title: リモート デバッグ |Microsoft Docs
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
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
ms.openlocfilehash: 84ba15ddbfdb6e3bbcf7a9f7c3ee3dd7e0f89c9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866336"
---
# <a name="remote-debugging"></a>Remote Debugging
別のコンピューターに配置されている Visual Studio アプリケーションをデバッグすることができます。 このデバッグを行うには、Visual Studio リモート デバッガーを使用します。

リモート デバッグに関する詳細な手順については、これらのトピックを参照してください。

|シナリオ|リンク|
|-|-|-|
|Azure App Service|[スナップショット デバッガー](../debugger/debug-live-azure-applications.md)または[Azure での ASP.NET のリモート デバッグ](../debugger/remote-debugging-azure.md)|
|Azure 仮想マシン|[Azure での ASP.NET のリモート デバッグ](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Azure Service Fabric アプリケーションをデバッグします。](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[ASP.NET Core のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)または[リモート デバッグの ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# または Visual Basic|[C# プロジェクトまたは Visual Basic プロジェクトのリモート デバッグ](../debugger/remote-debugging-csharp.md)|
|C++|[C++ Project プロジェクトのリモート デバッグ](../debugger/remote-debugging-cpp.md)|
|ユニバーサル Windows アプリ (UWP)|[リモート コンピューターで UWP アプリを実行](../debugger/run-windows-store-apps-on-a-remote-machine.md)または[インストールされているアプリ パッケージのデバッグ](../debugger/debug-installed-app-package.md)|

だけをダウンロードして、リモート デバッガーをインストールして、実際のシナリオについて、追加の手順は不要する場合、はこの記事の手順に従います。

## <a name="download-and-install-the-remote-tools"></a>リモート ツールのダウンロードおよびインストール

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements_msvsmon"></a> 要件

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a> (省略可能)ファイル共有からリモート デバッガーを実行するには

リモート デバッガーを検索することができます (*msvsmon.exe*) Visual Studio Community、Professional、または Enterprise が既にインストールされているコンピューターでします。 シナリオによっては、リモート デバッグをセットアップする最も簡単な方法では、ファイル共有からリモート デバッガー (msvsmon.exe) を実行します。 使用量の制限については、リモート デバッガーのヘルプ ページを参照してください (**ヘルプ > 使用状況**リモート デバッガーで)。

1. 検索*msvsmon.exe*で Visual Studio のバージョンに一致するディレクトリ。 Visual Studio enterprise 2017。

      *Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

      *Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

2. 共有、**リモート デバッガー** Visual Studio コンピューター上のフォルダー。

3. リモートのコンピューターで実行して*msvsmon.exe*共有フォルダーから。 に従って、[セットアップ手順](#bkmk_setup)します。

> [!TIP]
> コマンド ライン インストールおよびコマンド ライン リファレンスでは、ヘルプ ページをご覧ください*msvsmon.exe* 」と入力して``msvsmon.exe /?``で Visual Studio がインストールされているコンピューターでコマンドラインで (に移動または**ヘルプ > 使用状況**リモート デバッガーで)。

## <a name="bkmk_setup"></a> リモート デバッガーのセットアップ

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> リモート デバッガーの構成
リモート デバッガーを初めて起動した後、リモート デバッガーの構成の一部を変更できます。

-   リモート デバッガーへの接続を選択するには、他のユーザーのアクセス許可を追加する必要がある場合**ツール > アクセス許可**します。 アクセス許可を付与または拒否するには、管理者特権が必要です。

     > [!IMPORTANT]
     > Visual Studio コンピューターを使用しているユーザー アカウントとは異なるユーザー アカウントでリモート デバッガーを実行することができますが、リモート デバッガーのアクセス許可を別のユーザー アカウントを追加する必要があります。

     または、使用してコマンドラインからリモート デバッガーを起動、 **/allow\<ユーザー名 >** パラメーター: **msvsmon/allow \< username@computer>** します。

-   認証モードや、ポート番号を変更したり、リモート ツールのタイムアウト値を指定する必要がある場合: 選択**ツール > オプション**します。

     既定で使用されるポート番号の一覧については、次を参照してください。 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)します。

     > [!WARNING]
     >  リモート ツールを [認証なし] モードで実行することも選択できますが、このモードの使用は避けることを強く推奨します。 このモードで実行した場合、ネットワーク セキュリティはまったく提供されません。 [認証なし] モードは、ネットワークに悪意のあるコードや悪意のあるトラフィックのリスクがないことが確実である場合にのみ選択してください。

##  <a name="bkmk_configureService"></a> (省略可能)サービスとしてリモート デバッガーを構成します。
ASP.NET およびその他のサーバー環境でデバッグ、リモート デバッガーを管理者として実行かを常に実行する場合は、サービスとしてリモート デバッガーを実行します。

 サービスとしてリモート デバッガーを構成するには、以下の手順を実行します。

1. **リモート デバッガー構成ウィザード** (rdbgwiz.exe) を見つけます (このアプリケーションは、リモート デバッガーとは別のアプリケーションです)。このアプリケーションは、リモート ツールをインストールした場合にのみ入手でき、 Visual Studio と共にはインストールされません。

2. 構成ウィザードの実行を開始します。 最初のページが表示されたら、 **[次へ]** をクリックします。

3. **[Visual Studio 2015 リモート デバッガー サービスを実行する]** チェック ボックスをオンにします。

4. ユーザー アカウントの名前とパスワードを追加します。

    追加する必要があります、**サービスとしてログオン**ユーザー権限をこのアカウント (検索**ローカル セキュリティ ポリシー** (secpol.msc) で、**開始**ページまたはウィンドウ (または型**secpol**コマンド プロンプトで)。 ウィンドウが表示されたら、 **[ユーザー権利の割り当て]** をダブルクリックし、右ペインで **[サービスとしてログオン]** を見つけます。 これをダブルクリックします。 ユーザー アカウントを **[プロパティ]** ウィンドウに追加して **[OK]** をクリックします)。 **[次へ]** をクリックします。

5. リモート ツールが通信するネットワークの種類を選択します。 少なくとも 1 つのネットワークの種類を選択する必要があります。 コンピューターがドメインを介して接続されている場合は、最初の項目を選択する必要があります。 コンピューターがワークグループまたはホーム グループを介して接続されている場合は、2 番目または 3 番目の項目を選択する必要があります。 **[次へ]** をクリックします。

6. サービスを開始できた場合は、「 **Visual Studio リモート デバッガー構成ウィザードは正常に完了しました**」と表示されます。 サービスを開始できなかった場合は、「 **Visual Studio リモート デバッガー構成ウィザードを完了できませんでした**」と表示されます。 このページには、サービスを開始するために従う必要があるヒントもいくつか提供されます。

7. **[完了]** をクリックします。

   この時点で、リモート デバッガーはサービスとして実行されています。 これを確認するには、**[コントロール パネル] > [サービス]** に移動して **[Visual Studio 2015 リモート デバッガー]** を探します。

   リモート デバッガー サービスは、**[コントロール パネル] > [サービス]** で停止してから開始することができます。

## <a name="set-up-debugging-with-remote-symbols"></a>リモート シンボルを使用したデバッグのセットアップ

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>関連項目

- [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)
- [Windows ファイアウォールをリモート デバッグ用に構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [リモート デバッガーのポートの割り当て](../debugger/remote-debugger-port-assignments.md)
- [リモート デバッグ、リモートの IIS コンピューター上の ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)