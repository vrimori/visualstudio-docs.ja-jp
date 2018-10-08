---
title: リモート デバッグ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: hero-article
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc6cbcb4bba7e808a72ca389ab8ad9157e80375c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546553"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[リモート デバッグ](https://docs.microsoft.com/visualstudio/debugger/remote-debugging)します。  
  
別のコンピューターに配置されている Visual Studio アプリケーションをデバッグすることができます。  このデバッグを行うには、Visual Studio リモート デバッガーを使用します。  
  
 ここに記載された情報は、Windows デスクトップ アプリケーションと ASP.NET アプリケーションに適用されます。  Windows ストア アプリのリモート デバッグと Azure apps については、次を参照してください。 [Windows ストアと Azure アプリでのリモート デバッグ](#bkmk_winstoreAzure)します。  
  
## <a name="get-the-remote-tools"></a>リモート ツールを入手します。  
デバイスまたはデバッグをするかにするサーバーに直接リモート ツールは Visual Studio がインストールされていると、ホスト コンピューターからリモート ツールを入手することができますいずれかをダウンロードすることができます。

### <a name="to-download-and-install-the-remote-tools"></a>ダウンロードして、リモート ツールをインストールするには
  
1.  (Visual Studio を実行しているマシン) ではなくデバッグするデバイスまたはサーバー コンピューター、上の正しいバージョンを取得、リモート ツール。

    |Version|リンク|メモ|
    |-|-|-|
    |Visual Studio 2015 更新プログラム 3|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|メッセージが表示されたら、無料の Visual Studio Dev Essentials のグループに参加またはのみ、有効な Visual Studio サブスクリプションでサインインすることができます。 必要な場合は、リンクを再度開きますし。 常に、デバイスのオペレーティング システム (x 86、x64、または ARM バージョン) に一致するバージョンをダウンロードします。|
    |(古い) の visual Studio 2015|[リモート ツール](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|メッセージが表示されたら、無料の Visual Studio Dev Essentials のグループに参加またはのみ、有効な Visual Studio サブスクリプションでサインインすることができます。 必要な場合は、リンクを再度開きますし。|
    |Visual Studio 2013|[リモート ツール](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 のドキュメント内のページをダウンロードします。|
    |Visual Studio 2012|[リモート ツール](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 のドキュメント内のページをダウンロードします。|
  
2.  [ダウンロード] ページで、オペレーティング システム (x 86、x64、または ARM バージョン) に一致するバージョンのツールを選択し、リモート ツールをダウンロードします。
  
    > [!IMPORTANT]
    >  Visual Studio のバージョンに一致する remote tools の最新バージョンをインストールすることをお勧めします。 一致しないバージョンは推奨されません。  
    >   
    >  さらをインストールするオペレーティング システムと同じアーキテクチャを持つリモート ツールをインストールする必要があります。 つまりの 32 ビット アプリケーションをデバッグするかどうか、64 ビットのオペレーティング システムを実行しているリモート コンピューター、リモート コンピューターでリモート ツールの 64 ビット バージョンをインストールする必要があります。  
  
3.  実行可能ファイルのダウンロードが完了したら、アプリケーションをリモート コンピューターにインストールするための指示に従います。 参照してください[セットアップ手順](#bkmk_setup)

リモートのコンピューターにリモート デバッガー (msvsmon.exe) をコピーし、実行しようとする場合がありますが、**リモート デバッガー構成ウィザード**(**rdbgwiz.exe**) をダウンロードする場合にのみがインストールされている、ツール、およびするは、特にリモート デバッガーをサービスとして実行する場合に、後で構成ウィザードを使用する必要があります。 詳細については、次を参照してください。 [(省略可能) 構成サービスとしてリモート デバッガー](#bkmk_configureService)以下。

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>ファイル共有からリモート デバッガーを実行するには

リモート デバッガーを検索することができます (**msvsmon.exe**) Visual Studio 2015 Community、Professional、または Enterprise が既にインストールされているコンピューターでします。 多くのシナリオでは、リモート デバッグをセットアップする最も簡単な方法ではファイル共有からリモート デバッガー (msvsmon.exe) を実行します。 使用量の制限については、リモート デバッガーのヘルプ ページを参照してください (**ヘルプ/使用状況**リモート デバッガーで)。

1. 検索**msvsmon.exe**で Visual Studio のバージョンに一致するディレクトリ。 Visual Studio 2015。

      **Program files \microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program files \microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. 共有、**リモート デバッガー** Visual Studio コンピューター上のフォルダー。

3. リモートのコンピューターで実行して**msvsmon.exe**します。 に従って、[セットアップ手順](#bkmk_setup)します。

> [!TIP] 
> コマンド ライン インストールおよびコマンド ライン リファレンスでは、ヘルプ ページをご覧ください**msvsmon.exe** 」と入力して``msvsmon.exe /?``で Visual Studio がインストールされているコンピューターでコマンドラインで (に移動または**ヘルプ/使用状況**リモート デバッガーで)。

  
## <a name="supported-operating-systems"></a>Supported Operating Systems  
 リモート コンピューターで次のいずれかのオペレーティング システムが実行されている必要があります。  
  
-   Windows 10  
  
-   Windows 8 または 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 または Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2、Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>サポートされているハードウェア構成  
  
-   1.6 GHz 以上の高速プロセッサ  
  
-   1 GB の RAM (仮想マシン上で実行されている場合は 1.5 GB)  
  
-   1 GB のハード ディスク空き容量  
  
-   5400 RPM のハード ドライブ  
  
-   1024 x 768 以上のディスプレイ解像度の DirectX 9 対応ビデオ カード  
  
## <a name="network-configuration"></a>ネットワーク構成  
 リモート コンピューターと Visual Studio コンピューターは、ネットワーク、ワークグループ、またはホームグループを介して接続されているか、あるいはイーサネット ケーブルによって直接接続されている必要があります。 インターネットを介したデバッグはサポートされません。  
  
## <a name="bkmk_setup"></a>リモート デバッガーを設定します。  
 リモート コンピューターに対する管理アクセス許可が必要です。  
  
1.  リモート デバッガー アプリケーションを探します。 ([スタート] メニューを開き、検索**リモート デバッガー**)。
  
     リモート サーバーでリモート デバッガーを実行している場合は、リモート デバッガーのアプリを右クリックし、選択**管理者として実行**(または、サービスとしてリモート デバッガーを実行することができます)。場合を実行して、リモート サーバーではない、通常開始だけです。
  
3.  リモート ツールを起動すると、最初に (またはそれを構成する前に)、**リモート デバッグの構成**ダイアログ ボックスが表示されます。  
  
     ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Windows サービスの API が、(これは、Windows Server 2008 R2 でのみ発生します) もインストールされていない場合は、選択、**インストール**ボタンをクリックします。  
  
5.  リモート ツールで利用される、使用するネットワークの種類を選択します。 少なくとも 1 つのネットワークの種類を選択する必要があります。 コンピューターがドメインを介して接続されている場合は、最初の項目を選択する必要があります。 コンピューターがワークグループまたはホーム グループを介して接続されている場合は、必要に応じて、2 番目または 3 番目の項目を選択する必要があります。  
  
6.  選択**のリモート デバッグ構成**ファイアウォールを構成し、ツールを起動します。  
  
7.  構成が完了すると、リモート デバッガーのウィンドウが表示されます。
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     接続のリモート デバッガーが待機しているようになりました。 サーバー名をメモしておき、Visual Studio での構成後で必要があるために、表示されている数値をポートします。  
  
 デバッグとリモート デバッガーを停止する必要が終了したら、クリックして**ファイル]/[終了**ウィンドウ。 再起動することができます、**開始**メニューまたはコマンドラインから。  
  
 **\<Visual Studio のインストール ディレクトリ > \Common7\IDE\Remote Debugger\\< x86、x64、または Appx\msvsmon.exe**します。  
  
## <a name="configure-the-remote-debugger"></a>リモート デバッガーの構成  
 リモート デバッガーを初めて起動した後、リモート デバッガーの構成の一部を変更できます。
  
-   リモート デバッガーに接続するには、他のユーザーを有効にするには、**ツール/アクセス許可**します。 アクセス許可を付与または拒否するには、管理者特権が必要です。

    > [!IMPORTANT]
    > Visual Studio コンピューターを使用しているユーザー アカウントとは異なるユーザー アカウントでリモート デバッガーを実行することができますが、リモート デバッガーのアクセス許可を別のユーザー アカウントを追加する必要があります。 

     または、使用してコマンドラインからリモート デバッガーを起動、 **/allow\<ユーザー名 >** パラメーター: **msvsmon/allow \< username@computer>** します。
  
-   認証モードまたはポート番号を変更するかリモート ツールのタイムアウト値を指定する: 選択**ツール/オプション**します。  
  
     既定で使用されるポート番号の一覧については、次を参照してください。 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)します。  
  
     > [!WARNING]
>  リモート ツールを [認証なし] モードで実行することも選択できますが、このモードの使用は避けることを強く推奨します。 このモードで実行した場合、ネットワーク セキュリティはまったく提供されません。 [認証なし] モードは、ネットワークに悪意のあるコードや悪意のあるトラフィックのリスクがないことが確実である場合にのみ選択してください。

##  <a name="bkmk_configureService"></a> (省略可能)サービスとしてリモート デバッガーを構成します。
 ASP.NET およびその他のサーバー環境でデバッグ、リモート デバッガーを管理者として実行かを常に実行する場合は、サービスとしてリモート デバッガーを実行します。
  
 サービスとしてリモート デバッガーを構成するには、以下の手順を実行します。  
  
1.  **リモート デバッガー構成ウィザード** (rdbgwiz.exe) を見つけます (このアプリケーションは、リモート デバッガーとは別のアプリケーションです)。このアプリケーションは、リモート ツールをインストールした場合にのみ入手でき、 Visual Studio と共にはインストールされません。  
  
2.  構成ウィザードの実行を開始します。 最初のページが表示されたら、 **[次へ]** をクリックします。  
  
3.  **[Visual Studio 2015 リモート デバッガー サービスを実行する]** チェック ボックスをオンにします。  
  
4.  ユーザー アカウントの名前とパスワードを追加します。  
  
     このアカウントに、 **[サービスとしてログオン]** のユーザー権限を追加することが必要になる場合があります。 ( **ローカル セキュリティ ポリシー** (secpol.msc) を **[スタート]** ページまたはウィンドウで、あるいはコマンド プロンプトに「 **secpol** 」と入力して見つけます。 ウィンドウが表示されたら、 **[ユーザー権利の割り当て]** をダブルクリックし、右ペインで **[サービスとしてログオン]** を見つけます。 これをダブルクリックします。 ユーザー アカウントを追加、**プロパティ**ウィンドウをクリックします**OK**)。**[次へ]** をクリックします。  
  
5.  リモート ツールが通信するネットワークの種類を選択します。 少なくとも 1 つのネットワークの種類を選択する必要があります。 コンピューターがドメインを介して接続されている場合は、最初の項目を選択する必要があります。 コンピューターがワークグループまたはホーム グループを介して接続されている場合は、2 番目または 3 番目の項目を選択する必要があります。 **[次へ]** をクリックします。  
  
6.  サービスを開始できた場合は、「 **Visual Studio リモート デバッガー構成ウィザードは正常に完了しました**」と表示されます。 サービスを開始できなかった場合は、「 **Visual Studio リモート デバッガー構成ウィザードを完了できませんでした**」と表示されます。 このページには、サービスを開始するために従う必要があるヒントもいくつか提供されます。  
  
7.  **[完了]** をクリックします。  
  
 この時点で、リモート デバッガーはサービスとして実行されています。 これを確認するには、 **[コントロール パネル] / [サービス]** に移動して **[Visual Studio 2015 リモート デバッガー]** を探します。  
  
 リモート デバッガー サービスは、 **[コントロール パネル] / [サービス]** で停止してから開始することができます。  

## <a name="remote-debug-an-aspnet-application"></a>ASP.NET アプリケーションのリモート デバッグ  
 IIS が実行されているリモート コンピューターに ASP.NET アプリケーションを配置する手順は、オペレーティング システムと IIS のバージョンによって異なります。 IIS 7.5 または以降にインストールされているを参照してください、Windows Server 2008 または Windows Server 2012 を実行しているリモートのコンピューター [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)します。
 
 ASP.NET Core アプリをデバッグする場合を参照してください[IIS への発行](https://docs.asp.net/en/latest/publishing/iis.html)します。 IIS で ASP.NET Core の発行には、さまざまな手順が必要です。 リモート接続したり、ASP.NET Core アプリを正常に発行した後、デバッグ[他の ASP.NET アプリと同様](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)にアタッチする必要があるプロセスは w3wp.exe ではなく dnx.exe 点を除き、します。

## <a name="remote-debug-a-visual-c-project"></a>Visual C++ プロジェクトのリモート デバッグ  
 次の手順で名前と、プロジェクトのパスは C:\remotetemp\MyMfc、およびリモート コンピューターの名前は**MJO DL**します。  
  
1.  という名前の MFC アプリケーションの作成**mymfc します。**  
  
2.  例では、簡単に到達したアプリケーションのどこかにブレークポイントを設定**MainFrm.cpp**、先頭の`CMainFrame::OnCreate`します。  
  
3.  ソリューション エクスプ ローラーでクリックし、プロジェクトを右クリックして**プロパティ**します。 開く、**デバッグ**タブ。  
  
4.  設定、**起動するデバッガー**に**リモート Windows デバッガー**します。  
  
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
  
6.  ソリューション エクスプ ローラーでソリューションを右クリックし、選択**Configuration Manager**します。  
  
7.  **デバッグ**構成では、選択、**デプロイ**チェック ボックスをオンします。  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  デバッグを開始 (**デバッグ]/[デバッグの開始**、または**F5**)。  
  
9. 実行可能ファイルが、リモート コンピューターに自動的に配置されます。  
  
10. メッセージが表示されたら、リモート マシンに接続するネットワーク資格情報を入力します。  
  
     必要な資格情報は、ネットワークのセキュリティの構成に固有です。 たとえば、ドメインのコンピューターでセキュリティ証明書を選択または、ドメイン名とパスワードを入力します。 非ドメイン コンピューターで、可能性がありますを入力する、マシン名と有効なユーザー アカウント名では、このような**MJO-DL\name@something.com**、正しいパスワードと共にします。  
  
11. Visual Studio コンピューターで、実行がブレークポイントで停止したことを確認できるはずです。  
  
    > [!TIP]
    >  また、これらのファイルは別の手順でも配置できます。 **ソリューション エクスプ ローラー**を右クリックし、 **mymfc**ノード選び、**デプロイ**します。  
  
 アプリケーションで使用する必要がある、コード以外のファイルがある場合は、Visual Studio プロジェクトに含める必要があります。 追加ファイル用のプロジェクト フォルダーの作成 (で、**ソリューション エクスプ ローラー**、 をクリックして**追加/新しいフォルダー**)。フォルダーにファイルを追加して (で、**ソリューション エクスプ ローラー**、 をクリックして**追加/既存の項目**ファイルを選択します。)。 **プロパティ**ファイルごとに ページで、設定**出力ディレクトリにコピー**に**常にコピー**します。  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Visual C# プロジェクトまたは Visual Basic プロジェクトのリモート デバッグ  
 デバッガーでは、Visual C# または Visual Basic のデスクトップ アプリケーションをリモート コンピューターに配置できませんが、次のようにリモートからそれらのデスクトップ アプリケーションをデバッグすることはできます。 次の手順では、という名前のコンピューターでデバッグする場合を前提と**MJO DL**の前の図に示すようにします。
  
1.  という名前の WPF プロジェクトの作成**MyWpf**します。  
  
2.  ブレークポイントをコード内の達しやすい任意の箇所に設定します。  
  
     たとえば、ブレークポイントをボタン ハンドラーに設定できます。 これを行うには、MainWindow.xaml をし、ツールボックスからボタン コントロールを追加のハンドラーを開く ボタンをダブルクリックします。
  
3.  ソリューション エクスプ ローラーでプロジェクトを右クリックし、選択**プロパティ**します。  
  
4.  **プロパティ**ページで、選択、**デバッグ**タブ。  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  確認、**作業ディレクトリ**テキスト ボックスが空です。  
  
6.  選択**リモート コンピューターの使用**、および種類**MJO-DL:4020**テキスト ボックスにします。 (4020 はリモート デバッガー ウィンドウに表示されるポート番号) です。  
  
7.  必ず**ネイティブ コードのデバッグを有効にする**が選択されていません。  
  
8.  プロジェクトをビルドします。  
  
9. 同じパスであるリモート コンピューター上のフォルダーを作成、**デバッグ**Visual Studio コンピューター上のフォルダー: **\<ソース パス > \MyWPF\MyWPF\bin\Debug**します。  
  
10. 上で作成した実行可能ファイルを、Visual Studio コンピューターから、リモート コンピューター上の新しく作成したフォルダーにコピーします。
  
    > [!CAUTION]
    >  コードまたは再構築に変更しないでください (または、この手順を繰り返す必要があります)。 リモート コンピューターにコピーした実行可能ファイルは、ローカルのソースとシンボルに正確に一致している必要があります。

    プロジェクトを手動でコピー、Xcopy、Robocopy、Powershell、またはその他のオプションを使用できます。
  
11. リモート デバッガーが、ターゲット コンピューターで実行されていることを確認します。 (そうでない場合は検索**リモート デバッガー**で、**開始**メニュー。 ) 次のようなリモート デバッガーのウィンドウが表示されます。  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Visual Studio でデバッグを開始 (**デバッグ]/[デバッグの開始**、または**F5**)。  
  
13. メッセージが表示されたら、リモート マシンに接続するネットワーク資格情報を入力します。  
  
     必要な資格情報は、ネットワークのセキュリティ構成によって異なります。 たとえば、ドメインのコンピューターで、ドメイン名とパスワードを入力できます。 非ドメイン コンピューターで、可能性がありますを入力する、マシン名と有効なユーザー アカウント名では、このような**MJO-DL\name@something.com**、正しいパスワードと共にします。

     WPF アプリケーションのメイン ウィンドウがリモート コンピューター上で開いていることを確認できるはずです。
  
14. 必要に応じては、ブレークポイントにヒットするアクションを実行します。 ブレークポイントがアクティブになっていることを確認できるはずです。 ブレークポイントがアクティブでない場合、アプリケーションのシンボルが読み込まれていません。 Retry、およびシンボルの読み込みについての情報を取得しでそれらのトラブルシューティング方法がうまくいかない場合[Understanding シンボル ファイルおよび Visual Studio のシンボルの設定](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx)します。
  
15. Visual Studio コンピューターで、実行がブレークポイントで停止したことを確認できるはずです。
  
 アプリケーションで使用する必要がある、コード以外のファイルがある場合は、Visual Studio プロジェクトに含める必要があります。 追加ファイル用のプロジェクト フォルダーの作成 (で、**ソリューション エクスプ ローラー**、 をクリックして**追加/新しいフォルダー**)。フォルダーにファイルを追加して (で、**ソリューション エクスプ ローラー**、 をクリックして**追加/既存の項目**ファイルを選択します。)。 **プロパティ**ファイルごとに ページで、設定**出力ディレクトリにコピー**に**常にコピー**します。
  
## <a name="set-up-debugging-with-remote-symbols"></a>リモート シンボルを使用したデバッグのセットアップ  
 Visual Studio コンピューターで生成したシンボルを使用して、コードをデバッグすることができます。 リモート デバッガーのパフォーマンスは、ローカル シンボルを使用すると大幅に向上します。  リモート シンボルを使用する必要がある場合、リモート コンピューター上のシンボルを検索するように、リモート デバッグ モニターに指示する必要があります。  
  
 Visual Studio 2013 Update 2 以降、msvsmon コマンド ライン スイッチを使用して、マネージ コードのリモート シンボルを使用します。 `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 詳細については、リモート デバッグのヘルプを参照してください (キーを押して**F1**リモート デバッガー ウィンドウで**ヘルプ/使用状況**)。 詳細についてを検索する[.NET リモート シンボルの読み込みの変更では、Visual Studio 2012 および 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Windows ストアと Azure アプリでのリモート デバッグ  
 Windows ストア アプリでのリモート デバッグについては、次を参照してください。[デバッグし、Visual Studio からリモート デバイス上の Windows ストア アプリをテスト](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx)します。  
  
 Azure でのデバッグ方法の詳細については、次のトピックのいずれかを参照してください。  
  
-   [Visual Studio での仮想マシンまたはクラウド サービスのデバッグ](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Visual Studio で .NET バックエンドのデバッグ](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Azure Websites でのリモート デバッグの概要 ([パート 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/)、[パート 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/)、[パート 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/))。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)   
 [リモート デバッグ用の Windows ファイアウォールを構成します。](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [リモート デバッガーのポートの割り当て](../debugger/remote-debugger-port-assignments.md)   
 [リモートの IIS コンピューター上の ASP.NET のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)



