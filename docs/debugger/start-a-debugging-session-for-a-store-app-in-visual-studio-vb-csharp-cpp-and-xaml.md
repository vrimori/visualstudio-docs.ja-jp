---
title: UWP アプリのデバッグ セッションを開始 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 3c2ef4e92cddb302e67f99c921750d4e9e83d98e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901987"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>UWP アプリのデバッグ セッションを開始する
  
この記事では、ユニバーサル Windows プラットフォーム (UWP) アプリの Visual Studio デバッグ セッションを開始する方法について説明します。 UWP アプリは、XAML、C++、XAML で記述することができますとC#/Visual Basic、または HTML と JavaScript です。 UWP アプリのデバッグを開始するには、デバッグ セッションを構成し、アプリの起動方法を選択します。  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Visual Studio のツールバーからデバッグを開始します。 
  
構成して、デバッグを開始する最も簡単な方法は、標準の Visual Studio ツールバーです。 

![ツールバーをデバッグします。](../debugger/media/vsrun_select_target_device.png)  
  
1. **構成**ボックスの一覧、**標準**ツールバーで、**デバッグ**します。  
  
1. **プラットフォーム**ドロップダウンで、用にビルドするターゲット プラットフォームを選択します。 
   
1. 緑色の矢印の横にあるドロップダウン リストから、デバッグ ターゲットを選択します。 ローカル コンピューター、デバイスの直接接続、ローカルの Visual Studio シミュレーター、リモート デバイスまたはエミュレーターを選択できます。 
   
1. デバッグを開始するには、緑を選択します**開始**ツールバー、または select の矢印**デバッグ** > **デバッグの開始**、またはキーを押します**F5**。. 
   
   Visual Studio によってアプリがビルドされ、アタッチされたデバッガーが起動します。 

デバッグするには、ブレークポイントに到達する、手動で実行を中断した、ハンドルされない例外が発生するか、アプリが終了するまでが続行されます。  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> 展開ターゲットのオプション 
  
Visual Studio のツールバーでデバッグ ターゲットを設定できるまたはプロジェクトのプロパティ ページをデバッグします。 次のいずれかのオプションを選択します。

|||  
|-|-|  
|**ローカル コンピューター**|ローカル コンピューターの現在のセッションでアプリをデバッグします。|  
|**シミュレーター**|UWP アプリ用の Visual Studio シミュレーターでアプリをデバッグします。 シミュレーターは、デバイスで動作するタッチ ジェスチャと、ローカル コンピューター上にない可能性がありますデバイスの回転をシミュレートするデスクトップ ウィンドウです。 シミュレーターのオプションがある場合にのみ、アプリの**ターゲット プラットフォームの最小値。バージョン**がローカル コンピューター上のオペレーティング システム未満です。 詳細については、次を参照してください。[シミュレーターでアプリの実行の UWP](../debugger/run-windows-store-apps-in-the-simulator.md)します。|  
|**リモート コンピューター**|イーサネット ケーブルまたはネットワーク上のローカル コンピューターに接続されているデバイスでアプリをデバッグします。 Remote Tools for Visual Studio インストールされ、リモート デバイスで実行されている必要があります。 詳細については、次を参照してください。[リモート マシンでの実行の UWP アプリ](../debugger/run-windows-store-apps-on-a-remote-machine.md)します。|  
|**デバイス**|USB で接続されたデバイスでアプリをデバッグします。 デバイスは、開発者のロックを解除し、画面がロックを解除する必要があります。|  
|**モバイル エミュレーター**|エミュレーターの名で指定されたエミュレーターを起動、アプリのデプロイ、デバッグを開始します。 エミュレーターは、HYPER-V が有効になっているマシンでのみ使用できます。|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> プロジェクトのプロパティ ページでのデバッグを構成します。 

追加のデバッグ オプションを構成するには、プロジェクトのデバッグ プロパティ ページを使用します。 

**デバッグのプロパティを開きます。**

1. **ソリューション エクスプ ローラー**、プロジェクトを選択し、、**プロパティ**アイコン、またはプロジェクトを右クリックし、選択**プロパティ**します。  
   
