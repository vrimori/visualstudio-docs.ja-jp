---
title: "インストールされているアプリ パッケージ (UWP) をデバッグ |Microsoft ドキュメント"
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: e21d29c3a95de4e5174a9966665f3e4e6781f726
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Visual Studio (UWP) にインストールされているアプリ パッケージをデバッグします。

任意のインストール済みアプリ パッケージをデバッグするをクリックすると**デバッグ > その他のデバッグ ターゲット > インストール済みアプリ パッケージのデバッグ**です。 このデバッグ メソッドは、これらのデバイスでユニバーサル Windows アプリ (UWP) を入手できます。

* Windows 10 (携帯電話ではサポートされていません)
* XBox
* HoloLens
* IoT

これらの機能に関する詳細については、ブログの投稿用更新プログラムを参照してください。[インストール済みアプリ パッケージのデバッグ](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)およびで post[ユニバーサル Windows アプリ (UWP) を構築](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/)です。

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>インストールされているアプリのパッケージまたはローカル コンピューターまたはデバイスで実行中のアプリをデバッグします。

1. UWP プロジェクトを Visual Studio で開いて、をクリックして**デバッグ > その他のデバッグ ターゲット > インストール済みアプリ パッケージのデバッグ**です。

2. いずれかを選択**ローカル マシン**または**デバイス**です。

     選択した場合**デバイス**、お使いのコンピューターを Windows 10 デバイスに物理的に接続する必要があります。

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     下にアプリ パッケージの表示がインストールされている現在実行中、**を実行している**ノード。 インストールされているアプリ パッケージは実行されている番組を**が実行されていない**です。

3. デバッグするアプリの名前を選択**を実行している**または**が実行されていない**を選択し、**開始**、アプリが既に実行されている場合は、「**アタッチ**.

     選択した場合**起動しないが、開始時に、コードをデバッグ**、これは、Visual Studio デバッガーはユーザー設定時に起動するときに、アプリにアタッチします。 コントロールのパスをデバッグする効果的な方法は、この[別の起動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)、カスタム パラメーターでプロトコルのアクティブ化などです。

> [!NOTE]
> 選択して、visual Studio は、実行中の UWP アプリのプロセスにアタッチもできる**デバッグ**、し**プロセスにアタッチする**です。 実行中のプロセスにアタッチすると、元の Visual Studio プロジェクトが必要としないもので、プロセスのシンボルの読み込みが大幅の元のコードがないプロセスをデバッグするとき。
  
## <a name="remote"></a>リモート コンピューター上のインストールまたは実行されているアプリをデバッグします。 

最初にリモート コンピューターにインストールされているアプリ パッケージをデバッグするときに、Visual Studio は、対象デバイス用のリモート ツールの正しいバージョンをインストールします。 ターゲット デバイスは、Windows 10 コンピューター、XBox、HoloLens や IoT デバイスである必要があります。

1. Windows 10 デバイスで有効にする[開発者モード](/windows/uwp/get-started/enable-your-device-for-development)です。

2. Windows 10 のより前の作成者の更新プログラムのバージョンをまず手動で実行するリモート PC に接続する場合は[をインストールし、リモート デバッガーを起動](../debugger/remote-debugging.md)です。

     XBox、HoloLens や IoT デバイスと Windows 10 の作成者の更新プログラムを実行している Windows デバイスの場合は、リモート デバッガーを手動でインストールする必要はありません。 リモート ツールは、アプリを展開するときに自動的にインストールされます。

3. をクリックして**デバッグ > その他のデバッグ ターゲット > インストール済みアプリ パッケージのデバッグ**です。

4. 最初のドロップダウン リストから選択**リモート マシン**です。

5. 名前またはに添付するコンピューターの IP アドレスに入力します。

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     コンピューター名を使用した接続できない場合 (選択した後**開始**)、代わりに IP アドレスを使用します。 XBox、HoloLens や IoT デバイスの IP アドレスを使用します。

5. オプションを選択して認証する方法を選択して**認証モード**です。

    ほとんどのアプリの既定値の保持、**ユニバーサル (暗号化されていないプロトコル)**です。

6. デバッグするアプリの名前を選択**を実行している**または**が実行されていない**を選択し、**開始**または (アプリの実行)**アタッチ**です。

     選択した場合**起動しないが、開始時に、コードをデバッグ**、これにより、Visual Studio デバッガーをカスタム時に起動するときにアプリ パッケージにアタッチします。 コントロールのパスをデバッグする効果的な方法は、この[別の起動方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)、カスタム パラメーターでプロトコルのアクティブ化などです。

     最初に接続された XBox、HoloLens や IoT デバイスでインストールされているアプリ パッケージをデバッグするときに、Visual Studio は、対象デバイスのリモート デバッガーの正しいバージョンをインストールします。 少しの時間がかかります、メッセージが表示されます``Starting remote debugger``この問題が発生します。

     > [!NOTE]
> 存在する、XBox または HoloLens デバイスは既に実行されている場合にアタッチされたデバッガーで、アプリを再起動します。

> [!NOTE]
> UWP アプリは開発できますが Windows 8.1 以降で、コンパイルし Windows 10 を実行する必要があります。 Windows 8.1 PC で UWP アプリを開発している場合をする、同じ LAN 上のホストとターゲットの両方のコンピューターが別の Windows 10 デバイスで実行されている UWP アプリでのリモート デバッグできます。 これを行うには、ダウンロードして Visual Studio の両方のコンピューターでリモート ツールをインストールします。 インストールされているバージョンがインストールされている Visual Studio の既存のバージョンと一致しなければなりません、アーキテクチャ (x86、x64) を選択する必要がありますもの一致する対象のアプリです。

UWP アプリのリモート展開の詳細設定オプションについては、次を参照してください。[の展開と UWP アプリのデバッグ](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps.md#advanced-remote-deployment-options)です。 
  
## <a name="see-also"></a>参照  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)  
 [Remote Debugging](../debugger/remote-debugging.md)  
 [Windows ファイアウォールをリモート デバッグ用に構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [リモート デバッガーのポートの割り当て](../debugger/remote-debugger-port-assignments.md)  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)