---
title: リモート コンピューター上の UWP アプリの実行 |Microsoft Docs
ms.custom: ''
ms.date: 01/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2845057fe970299d249d580d97b557a5ed311fc0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38795973"
---
# <a name="run-uwp-apps-on-a-remote-machine-in-visual-studio"></a>Visual Studio でのリモート コンピューターで UWP アプリを実行します。
  
UWP アプリをリモート コンピューターで実行するには、for Visual Studio リモート ツールを使用してアタッチする必要があります。 リモート ツールを使用すると、実行、デバッグ、プロファイル、および Visual Studio を実行している 2 つ目のコンピューターから 1 つのデバイスで実行されている UWP アプリをテストできます。 リモート デバイスで実行されているが、Visual Studio コンピューターがタッチ、位置情報、および物理的な方向など、UWP アプリに固有の機能をサポートしていない場合に特に効果的です。 このトピックでは、リモート セッションを構成および開始する手順について説明します。

一部のシナリオでリモート ツールは、リモート デバイスに展開するときに自動的にインストールされます。

- Creators Update 以降を実行している Windows 10 Pc の場合は、リモート ツールを自動的にインストールされます。
- Windows 10 の Xbox、IOT、HoloLens デバイスのリモート ツールを自動的にインストールされます。
- Windows モバイル 10 では、電話に物理的に接続する必要がある、有効にする必要があります[開発者モード](/windows/uwp/get-started/enable-your-device-for-development)し選択する必要があります**デバイス**デバッグ ターゲットとして。 リモート ツールは必要なまたはサポートされていません。

事前作成元の更新プログラムのバージョンの Windows を実行している Windows 10 Pc の場合必要がありますリモート ツール、リモート コンピューターで手動でインストールするをデバッグする前に。 このトピックの手順に従います。 
  
##  <a name="BKMK_Prerequisites"></a> 必要条件  
 リモート デバイスでデバッグするには:  
  
- リモート デバイスと、Visual Studio コンピューターをネットワーク経由で接続されているか、USB ドライブまたはイーサネット ケーブルによって直接接続されています。 インターネットを介したデバッグはサポートされません。  

- 有効にする必要があります[開発者モード](/windows/uwp/get-started/enable-your-device-for-development)します。 
  
- Windows 10 Pc の Windows 10 Creators Update より前のバージョンの Windows 10 を実行している場合にする必要があります[をインストールして、リモート デバッグ コンポーネントの実行](#BKMK_download)します。
  
##  <a name="BKMK_Security"></a> セキュリティ  
既定では、**ユニバーサル (暗号化されていないプロトコル)** は Windows 10 で使用されます。 このプロトコルは、信頼されたネットワークでのみ使用する必要があります。 デバッグ接続がインターセプトし、開発およびリモート コンピューターの間で渡されるデータを変更する悪意のあるユーザーに対して脆弱です。
  
> [!WARNING]
>  認証モードを設定すると、ネットワークのセキュリティがない**ユニバーサル (暗号化されていないプロトコル)** または**None**します。 ネットワークがの悪意のあるまたは悪意のあるトラフィックのリスクがないことを確認する場合にのみ、これらのモードを選択します。  
  
##  <a name="BKMK_DirectConnect"></a> USB ケーブルを使用して直接接続する方法 

選択して Windows 10 で USB 接続されたデバイスに展開できます**デバイス**の代わりに**リモート マシン**デプロイ ターゲットとして (これを行う、**標準**ツールバーまたは、デバッグのプロパティ ページ)。

##  <a name="BKMK_ConnectVS"></a> リモート デバッグ用の Visual Studio プロジェクトを構成します。  
 プロジェクトのプロパティに、接続するリモート デバイスを指定します。 手順はプログラミング言語によって異なります。 リモート デバイスのネットワーク名を入力するかから選択することができます、**リモート接続** ダイアログ ボックス。  
  
 ![リモート デバッガー接続 ダイアログ ボックスをオン](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 ダイアログ ボックスには、Visual Studio コンピューターのローカル サブネット上にあるデバイスで、リモート デバッガーを実行中のデバイスだけが表示されます。  
  
> [!TIP]
>  リモート デバイスへの接続に問題がある場合は、デバイスの IP アドレスを入力してください。 デバイスの IP アドレスを確認するには、コマンド ウィンドウを開き、「 **ipconfig**」と入力します。 IP アドレスは **IPv4 Address**として表示されます。  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> C# および Visual Basic プロジェクト用のリモート デバイスを選択します。  
  
1.  ソリューション エクスプローラーでプロジェクト名を選択し、ショートカット メニューの **[プロパティ]** をクリックします。  
  
2.  **[デバッグ]** をクリックします。  
  
3.  **[ターゲット デバイス]** ボックスの一覧の **[リモート コンピューター]** をクリックします。  
  
4.  リモート デバイスのネットワーク名を **[リモート コンピューター]** ボックスに入力するか、 **[検索]** を選び、 **[リモート デバッガー接続の選択]** ダイアログ ボックスでデバイスを選択します。 

    ![リモート デバッグ用のプロジェクトのプロパティを管理](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> JavaScript と C++ プロジェクト用のリモート デバイスを選択します。  
  
1.  ソリューション エクスプローラーでプロジェクト名を選択し、ショートカット メニューの **[プロパティ]** をクリックします。  
  
2.  **[構成プロパティ]** ノードを展開し、 **[デバッグ]** をクリックします。  
  
3.  **[起動するデバッガー]** ボックスの一覧の **[リモート デバッガー]** をクリックします。  
  
4.  リモート デバイスのネットワーク名を **[コンピューター名]** ボックスに入力するか、ボックスの下向き矢印を選び、 **[リモート デバッガー接続の選択]** ダイアログ ボックスでデバイスを選択します。  

    ![C&#43; &#43;リモート デバッグのプロパティをプロジェクト](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")
  
## <a name="BKMK_download"></a> ダウンロードして、リモート ツールのインストール (事前 Creators Update)

事前作成元の更新プログラムのバージョンの Windows 10 を使用している場合は、次の手順をに従ってください。 それ以外の場合、このセクションをスキップすることができます。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> リモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> リモート デバッグ セッションを開始します。  
 リモート デバッグ セッションは、ローカル セッションと同じ方法で開始、停止、および移動します。 Windows 10 の以前の作成者の更新プログラムのバージョンでは、リモート デバッグ モニターがリモートのデバイスで実行されていることを確認します。  
  
 **[デバッグ]** メニューの **[デバッグの開始]** をクリックします (キーボードの場合: F5 キーを押します)。 プロジェクトが再コンパイルされた後、リモート デバイスに配置され、開始されます。 デバッガーはブレークポイントで実行を中断するので、その時点でコードをステップ イン、ステップ オーバー、およびステップ アウトできます。 デバッグ セッションを終了し、リモート アプリケーションを閉じるには、 **[デバッグの停止]** をクリックします。
  
## <a name="see-also"></a>関連項目  
 [リモート配置オプションの詳細](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Visual Studio での UWP アプリのテスト](../test/testing-store-apps-with-visual-studio.md)   
 [Visual Studio でアプリをデバッグします。](../debugger/debug-store-apps-in-visual-studio.md)
