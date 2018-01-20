---
title: "リモート コンピューターでの UWP アプリの実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/05/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: "43"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: f9d538cbc650de2d704c885a8eff6a897c9ef68e
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="run-uwp-apps-on-a-remote-machine-in-visual-studio"></a>Visual Studio でのリモート コンピューター上の UWP アプリを実行します。
  
実行するには、UWP アプリをリモート コンピューターでは、for Visual Studio リモート ツールを使用してそれにアタッチする必要があります。 リモート ツールを使用すると、実行、デバッグ、プロファイル、および Visual Studio を実行している 2 つ目のコンピューターから 1 つのデバイスで実行されている UWP アプリをテストできます。 リモート デバイスで実行されていることが効果的である特に、Visual Studio コンピューターがタッチ、位置情報、物理的な方向など、UWP アプリに固有の機能をサポートしていない場合。 このトピックでは、リモート セッションを構成および開始する手順について説明します。

一部のシナリオでリモート ツールはリモート デバイスに展開するときに自動的にインストールされます。

- Windows 10 Pc の作成者の更新プログラムおよびそれ以降のバージョンを実行するのリモート ツールを自動的にインストールされます。
- Windows 10 Xbox、IOT、HoloLens デバイスの場合は、リモート ツールを自動的にインストールされます。
- Windows Mobile 10、電話に物理的に接続している、有効にする必要があります[開発者モード](/windows/uwp/get-started/enable-your-device-for-development)を選択する必要がありますと**デバイス**デバッグ ターゲットとして。 リモート ツールがないために必要なか、サポート。

事前作成元の更新プログラムのバージョンの Windows を実行している Windows 10 Pc、必要がありますリモート ツール リモート コンピューターに手動でインストールするをデバッグする前にします。 このトピックの手順に従います。 
  
##  <a name="BKMK_Prerequisites"></a> 必要条件  
 リモート デバイスでデバッグするには:  
  
- リモート デバイスと、Visual Studio コンピューターをネットワーク経由で接続されているか、USB またはイーサネット ケーブルによって直接接続します。 インターネットを介したデバッグはサポートされません。  

- 有効にする必要があります[開発者モード](/windows/uwp/get-started/enable-your-device-for-development)です。 
  
- Windows 10 Pc の Windows 10 の作成者の更新プログラムよりも前のバージョンの Windows 10 を実行している場合に行う必要があります[をインストールして、リモート デバッグ コンポーネントの実行](#BKMK_download)です。
  
##  <a name="BKMK_Security"></a> セキュリティ  
既定では、**ユニバーサル (暗号化されていないプロトコル)**は Windows 10 で使用します。 このプロトコルは、信頼されたネットワークでのみ使用する必要があります。 デバッグ接続は、悪意のあるユーザーでしたをインターセプトし、開発とリモート コンピューターの間で渡されるデータの変更に対して脆弱です。
  
> [!WARNING]
>  認証モードを設定すると、ネットワーク セキュリティはありません**ユニバーサル (暗号化されていないプロトコル)**または**None**です。 ネットワークがないこと悪意のあるまたは悪意のあるトラフィックからのリスク場合にのみ、これらのモードを選択します。  
  
##  <a name="BKMK_DirectConnect"></a>USB ケーブルを使用して直接接続する方法 

選択して Windows 10 で USB 接続されたデバイスに展開できます**デバイス**の代わりに**リモート マシン**配置ターゲットとして (これを行う、**標準**ツールバーまたは、デバッグのプロパティ ページで)。

##  <a name="BKMK_ConnectVS"></a>リモート デバッグ用の Visual Studio プロジェクトを構成します。  
 プロジェクトのプロパティに、接続するリモート デバイスを指定します。 手順はプログラミング言語によって異なります。 リモート デバイスのネットワーク名を入力するかから選択することができます、**リモート接続** ダイアログ ボックス。  
  
 ![[リモート デバッガー接続] ダイアログ ボックス](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 ダイアログ ボックスには、Visual Studio コンピューターのローカル サブネット上にあるデバイスで、リモート デバッガーを実行中のデバイスだけが表示されます。  
  
> [!TIP]
>  リモート デバイスへの接続に問題がある場合は、デバイスの IP アドレスを入力してください。 デバイスの IP アドレスを確認するには、コマンド ウィンドウを開き、「 **ipconfig**」と入力します。 IP アドレスは **IPv4 Address**として表示されます。  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a>C# および Visual Basic プロジェクト用のリモート デバイスを選択します。  
  
1.  ソリューション エクスプローラーでプロジェクト名を選択し、ショートカット メニューの **[プロパティ]** をクリックします。  
  
2.  **[デバッグ]**をクリックします。  
  
3.  **[ターゲット デバイス]** ボックスの一覧の **[リモート コンピューター]** をクリックします。  
  
4.  リモート デバイスのネットワーク名を **[リモート コンピューター]** ボックスに入力するか、 **[検索]** を選び、 **[リモート デバッガー接続の選択]** ダイアログ ボックスでデバイスを選択します。 

    ![マネージ リモート デバッグ用のプロジェクト プロパティ](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a>JavaScript と C++ プロジェクト用のリモート デバイスを選択します。  
  
1.  ソリューション エクスプローラーでプロジェクト名を選択し、ショートカット メニューの **[プロパティ]** をクリックします。  
  
2.  **[構成プロパティ]** ノードを展開し、 **[デバッグ]**をクリックします。  
  
3.  **[起動するデバッガー]** ボックスの一覧の **[リモート デバッガー]** をクリックします。  
  
4.  リモート デバイスのネットワーク名を **[コンピューター名]** ボックスに入力するか、ボックスの下向き矢印を選び、 **[リモート デバッガー接続の選択]** ダイアログ ボックスでデバイスを選択します。  

    ![C &#43; #43 です。リモート デバッグのプロパティをプロジェクト](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")
  
## <a name="BKMK_download"></a>ダウンロードして、リモート ツールのインストール (前の作成者が更新プログラム)

Windows 10 の事前作成元の更新バージョンを使用している場合は、次の手順に従います。 それ以外の場合、このセクションをスキップすることができます。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a>リモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a>リモート デバッグ セッションを開始します。  
 リモート デバッグ セッションは、ローカル セッションと同じ方法で開始、停止、および移動します。 プレ-作成者の更新プログラムのバージョンの Windows 10、リモート デバッグ モニターがリモート デバイスで実行されていることを確認します。  
  
 **[デバッグ]** メニューの **[デバッグの開始]** をクリックします (キーボードの場合: F5 キーを押します)。 プロジェクトが再コンパイルされた後、リモート デバイスに配置され、開始されます。 デバッガーはブレークポイントで実行を中断するので、その時点でコードをステップ イン、ステップ オーバー、およびステップ アウトできます。 デバッグ セッションを終了し、リモート アプリケーションを閉じるには、 **[デバッグの停止]** をクリックします。
  
## <a name="see-also"></a>参照  
 [リモート展開のオプションの詳細](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Visual Studio での UWP アプリのテスト](../test/testing-store-apps-with-visual-studio.md)   
 [Visual Studio でアプリをデバッグします。](../debugger/debug-store-apps-in-visual-studio.md)