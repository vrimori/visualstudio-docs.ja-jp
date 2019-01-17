---
title: リモート デバッグ、C#または VB プロジェクト |Microsoft Docs
ms.custom:
- remotedebugging"=
- seodec18
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
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3f923d145d52ac86ad99c9aecd9875be4f78d4ef
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270113"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>リモート Visual Studio で c# または Visual Basic プロジェクトのデバッグ
別のコンピューターに展開されている Visual Studio アプリケーションをデバッグするには、インストールし、アプリをデプロイしたコンピューターでリモート ツールを実行、Visual Studio からリモート コンピューターに接続するプロジェクトを構成し、アプリを実行します。

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
  
## <a name="remote_csharp"></a> プロジェクトのリモート デバッグ
デバッガーでは、Visual C# または Visual Basic のデスクトップ アプリケーションをリモート コンピューターに配置できませんが、次のようにリモートからそれらのデスクトップ アプリケーションをデバッグすることはできます。 次の手順では、という名前のコンピューターでデバッグする場合を前提と**MJO DL**の次の図に示すようにします。
  
1. **MyWpf** という名前の WPF プロジェクトを作成します。  
  
2. ブレークポイントをコード内の達しやすい任意の箇所に設定します。  
  
    たとえば、ブレークポイントをボタン ハンドラーに設定できます。 これを行うには、MainWindow.xaml をし、ツールボックスからボタン コントロールを追加のハンドラーを開く ボタンをダブルクリックします。
  
3. ソリューション エクスプ ローラーでプロジェクトを右クリックし、選択**プロパティ**します。  
  
4. **[プロパティ]** ページで、**[デバッグ]** タブをクリックします。  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. **[作業ディレクトリ]** テキスト ボックスが空であることを確認してください。  
  
6. 選択**リモート コンピューターの使用**、および種類**MJO-DL:4022**テキスト ボックスにします。 (4022 は、リモート デバッガー ウィンドウに表示されるポート番号です。 ポート番号をインクリメントで Visual Studio の各バージョン 2)。
  
7. **[ネイティブ コードのデバッグを有効にする]** がオフであることを確認します。  
  
8. プロジェクトをビルドします。  
  
9. Visual Studio コンピューター上の **Debug** フォルダー (**\<ソース パス>\MyWPF\MyWPF\bin\Debug**) と同じパスのフォルダーをリモート コンピューター上に作成します。  
  
10. 上で作成した実行可能ファイルを、Visual Studio コンピューターから、リモート コンピューター上の新しく作成したフォルダーにコピーします。
  
    > [!CAUTION]
    >  コードまたは再構築に変更しないでください (または、この手順を繰り返す必要があります)。 リモート コンピューターにコピーした実行可能ファイルは、ローカルのソースとシンボルに正確に一致している必要があります。

    プロジェクトを手動でコピー、Xcopy、Robocopy、Powershell、またはその他のオプションを使用できます。
  
11. リモート デバッガーが、ターゲット コンピューターで実行されていることを確認 (そうでない場合は検索**リモート デバッガー**で、**開始**メニュー)。 次のようなリモート デバッガー ウィンドウが表示されます。  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Visual Studio でデバッグを開始します (**[デバッグ] > [デバッグの開始]**、または **F5** キー)。  
  
13. メッセージが表示されたら、リモート マシンに接続するネットワーク資格情報を入力します。  
  
     必要な資格情報は、ネットワークのセキュリティ構成によって異なります。 たとえば、ドメインのコンピューターで、ドメイン名とパスワードを入力できます。 非ドメイン コンピューターで、可能性がありますを入力する、マシン名と有効なユーザー アカウント名では、このような<strong>MJO-DL\name@something.com</strong>、正しいパスワードと共にします。

     WPF アプリケーションのメイン ウィンドウがリモート コンピューター上で開いていることを確認できるはずです。
  
14. 必要に応じては、ブレークポイントにヒットするアクションを実行します。 ブレークポイントがアクティブになっていることを確認できるはずです。 いない場合は、アプリケーションのシンボルが読み込まれていません。 Retry、およびシンボルの読み込みについての情報を取得しでそれらのトラブルシューティング方法がうまくいかない場合[Understanding シンボル ファイルおよび Visual Studio のシンボルの設定](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)します。
  
15. Visual Studio コンピューターで、実行がブレークポイントで停止したことを確認できるはずです。
  
    アプリケーションで使用する必要があるすべての非コード ファイルがある場合は、Visual Studio プロジェクトに追加する必要があります。 追加のファイル用のプロジェクト フォルダーを作成します (**ソリューション エクスプローラー**で、**[追加] > [新しいフォルダー]** をクリックします)。 次にファイルをそのフォルダーに追加します (**ソリューション エクスプローラー**で、**[追加] > [既存の項目]** の順にクリックしてからファイルを選択します)。 ファイルごとの **[プロパティ]** ページで、**[出力ディレクトリにコピー]** を **[常にコピーする]** に設定します。

## <a name="set-up-debugging-with-remote-symbols"></a>リモート シンボルを使用したデバッグのセットアップ 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>「  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガーでのはじめに](../debugger/debugger-feature-tour.md)   
 [Windows ファイアウォールをリモート デバッグ用に構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [リモートの IIS コンピューター上の ASP.NET のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)