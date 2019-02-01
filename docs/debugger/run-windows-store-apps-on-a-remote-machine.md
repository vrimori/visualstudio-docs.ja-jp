---
title: リモート コンピューター上の UWP アプリのデバッグ |Microsoft Docs
ms.date: 10/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 9125887789cdeee3152f9ebf3e2c82cf523cc468
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932767"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Visual Studio からリモート コンピューター上の UWP アプリをデバッグします。
  
Visual Studio を使用して、実行、デバッグ、プロファイル、および別のコンピューターまたはデバイス上のユニバーサル Windows プラットフォーム (UWP) アプリをテストすることができます。 Visual Studio コンピューターがタッチ、位置情報、または物理的な方向など、UWP 固有の機能をサポートしていない場合は、リモート コンピューターで UWP アプリを実行するいると便利です。 

##  <a name="BKMK_Prerequisites"></a> 必要条件  

Visual Studio からリモート デバイスで UWP アプリをデバッグします。  
  
- リモート デバッグ用には、Visual Studio プロジェクトを構成する必要があります。
- Visual Studio コンピューターとリモート コンピューターをネットワーク経由で接続されているか、USB またはイーサネット ケーブルによって直接接続されています。 インターネットを介したデバッグはサポートされません。  
- 必要があります[開発者モードを有効に](/windows/uwp/get-started/enable-your-device-for-development)Visual Studio コンピューターとリモート コンピューターの両方でします。 
- リモート コンピューターには、Visual Studio のリモート ツールが実行しなければなりません。 
  - 一部の Windows 10 のバージョンが起動し、リモート ツールを自動的に実行します。 それ以外の場合、[をインストールして Visual Studio のリモート ツールを実行](#BKMK_download)します。
  - 10 の Windows Mobile デバイスを必要としたり、リモート ツールをサポートしないでください。 

##  <a name="BKMK_ConnectVS"></a> リモート デバッグ用の Visual Studio プロジェクトを構成します。
<a name="BKMK_DirectConnect"></a> プロジェクトを使用する**プロパティ**に接続するリモート デバイスを指定します。 設定は、プログラミング言語によって異なります。 

> [!CAUTION]
> 既定では、プロパティ ページ設定**ユニバーサル (暗号化されていないプロトコル)** として、**認証の種類**は Windows 10 のリモート接続します。 設定する必要があります**認証なし**リモート デバッガーに接続します。 **ユニバーサル (暗号化されていないプロトコル)** と**認証なし**プロトコルがありますいないネットワーク セキュリティ、開発とリモート コンピューターの間で渡されるデータは脆弱です。 悪意のあるまたは悪意のあるトラフィックのリスク、これらは信頼されたネットワークをのみの認証の種類をいないことを確認を選択します。 
>
>選択した場合**Windows 認証**の**認証の種類**、デバッグするときに、リモート コンピューターにサインインする必要があります。 リモート デバッガーを実行する必要がありますも**Windows 認証**モードは、Visual Studio コンピューターと同じユーザー アカウントとします。

###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> 構成、C#または Visual Basic プロジェクトのリモート デバッグ  

1. 選択、C#または Visual Studio で Visual Basic プロジェクト**ソリューション エクスプ ローラー**を選択し、**プロパティ**アイコン、キーを押して**Alt** + **入力**、または右クリックし、選択**プロパティ**します。
  
1.  **[デバッグ]** タブを選択します。  
  
1.  **ターゲット デバイス**を選択します**リモート マシン**リモート コンピューターの場合、または**デバイス**の直接接続されている 10 の Windows Mobile デバイス。  
  
1.  リモート マシンの場合に、ネットワーク名または IP アドレスを入力してください、**リモート マシン**フィールド、または選択**検索**でデバイスを検索する、[リモート接続 ダイアログ ボックス](#remote-connections)。 
    
    ![リモート デバッグ用のプロジェクトのプロパティを管理](../debugger/media/vsrun_managed_projprop_remote.png "デバッグ マネージ プロジェクトのプロパティ")  
    
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> リモート デバッグ用の JavaScript または C++ プロジェクトを構成します。   
  
1.  Visual Studio で C++ または JavaScript プロジェクトを選択**ソリューション エクスプ ローラー**を選択し、**プロパティ**アイコン、キーを押して**Alt**+**」と入力**、または右クリックし、選択**プロパティ**します。
  
1.  選択、**デバッグ**タブ。  
  
3.  **起動するデバッガー**を選択します**リモート マシン**リモート コンピューターの場合、または**デバイス**の直接接続されている 10 の Windows Mobile デバイス。 
  
1.  リモート マシンでは、次のように入力しますまたは、ネットワーク名または IP アドレスを選択して、**マシン名**フィールド、またはドロップ ダウンして**検索**でデバイスを検索する、[リモート接続 ダイアログ ボックス。](#remote-connections). 

    ![リモート デバッグ用の C++ プロジェクト プロパティ](../debugger/media/vsrun_cpp_projprop_remote.png "C++ のデバッグ プロジェクト プロパティ")
    
### <a name="remote-connections"></a> リモート接続 ダイアログ ボックスを使用します。

**リモート接続**ダイアログ ボックスで、特定のリモート コンピューター名または IP アドレスを検索したり、丸め矢印更新アイコンを選択して接続を自動検出します。 ダイアログ ボックスでは、ローカル サブネット上のリモート デバッガーを現在実行されているデバイスのみを検索します。 すべてのデバイスで検出できる、**リモート接続** ダイアログ ボックス。 

 ![リモート接続 ダイアログ ボックス](../debugger/media/vsrun_selectremotedebuggerdlg.png "リモート接続 ダイアログ ボックス")  

>[!TIP]
>名前でリモート デバイスに接続できない場合は、IP アドレスを使用してみてください。 リモートのデバイスで、IP アドレスを確認する次のように入力します。 **ipconfig**コマンド ウィンドウにします。 IP アドレスは、 **IPv4 アドレス**します。  
    
## <a name="BKMK_download"></a> Remote Tools for Visual Studio をダウンロードしてインストールする

リモート コンピューター上のアプリをデバッグする Visual Studio は、リモート コンピューターする必要があります実行されている Remote Tools for Visual Studio。 

- 10 の Windows Mobile デバイスは必要があります。 またはリモート ツールをサポートしていないしないでください。 
- 作成者を実行している Windows 10 Pc が (バージョン 1703) を更新し、後で、Windows 10 の Xbox、IoT、HoloLens デバイス リモート ツールのインストールに自動的にアプリを展開するときにします。 
- 前の作成者の更新プログラムの Windows 10 Pc にする必要があります手動でダウンロード、インストール、およびデバッグを開始する前に、リモート コンピューターでリモート ツールを実行します。

**ダウンロードして、リモート ツールをインストールします。**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> リモート ツールを構成します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> UWP アプリをリモートでデバッグします。 

リモート デバッグとローカル デバッグ同様に機能します。 

1. Windows 10 の以前の作成者の更新プログラムのバージョンでは、必ず、リモート デバッグ モニター (*msvsmon.exe*) がリモート デバイスで実行されています。  
   
1. Visual Studio コンピューターでは、必ず、適切なデバッグ ターゲット (**リモート マシン**または**デバイス**)、ツールバーの緑色の矢印の横に表示します。 
   
1. 選択してデバッグを開始**デバッグ** > **デバッグの開始**を**F5**、またはツールバーの緑色の矢印を選択します。 
   
   プロジェクトは再コンパイル、展開し、リモート デバイスで開始します。 デバッガーがブレークポイントでは、実行を中断しに、オーバー、およびコードからステップすることができます。 
   
1. 必要に応じて、選択**デバッグ** > **デバッグの停止**またはキーを押します**Shift**+**F5**デバッグを停止してリモート アプリケーションを閉じます。
  
## <a name="see-also"></a>関連項目  
 [高度なリモート配置オプション](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Visual Studio での UWP アプリのテスト](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)   
 [Visual Studio で UWP アプリを展開する](debugging-windows-store-and-windows-universal-apps.md)
