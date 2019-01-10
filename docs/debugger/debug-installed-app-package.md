---
title: UWP アプリ パッケージのインストールのデバッグ |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 313fceed4715127696d04a7dfea6990e9cf18718
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879745"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Visual Studio でインストールされている UWP アプリ パッケージをデバッグします。

Visual Studio では、Windows 10 コンピューターおよび Xbox、HoloLens、IoT デバイスでインストールされているユニバーサル Windows プラットフォーム (UWP) アプリのパッケージをデバッグできます。 

>[!NOTE]
>スマート フォンでは、visual Studio がインストールされている UWP アプリのデバッグはサポートされていません。
   
UWP アプリのデバッグに関する詳細については、上、ブログの投稿を参照してください。[インストール済みアプリ パッケージのデバッグ](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)と[ユニバーサル Windows アプリ (UWP) を構築](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/)します。

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>ローカル コンピューターにインストールされている UWP アプリをデバッグします。

1. Visual Studio で、次のように選択します。**デバッグ** > **その他のデバッグ ターゲット** > **インストール済みアプリ パッケージのデバッグ**します。
   
1. **インストール済みアプリ パッケージのデバッグ**ダイアログで、**接続の種類**を選択します**ローカル マシン**します。
   
1. **アプリ パッケージのインストールされている**、デバッグするアプリを選択するか、検索ボックスに名前を入力します。 実行されていないインストール済みアプリ パッケージの下に表示**実行されていない**と実行中のアプリが**を実行している**します。 
   
   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")
   
1. 必要に応じて、コードの種類を変更**このコードの種類をデバッグ**、他のオプションを選択します。 
   - 選択**起動しないが、開始時に、コードをデバッグ**アプリの起動時にデバッグを開始します。 デバッグの開始からコントロールのパスをデバッグする効果的な方法は、アプリが起動[さまざまな起動メソッド](/windows/uwp/xbox-apps/automate-launching-uwp-apps)、カスタム パラメーターでプロトコルのアクティブ化などです。
   
1. 選択**開始**、アプリが実行されている場合は、選択または**アタッチ**します。

> [!NOTE]
> 選択して、実行中の UWP またはその他のアプリのプロセスに接続することもできます**デバッグ** > **プロセスにアタッチ**Visual Studio でします。 元の Visual Studio プロジェクトを実行中のプロセスにアタッチする必要はありませんの元のコードを持っていないプロセスをデバッグするときに大きく役立ちますが、アプリのシンボルの読み込み。 参照してください[デバッガーでシンボルとソース ファイルの指定](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)します。
  
## <a name="remote"></a> リモート コンピューターまたはデバイスにインストールされている UWP アプリをデバッグします。

初めて Visual Studio は Windows 10 デバイスをリモート投稿の作成者の Windows 10 の更新プログラム、またはコンピューターにインストールされている UWP アプリをデバッグ対象のデバイスにリモート デバッグ ツールをインストールします。 

1. [開発者モードを有効にする](/windows/uwp/get-started/enable-your-device-for-development)Visual Studio コンピューターとリモート デバイスまたはコンピューター。
   
1. 前の作成者の更新プログラムの Windows 10 を実行しているリモート コンピューターに接続している場合[手動でインストールして、リモート デバッガーを起動](../debugger/remote-debugging.md)リモート コンピューター。
   
1. Visual Studio コンピューターでは、次のように選択します。**デバッグ** > **その他のデバッグ ターゲット** > **インストール済みアプリ パッケージのデバッグ**します。
   
1. **インストール済みアプリ パッケージのデバッグ**ダイアログで、**接続の種類**を選択します**リモート マシン**または**デバイス**します。
   
   選択した場合**デバイス**、お使いのコンピューターを Windows 10 デバイスに物理的に接続する必要があります。
   
   コンピューターのアドレスが横に表示されない場合、リモート コンピューターの**アドレス**、**変更**します。 
      
   1. **リモート接続** ダイアログ ボックスの横に**アドレス**、名前または接続先のコンピューターの IP アドレスを入力します。
      
      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")
      
      デバッガーは、コンピューター名を使用してリモート コンピューターに接続できない場合は、IP アドレスを使用します。 Xbox、HoloLens、IoT デバイスの IP アドレスを使用します。
   1. 次に、認証オプションをオン**認証モード**します。
      
      ほとんどのアプリでは、既定値をそのまま**ユニバーサル (暗号化されていないプロトコル)** します。
   1. 選択**選択**します。 

1. **アプリ パッケージのインストールされている**、デバッグするアプリを選択するか、検索ボックスに名前を入力します。 実行されていないインストール済みアプリ パッケージの下に表示**実行されていない**と実行中のアプリが**を実行している**します。 
   
1. 必要に応じて、コードの種類を変更**このコードの種類をデバッグ**、他のオプションを選択します。 
   - 選択**起動しないが、開始時に、コードをデバッグ**アプリの起動時にデバッグを開始します。 デバッグの開始からコントロールのパスをデバッグする効果的な方法は、アプリが起動[さまざまな起動メソッド](/windows/uwp/xbox-apps/automate-launching-uwp-apps)、カスタム パラメーターでプロトコルのアクティブ化などです。
   
1. 選択**開始**、アプリが実行されている場合は、選択または**アタッチ**します。

最初に接続されているか、Xbox、HoloLens、IoT デバイスにインストールされているアプリ パッケージのデバッグを開始すると、Visual Studio には、ターゲット デバイスのリモート デバッガーの正しいバージョンがインストールされます。 リモート デバッガーのインストールは、時間と、メッセージにかかる場合があります**リモート デバッガーを開始**が発生しているときに表示します。

>[!NOTE]
>現時点では、Xbox や HoloLens デバイスでは、既に実行されている場合にアタッチされたデバッガーでアプリを再起動します。

UWP アプリのリモート展開の詳細については、次を参照してください。 [UWP アプリのデプロイとデバッグ](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)と[リモート マシンでのデバッグの UWP アプリ](run-windows-store-apps-on-a-remote-machine.md)します。 
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)  
 [リモート デバッグ](../debugger/remote-debugging.md)  
 [Windows ファイアウォールをリモート デバッグ用に構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [リモート デバッガーのポートの割り当て](../debugger/remote-debugger-port-assignments.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)