1. 左側にある、**プロパティ**ウィンドウ。
   
   - C#と Visual Basic アプリで、**デバッグ**します。  
     
     ![C#Visual Basic プロジェクト デバッグ プロパティ ページ](../debugger/media/dbg_csvb_debugpropertypage.png)  
   
   - C++ と JavaScript アプリでは、次のように選択します。**構成プロパティ** > **デバッグ**します。  
     
     ![C++ UWP アプリのデバッグ プロパティ ページ](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> 使用するデバッガーを選択する  

C#と既定では、マネージ コードを Visual Basic アプリでは、Visual Studio のデバッグ。 その他のまたは追加のコードをデバッグすることができます。 設定することも**デバッガーの種類**プロジェクトの一部である任意のバック グラウンド タスクの値。

C++ アプリでの Visual Studio は既定では、ネイティブ コードをデバッグします。 JavaScript アプリの場合は、Visual Studio は既定でスクリプトをデバッグします。 特定の種類のコードの代わりに、またはだけでなく、ネイティブ コードをデバッグすることができます。 

**デバッグするコードの種類を指定します。**

- C# Visual Basic アプリの場合を選択してから次のデバッガーのいずれかと、**アプリケーションの種類**と**バック グラウンド処理の種類**ドロップダウン リストから **デバッガーの種類**で**デバッグ**プロパティ ページ。  
  
- C++/cli、JavaScript アプリから次のデバッガーのいずれかを選択、**デバッガーの種類**ボックスの一覧、**デバッグ**プロパティ ページ。

|||  
|-|-|  
|**マネージドのみ**|アプリのマネージド コードをデバッグします。 JavaScript コードとネイティブ C/C++ コードは無視されます。|  
|**ネイティブのみ**|アプリのネイティブ コードと C/C++ コードをデバッグします。 マネージド コードと JavaScript コードは無視されます。|  
|**混合 (マネージドとネイティブ)**|アプリのネイティブ C/C++ コードとマネージド コードをデバッグします。 JavaScript コードは無視されます。 このオプションの名前は C++ のプロジェクトで**マネージとネイティブ**します。|  
|**スクリプト**|アプリの JavaScript コードをデバッグします。 マネージド コードとネイティブ コードは無視されます。|  
|**スクリプトを利用したネイティブ コード**|ネイティブの C/C++ コードとアプリの JavaScript コードをデバッグします。 マネージ コードは無視されます。 C++ プロジェクトまたはバック グラウンド タスクのみで使用できます。|  
|**GPU のみ (C++ AMP)**|GPU (Graphics Processing Unit) で実行されるネイティブ C++ コードをデバッグします。 C++ プロジェクトのみで使用できます。|  

  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (省略可能) ネットワーク ループバックを無効にします。 
  
 セキュリティ、標準的な方法でインストールされている UWP アプリはネットワーク呼び出しにインストールされて、デバイスを作成できません。 Visual Studio の除外対象では、既定では、この規則からのアプリが展開されるため、1 台のコンピューター上で通信プロシージャをテストすることができます。 アプリをリリースする前に、この免除なしアプリをテストする必要があります。  
  
**ネットワーク ループバックの免除を削除するには:**  
  
-   C# Visual Basic アプリの場合は、選択を解除し、**ローカル ネットワーク ループバックの許可**下のチェック ボックス**開始オプション**上、**デバッグ**プロパティ ページ。  
  
-   Visual C と JavaScript アプリでは、次のように選択します。**いいえ**から、**ローカル ネットワーク Loopback のを許可する**ボックスの一覧、**デバッグ**プロパティ ページ。  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> デバッグの開始時 (省略可能) アプリを再インストールします。 
 インストールの問題を診断する、C#または Visual Basic アプリで、**アンインストールし、パッケージを再インストール**上、**デバッグ**プロパティ ページ。 このオプションは、デバッグを開始するときに、元のインストールを再作成されます。 このオプションは C++ および JavaScript のプロジェクトで使用できます。  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> リモート デバッグ用の認証オプションを設定します。  
  
既定では、選択した場合は、リモート デバッガーを実行する Windows 資格情報を指定する必要があります**リモート マシン**デプロイ ターゲットとして。 認証の要件を変更することができます。 

**ユニバーサル (暗号化されていないプロトコル)** 認証モードは、IoT、Xbox、HoloLens デバイスと作成者の更新プログラムまたは以降の Windows 10 Pc。  

**認証方法を変更するには。**  

- C#と Visual Basic アプリの場合は、上、**デバッグ**プロパティ ページで、**リモート マシン**として、**ターゲット デバイス**します。 次に、選択**None**または**ユニバーサル (暗号化されていないプロトコル)** の**認証モード**します。 
  
- C++ と JavaScript アプリでは、次のように選択します。**リモート マシン****起動するデバッガー**上、**デバッグ**プロパティ ページ。 次に、選択**認証なし**または**ユニバーサル (暗号化されていないプロトコル)** の**認証の種類**します。 
  
> [!CAUTION]
> リモート デバッガーを実行すると、ネットワークのセキュリティがない**None**または**ユニバーサル (暗号化されていないプロトコル)** モード。 悪意のあるコードや悪意のあるトラフィックのリスクとしている信頼されたネットワーク上でのみこれらのモードをいないことを確認を選択します。  
  
##  <a name="BKMK_Start_the_debugging_session"></a> デバッグの開始オプション  
  
選択すると**デバッグ** > **デバッグの開始**またはキーを押します**f5 キーを押して**、Visual Studio がアタッチされたデバッガーでアプリを起動します。 実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> アプリの起動の遅延が、デバッグを開始します。  

既定では、Visual Studio は、デバッグを開始するときにすぐにアプリを起動します。 デバッグ モードで実行されますが、デバッガーの外部のアプリケーションを開始するアプリを設定することもできます。 Windows アプリの起動をデバッグするなど、**開始**メニューのまたはアプリのバック グラウンド プロセスをデバッグします。 このオプションを選択した場合、アプリの起動時にデバッガーで開始します。 

**アプリの自動起動を無効にします。**  
  
- C#と Visual Basic アプリで、**起動しないが、開始時に、コードをデバッグ****開始オプション**上、**デバッグ**プロパティ ページ。  
   
- C++ と JavaScript アプリでは、次のように選択します。**いいえ**から、**アプリケーションの起動**ボックスの一覧、**デバッグ**プロパティ ページ。  
  
バック グラウンド タスクのデバッグの詳細については、次を参照してください。[トリガー中断、再開、および UWP アプリ用のイベントをバック グラウンド](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)します。  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> インストールされているか、実行中の UWP アプリをデバッグします。 

使用することができます**インストール済みアプリ パッケージのデバッグ**が既にインストールされているか、ローカルまたはリモート デバイスで実行されている UWP アプリをデバッグします。 アプリを Microsoft Store からインストールする可能性があります。 または Visual Studio プロジェクトができない可能性があります。 たとえば、アプリには、Visual Studio を使用しないカスタム ビルド システムがあります。  
  
インストールされているアプリをすぐに開始することができますか、別の方法で開始すると、デバッガーで実行するように設定することができます。 詳細については、次を参照してください。[トリガー中断、再開、およびバック グラウンド イベントを UWP アプリ)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)します。  
  
デバッガーでインストールまたは実行中の UWP アプリを起動する**デバッグ** > **その他のデバッグ ターゲット** > **インストール済みアプリ パッケージのデバッグ**します。 詳細については、次を参照してください。 [、インストールされているアプリ パッケージをデバッグ](../debugger/debug-installed-app-package.md)します。

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 実行中の Windows 8.x アプリにデバッガーをアタッチします。

[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリにデバッガーをアタッチするには、デバッグ可能パッケージ マネージャーを使用して、デバッグ モードで実行するようにアプリを設定する必要があります。 デバッグ可能パッケージ マネージャーは、Visual Studio 用リモート ツールと共にインストールされます。  
  
1. Visual Studio のアプリがインストールされているデバイスでリモート ツールをインストールします。 詳細については、次を参照してください。 [remote tools のインストール](../debugger/remote-debugging.md)します。  
   
1. Windows で**開始**画面で、検索を開始して**デバッグ可能パッケージ マネージャー**します。  
   
   AppxDebug コマンドレット用に適切に構成された PowerShell ウィンドウが表示されます。  
   
1. アプリの PackageFullName 識別子を指定します。 
   
   1. すべてのアプリの PackageFullName を含む一覧を表示する次のように入力します。 `Get-AppxPackage` PowerShell プロンプトでします。  
   
   1. PowerShell プロンプトで次のように入力します。`Enable-AppxDebug <PackageFullName>`ここで、 \<PackageFullName > は、アプリの PackageFullName 識別子です。  
   
1. **[デバッグ]** > **[プロセスにアタッチ]** の順に選択します。  
   
1. **プロセスにアタッチ** ダイアログ ボックスで、リモート デバイスの指定、**接続のターゲット**ボックス。 
   
   デバイス名を入力、ドロップダウン リストから選択できます、**接続のターゲット**ボックス、または選択**検索**でデバイスを検索する、**リモート接続** ダイアログ ボックス。  
   
1. 次に、デバッグするコードの種類を指定する、**にアタッチ**ボックスで、**選択**します。  
   
1. **コードの種類の選択** ダイアログ ボックスで、いずれかを選択します。
   - **デバッグするコードの種類を自動的に決定**、または 
   - **これらのコードの種類をデバッグ**、一覧から 1 つまたは複数のコードの種類を選択します。  
   
1. **選択可能なプロセス**一覧で、アプリのプロセスをデバッグするを選択します。  
   
1. 選択**アタッチ**します。  
  
 Visual Studio によって、デバッガーがプロセスにアタッチされます。 実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。

> [!NOTE]
> JavaScript アプリは、*wwahost.exe* プロセスのインスタンスで実行されます。 1 つ以上の JavaScript アプリが実行されているアプリの数値型プロセス id (PID) を確認する必要があります*wwahost.exe*をアタッチするプロセス。  
> 
> JavaScript アプリにアタッチする最も簡単な方法は、その他のすべての JavaScript アプリを閉じることです。 または、実行中の Pid を記録して*wwahost.exe*プロセス Windows タスク マネージャーでは、アプリを開始する前にします。 アプリを起動するときにその*wwahost.exe* PID が以前にメモしたものとは異なるものになります。  

## <a name="see-also"></a>関連項目  
 [Visual Studio でのアプリのデバッグ](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)   