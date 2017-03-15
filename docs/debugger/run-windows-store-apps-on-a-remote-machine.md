---
title: "リモート コンピューターでの Windows ストア アプリの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 43
---
# リモート コンピューターでの Windows ストア アプリの実行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Windows のみに適用されます](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Visual Studio リモート ツール アプリケーションを使用すると、Visual Studio を実行中のコンピューターから、他のデバイスで実行中の Windows ストア アプリを実行、デバッグ、プロファイリング、およびテストできます。 リモート デバイスでの実行は、Visual Studio コンピューターが Windows ストア アプリ固有の機能 \(タッチ、位置情報、物理的な方向など\) をサポートしていない場合に特に有効です。 このトピックでは、リモート セッションを構成および開始する手順について説明します。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 以下を学習できます。  
  
 [必要条件](#BKMK_Prerequisites)  
  
 [セキュリティ](#BKMK_Security)  
  
 [リモート デバイスに接続する方法](#BKMK_DirectConnect)  
  
 [リモート ツールのインストール](#BKMK_Installing_the_Remote_Tools)  
  
 [リモート デバッガー モニターの起動](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [リモート デバッガーの構成](#BKMK_ConfigureRemoteDebugger)  
  
 [リモート デバッグ用の Visual Studio プロジェクトの構成](#BKMK_ConnectVS)  
  
-   [C# プロジェクトと Visual Basic プロジェクト用のリモート デバイスの選択](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
-   [JavaScript プロジェクトと C++ プロジェクト用のリモート デバイスの選択](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
 [リモート デバッグ セッションの実行](#BKMK_RunRemoteDebug)  
  
##  <a name="BKMK_Prerequisites"></a> 必要条件  
 リモート デバイスでデバッグするには:  
  
-   リモート デバイスと Visual Studio コンピューターがネットワークを介して接続されている、またはイーサネット ケーブルによって直接接続されている必要があります。 インターネットを介したデバッグはサポートされません。  
  
-   リモート デバイスに開発者ライセンスがインストールされている必要があります。  
  
-   リモート デバイスがリモート デバッグ コンポーネントを実行している必要があります。  
  
-   インストール中にファイアウォールを構成するために、リモート デバイスの管理者である必要があります。 リモート デバッガーを実行するかリモート デバッガーに接続するために、リモート デバイスへのユーザー アクセスが必要です。  
  
##  <a name="BKMK_Security"></a> セキュリティ  
 既定では、リモート デバッガーは Windows 認証を使用します。  
  
> [!WARNING]
>  リモート デバッガーを認証なしモードで実行することも選択できますが、このモードの使用は避けることを強く推奨します。 このモードで実行した場合、ネットワーク セキュリティはまったく提供されません。 認証なしモードは、ネットワークに悪意のあるコードや悪意のあるトラフィックのリスクがないことが確実である場合のみ選択してください。  
  
##  <a name="BKMK_DirectConnect"></a> リモート デバイスに接続する方法  
 リモート デバイスに直接接続するには、標準イーサネット ケーブルを使用して Visual Studio コンピューターをデバイスに接続します。 デバイスにイーサネット ポートがない場合は、USB イーサネット アダプターを使用してケーブルを接続できます。  
  
##  <a name="BKMK_Installing_the_Remote_Tools"></a> リモート ツールのインストール  
  
> [!NOTE]
>  **バージョンおよび更新プログラム**  
>   
>  **Remote Tools for Visual Studio 2015** は、以前のバージョンの Visual Studio ではサポートされていません。  
>   
>  Visual Studio インストールの更新バージョンと一致する Remote Tools for Visual Studio 2015 の更新バージョンをインストールすることをお勧めします。  
>   
>  VS デバッガーは、VS 2015 と Remote Tools for VS 2015 のどのバージョンの組み合わせとも互換性があります。 ただし、Visual Studio の最新機能を使用するには、Visual Studio とリモート ツールの両方が最新バージョンである必要があります。  
>   
>  他の診断ツールでは、リモート ツールと Visual Studio の同じバージョンを必要とする場合があります。  
  
 **リモート デバイスへのリモート デバッグ コンポーネントのインストール**  
  
 Remote Tools のインストール プログラムを実行または保存するには、この表にあるリモート デバイスのオペレーティング システムに対応するいずれかのリンクをお選びください。  
  
### Visual Studio 2013  
  
|||||  
|-|-|-|-|  
|**更新プログラムのバージョン**|**X86**|**X64**|**ARM**|  
|**RTM**|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=320706)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=320707)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=320708)|  
|**Update 1**|[ダウンロード](http://go.microsoft.com/fwlink/?LinkID=386599)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkID=386600)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkID=386601)|  
|**更新プログラム 2**|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=393218)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=393217)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=393216)|  
|**Update 3**|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=403046)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=403047)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=403048)|  
|**Update 4**|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=512599)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=512600)|[ダウンロード](http://go.microsoft.com/fwlink/?LinkId=512601)|  
  
### Visual Studio 2015  
  
|||||  
|-|-|-|-|  
|**バージョン**|**X86**|**X64**|**ARM**|  
|**プレビュー**|[ダウンロード](http://download.microsoft.com/download/4/8/A/48A0EA60-6097-4BA5-B7D3-EAE49499E1FB/rtools_setup_x86.exe)|[ダウンロード](http://download.microsoft.com/download/4/8/A/48A0EA60-6097-4BA5-B7D3-EAE49499E1FB/rtools_setup_x64.exe)|[ダウンロード](http://download.microsoft.com/download/4/8/A/48A0EA60-6097-4BA5-B7D3-EAE49499E1FB/rtools_setup_arm.exe)|  
  
 インストール プログラムをダウンロードするか、すぐに実行することができます。 インストール プログラムを実行するときは、ライセンス条項に同意し、**\[インストール\]** をクリックします。  
  
 既定では、リモート デバッグ コンポーネントは **C:\\Program Files\\Microsoft Visual Studio 14.0\\Common7\\IDE\\Remote Debugger** フォルダーにインストールされます。  
  
##  <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> リモート デバッガー モニターの起動  
  
> [!NOTE]
>  リモート デバッガーで Visual Studio ホストとの通信ができるようにファイアウォールを構成するため、リモート デバッガーを初めて起動する際は、リモート デバイスの管理者である必要があります。  
  
 リモート ツールをインストールしたら、**スタート**画面で **\[リモート デバッガー\]** をクリックします。 リモート デバッガーを初めて起動すると、**\[リモート デバッグの構成\]** が表示されます。  
  
 **\[リモート デバッグの構成\]** ダイアログ ボックスで次の操作を行います。  
  
1.  Windows Web サービス API がインストールされていない場合は、**\[インストール\]** をクリックします。  
  
2.  **\[Windows ファイアウォールの構成\]** から、接続を許可するネットワークを選択します。 デバイスが現在接続されているネットワークだけが有効です。 少なくとも 1 つのネットワークを選択する必要があります。  
  
3.  **\[リモート デバッグの構成\]** をクリックしてファイアウォール オプションを設定し、リモート デバッガーを起動します。**\[Visual Studio リモート デバッグ モニタ\]** ダイアログ ボックスを開いて、リモート ツールへのアクセス許可をユーザーに付与し、他の詳細オプションを設定します。  
  
4.  **\[Visual Studio リモート デバッグ モニター\]** ダイアログ ボックスが表示されます。 このダイアログ ボックスから、リモート ツールへのアクセス許可をユーザーに付与し、他の詳細オプションを設定できます。  
  
##  <a name="BKMK_ConfigureRemoteDebugger"></a> リモート デバッガーの構成  
 リモート デバッガーの構成を変更するには 2 つのツールを使用します。  
  
1.  **\[Visual Studio リモート デバッグ モニター\]** の **\[ツール\]** メニュー:  
  
    1.  リモート デバッガーのポート番号、認証モード、またはタイムアウト間隔を変更するには、**\[オプション\]** を選択します。  
  
    2.  リモート デバッグのアクセス許可を持つユーザーを追加または削除するには、**\[アクセス許可\]** を選択します。  
  
        > [!NOTE]
        >  アクセス許可は、リモートでデバッグするすべてのユーザー アカウントに付与する必要があります。  
  
 リモート デバッガーの詳細オプションを設定するには、**リモート デバッガー構成ウィザード**を使用します。 ウィザードを開くには、スタート画面の**リモート デバッガー構成ウィザード** を選択します。  
  
1.  **Visual Studio リモート デバッガーの構成**ページでリモート デバッガーをサービスとして実行するように選択できます。 ほとんどの場合、サービスとして実行する必要はありません。  
  
2.  **\[Windows ファイアウォールをデバッグ用に構成します\]** ページで、リモート デバッガーに接続するネットワークの種類を追加または削除できます。 デバイスが現在接続されているネットワークだけが有効です。 少なくとも 1 つのネットワークを選択する必要があります。  
  
##  <a name="BKMK_ConnectVS"></a> リモート デバッグ用の Visual Studio プロジェクトの構成  
 プロジェクトのプロパティに、接続するリモート デバイスを指定します。 手順はプログラミング言語によって異なります。 リモート デバイスのネットワーク名を入力するか、\[リモート デバッガー接続の選択\] ダイアログ ボックスで選択できます。  
  
 ![&#91;Select Remote Debugger Connection&#93; &#40;リモート デバッガーの接続の選択&#41; ダイアログ ボックス](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
 ダイアログ ボックスには、Visual Studio コンピューターのローカル サブネット上にあるデバイスで、リモート デバッガーを実行中のデバイスだけが表示されます。  
  
> [!TIP]
>  リモート デバイスへの接続に問題がある場合は、デバイスの IP アドレスを入力してください。 デバイスの IP アドレスを確認するには、コマンド ウィンドウを開き、「**ipconfig**」と入力します。 IP アドレスは **IPv4 Address**として表示されます。  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> C\# プロジェクトと Visual Basic プロジェクト用のリモート デバイスの選択  
 ![リモート デバッグ用のマネージ プロジェクト プロパティ](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN\_Managed\_ProjProp\_Remote")  
  
1.  ソリューション エクスプローラーでプロジェクト名を選択し、ショートカット メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[デバッグ\]** をクリックします。  
  
3.  **\[ターゲット デバイス\]** ボックスの一覧の **\[リモート コンピューター\]** をクリックします。  
  
4.  リモート デバイスのネットワーク名を **\[リモート コンピューター\]** ボックスに入力するか、**\[検索\]** を選び、**\[リモート デバッガー接続の選択\]** ダイアログ ボックスでデバイスを選択します。  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> JavaScript プロジェクトと C\+\+ プロジェクト用のリモート デバイスの選択  
 ![リモート デバッグ用の C&#43;&#43; プロジェクト プロパティ](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN\_CPP\_ProjProp\_Remote")  
  
1.  ソリューション エクスプローラーでプロジェクト名を選択し、ショートカット メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[構成プロパティ\]** ノードを展開し、**\[デバッグ\]** をクリックします。  
  
3.  **\[起動するデバッガー\]** ボックスの一覧の **\[リモート デバッガー\]** をクリックします。  
  
4.  リモート デバイスのネットワーク名を **\[コンピューター名\]** ボックスに入力するか、ボックスの下向き矢印を選び、**\[リモート デバッガー接続の選択\]** ダイアログ ボックスでデバイスを選択します。  
  
##  <a name="BKMK_RunRemoteDebug"></a> リモート デバッグ セッションの実行  
 リモート デバッグ セッションは、ローカル セッションと同じ方法で開始、停止、および移動します。 デバッグを開始する前に、リモート デバッグ モニターがリモート デバイスで実行されていることを確認します。  
  
 **\[デバッグ\]** メニューの **\[デバッグの開始\]** をクリックします \(キーボードの場合: F5 キーを押します\)。 プロジェクトが再コンパイルされた後、リモート デバイスに配置され、開始されます。 デバッガーはブレークポイントで実行を中断するので、その時点でコードをステップ イン、ステップ オーバー、およびステップ アウトできます。 デバッグ セッションを終了し、リモート アプリケーションを閉じるには、**\[デバッグの停止\]** をクリックします。 詳細については、以下を参照してください。[Visual Studio でのアプリのデバッグ](../debugger/debug-store-apps-in-visual-studio.md)  
  
## 参照  
 [Visual Studio でのストア アプリのテスト](../test/testing-store-apps-with-visual-studio.md)   
 [Visual Studio でのアプリのデバッグ](../debugger/debug-store-apps-in-visual-studio.md)