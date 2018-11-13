---
title: インストールされているアプリ パッケージ (UWP) のデバッグ |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 3bb858f2ee20eb65c09dd4979f2bbba1470cbe0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908249"
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Visual Studio (UWP) でインストールされているアプリ パッケージをデバッグします。

クリックして、インストールされているアプリ パッケージをデバッグする**デバッグ > その他のデバッグ ターゲット > インストール済みアプリ パッケージのデバッグ**します。 このデバッグ メソッドは、ユニバーサル Windows アプリ (UWP) のこれらのデバイスで使用します。

* Windows 10 の (スマート フォンではサポートされていません)
* XBox
* HoloLens
* IoT

これらの機能に関する詳細については、更新プログラムに関するブログ記事を参照してください。[インストール済みアプリ パッケージのデバッグ](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)の投稿と[ユニバーサル Windows アプリ (UWP) を構築](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/)します。

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>アプリ パッケージがインストールされている、または、ローカル コンピューターまたはデバイスで実行中のアプリをデバッグします。

1. UWP プロジェクトを Visual Studio で開いて、次のようにクリックします。**デバッグ > その他のデバッグ ターゲット > インストール済みアプリ パッケージのデバッグ**します。

2. いずれかを選択**ローカル マシン**または**デバイス**します。

     選択した場合**デバイス**、お使いのコンピューターを Windows 10 デバイスに物理的に接続する必要があります。

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     アプリ パッケージに表示されますがインストールされている現在実行中、**を実行している**ノード。 アプリ パッケージの表示を実行してではインストールされている**実行されていない**します。

3. 下をデバッグするアプリの名前を選択**を実行している**または**実行されていない**選択**開始**、アプリが既に実行されている場合は、「**アタッチ**.

     選択した場合**起動しないが、開始時に、コードをデバッグ**、これは、Visual Studio デバッガーはカスタム時に起動するときに、アプリにアタッチします。 これからコントロールのパスをデバッグする効果的な方法は、[さまざまな起動メソッド](/windows/uwp/xbox-apps/automate-launching-uwp-apps)、カスタム パラメーターでプロトコルのアクティブ化などです。

> [!NOTE]
> Visual Studio を選択して、実行中の UWP アプリのプロセスを添付できますも**デバッグ**、し**プロセスにアタッチ**します。 実行中のプロセスにアタッチすると、元の Visual Studio プロジェクトが必要としないの元のコードを持っていないプロセスをデバッグするときに大きく役立ちますが、プロセスのシンボルの読み込み。
  
## <a name="remote"></a> リモート コンピューターにインストールされているか実行されているアプリをデバッグします。 

最初にリモート コンピューターにインストールされているアプリ パッケージをデバッグするときに、Visual Studio には、ターゲット デバイスのリモート ツールの正しいバージョンがインストールされます。 ターゲット デバイスは、Windows 10 コンピューター、XBox、HoloLens、または IoT デバイスである必要があります。

1. Windows 10 デバイスで有効にする[開発者モード](/windows/uwp/get-started/enable-your-device-for-development)します。

2. プレ-作成者の更新プログラムのバージョンの Windows 10 では、まず手動で実行するリモート PC に接続している場合[をインストールしてリモート デバッガーを起動](../debugger/remote-debugging.md)します。

     XBox、HoloLens、または IoT デバイスと Windows 10 Creators Update を実行している Windows デバイスでは、リモート デバッガーを手動でインストールする必要はありません。 リモート ツールは、アプリを展開するときに自動的にインストールされます。

3. をクリックして**デバッグ > その他のデバッグ ターゲット > インストール済みアプリ パッケージのデバッグ**します。

4. 最初のドロップダウン リストから選択**リモート マシン**します。

5. 名前またはに添付するコンピューターの IP アドレスを入力します。

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     コンピューター名を使用してアタッチすることはできません場合、(選択した後**開始**)、代わりに IP アドレスを使用します。 XBox、HoloLens、IoT デバイスの IP アドレスを使用します。

6. オプションを選択して認証する方法を選択**認証モード**します。

    ほとんどのアプリでは、既定値をそのまま**ユニバーサル (暗号化されていないプロトコル)** します。

7. デバッグするアプリの名前を選択**を実行している**または**実行されていない**選択**開始**(アプリを実行) するため、または**アタッチ**します。

     選択した場合**起動しないが、開始時に、コードをデバッグ**、これは、Visual Studio デバッガーはカスタム時に起動するときに、アプリ パッケージにアタッチします。 これからコントロールのパスをデバッグする効果的な方法は、[さまざまな起動メソッド](/windows/uwp/xbox-apps/automate-launching-uwp-apps)、カスタム パラメーターでプロトコルのアクティブ化などです。

     最初に接続されているか、XBox、HoloLens、IoT デバイスにインストールされているアプリ パッケージをデバッグするときに、Visual Studio には、ターゲット デバイスのリモート デバッガーの正しいバージョンがインストールされます。 これには多少時間かかる場合があり、メッセージが表示されます``Starting remote debugger``この問題が発生します。

     > [!NOTE]
   > 存在する場合は、XBox または HoloLens デバイスは既に実行されている場合にアタッチされたデバッガー、アプリを再起動します。

UWP アプリのリモート展開の詳細設定オプションについては、[展開とデバッグ UWP apps]((/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) を参照してください。 
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)  
 [Remote Debugging](../debugger/remote-debugging.md)  
 [Windows ファイアウォールをリモート デバッグ用に構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [リモート デバッガーのポートの割り当て](../debugger/remote-debugger-port-assignments.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)