---
title: "Visual Studio での UWP アプリの展開 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 359431356bb06a04857b93e10996a2123c80f129
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Visual Studio からの UWP アプリを配置します。
![Windows にのみ適用されます](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Visual Studio の配置機能は、ビルドし、ターゲット デバイスに Visual Studio で作成した UWP アプリを登録します。 アプリの厳密な登録方法は、ターゲット デバイスがローカルかリモートかによって違います。  
  
-   ターゲットがローカルの Visual Studio コンピューターの場合、Visual Studio はアプリをビルド フォルダーから登録します。  
  
-   ターゲットがリモート デバイスの場合、Visual Studio は必要なファイルをリモート コンピューターにコピーしてから、そのデバイス上でアプリを登録します。  
  
 使用して Visual Studio からアプリをデバッグするときに、展開は自動、**デバッグの開始**オプション (キーボード: f5 キーを押して)、または**デバッグなしで開始**オプション (キーボード: ctrl キーを押しながら f5 キーを押します)。 アプリを手動で配置することも可能です。 次のシナリオでは、手動の配置は有効です。  
  
-   ローカル コンピューターまたはリモート コンピューターで行う臨時のテスト。  
  
-   デバッグ対象のアプリを起動するためのアプリを配置する場合。  
  
-   別のアプリまたはメソッドによって起動される、デバッグ対象のアプリを配置します。
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>UWP アプリを展開する方法  
 アプリを手動で配置する手順はシンプルです。  
  
1.  リモート デバイスへ配置する場合は、アプリのスタートアップ プロジェクトのプロパティ プロジェクト ページに、デバイスの名前または IP アドレスを指定します。 (指定するステップはこのトピック内で後述)。  
  
2.  デバッガーの Visual Studio ツールバーで、 **[デバッグの開始]** ボタンの横のドロップダウン リストから配置ターゲットを選択します。  
  
     ![ローカル コンピューター上で実行](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  **[ビルド]** メニューで **[配置]**を選択  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> リモート デバイスの指定方法  

**必須コンポーネント**  
  
Windows 10 のリモート デバイスを有効にする必要があります[開発者モード](/windows/uwp/get-started/enable-your-device-for-development)です。 作成者の更新プログラムを実行している Windows 10 デバイス上または後で、リモート ツールが自動的にインストールされているアプリを展開するときにします。 詳細については、次を参照してください。[インストール済みのアプリ パッケージをデバッグ](../debugger/debug-installed-app-package.md)です。

> [!NOTE]
> Windows 8.1 および Windows 10 のより前の作成者の更新プログラムのバージョンでは、リモート デバイスで、Visual Studio リモート ツールをインストールする必要があり、リモート デバッガーを実行する必要があります。 Windows 8.1 に開発者用ライセンスをインストールすることも必要があります。
  
配置では、リモート デバッガーのネットワーク チャネルを使用して、アプリのファイルをリモート デバイスに送信します。  
  
#### <a name="to-specify-a-remote-device"></a>リモート デバイスを指定するには  
  
1.  スタートアップ プロジェクトのデバッグ プロパティ ページで、リモートの配置ターゲットの名前または IP アドレスを指定します。  
  
2.  デバッグ プロパティ ページを開くには、ソリューション エクスプローラーでプロジェクトを選択してから、ショートカット メニューで **[プロパティ]** を選択します。  
  
3.  次に、プロパティ ページ ウィンドウで **[デバッグ]** ノードを選択します。

4. **ターゲット デバイス****リモート マシン**です。

5. **リモート マシン**をクリックして**検索**です。
  
4.  名前またはリモート デバイスの IP アドレスを入力するかからデバイスを選択することができます、**リモート接続** ダイアログ ボックス。  
  
     ![[リモート デバッガー接続] ダイアログ ボックス](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
     **リモート接続** ダイアログ ボックスでは、ローカル ネットワークのサブネットとイーサネット ケーブルによって Visual Studio コンピューターに直接接続されている任意のデバイスにデバイスを表示します。  
  
 **JavaScript または Visual C++ のプロジェクト ページにあるリモート デバイスを指定**  
  
 ![C &#43; #43 です。リモート デバッグのプロパティをプロジェクト](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  **[起動するデバッガー]** ボックスの一覧の **[リモート デバッガー]** をクリックします。  
  
2.  **[コンピューター名]** ボックスのリモート デバイスにネットワーク名を入力します。 あるいはボックス内の下向き矢印をクリックして、[リモート デバッガー接続の選択] ダイアログ ボックスからデバイスを選択します。  
  
 **Visual C# および Visual Basic のプロジェクト ページにあるリモート デバイスを指定**  
  
 ![マネージ リモート デバッグ用のプロジェクト プロパティ](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  **[ターゲット デバイス]** ボックスの一覧の **[リモート コンピューター]** をクリックします。  
  
2.  リモート デバイスのネットワーク名を **[リモート コンピューター]** ボックスに入力するか、 **[検索]** をクリックし、 **[リモート デバッガー接続の選択]** ダイアログ ボックスでデバイスを選択します。  
  
##  <a name="BKMK_Deployment_options"></a> 配置オプション  
 次の配置オプションを、スタートアップ プロジェクトのデバッグ プロパティ ページに設定できます。  
  
 **ネットワーク ループバックの許可**  
 セキュリティ上の理由から、標準的な方法でインストールされた [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリは、インストール先のデバイスに対してネットワーク呼び出しを行うことはできません。 既定では、Visual Studio による配置では、配置されたアプリに対するこの規則の適用は免除されます。 この免除によって、1 台のコンピューター上で通信プロシージャをテストできます。 アプリを [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]に送信する前に、アプリを適用除外せずにテストする必要があります。  
  
 アプリからネットワーク ループバックの適用除外を削除するには  
  
-   C# および VB のデバッグ プロパティ ページで、 **[ネットワーク ループバックの許可]** チェック ボックスをクリアします。  
  
-   JavaScript およびデバッグ プロパティ ページで、 **[ネットワーク ループバックの許可]** の値を **[いいえ]**に設定します。  
  
 **起動しない。ただし開始した場合にはコードをデバッグ (C# および VB) / アプリケーションを起動 (JavaScript および C++)**  
 アプリが起動した場合はデバッグ セッションを自動駅に開始するように、配置を構成するには  
  
-   C# および VB のデバッグ プロパティ ページで、 **[起動しないが、開始時にコードをデバッグ]** チェック ボックスをオンにします。  
  
-   JavaScript およびデバッグ プロパティ ページで、 **[アプリケーションの起動]** の値を **[はい]**に設定します。  
  
## <a name="see-also"></a>参照  
 [インストールされているアプリ パッケージをデバッグ](../debugger/debug-installed-app-package.md)です。   
 [Visual Studio からアプリを実行します。](../debugger/run-store-apps-from-visual-studio.md)