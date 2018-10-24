---
title: Visual Studio で UWP アプリのデバッグ セッションを開始 |Microsoft Docs
ms.custom: ''
ms.date: 01/04/2018
ms.technology: vs-ide-debug
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
ms.openlocfilehash: a7a9f74450ccf2cb493e44fa1fecef0630a27569
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818785"
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio"></a>Visual Studio で UWP アプリのデバッグ セッションを開始します。
  
 このトピックでは、XAML および Visual C、Visual c# または Visual Basic で記述された UWP アプリと HTML および JavaScript で記述された UWP アプリのデバッグ セッションを開始する方法について説明します。 アプリのデバッグには、デバッグ セッションの構成と、アプリの起動方法の選択の両方が関係します。  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> デバッグを開始する簡単な方法  
  
1. Visual Studio でアプリ ソリューションを開きます。  
  
2. F5 キーを選択します。  
  
   Visual Studio によってアプリがビルドされ、アタッチされたデバッガーが起動します。 実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。  
  
##  <a name="BKMK_Choose_the_build_configuration_options"></a> ビルド構成オプションを選択する  
  
1.   横にドロップダウン リストからリスト、**デバッグの開始**ボタン、デバッガーを**標準**ツールバーで、選択**デバッグ**します。  
  
2.  **[プラットフォーム]** ボックスの一覧で、ビルドするターゲット プラットフォームを選択します。  
  
##  <a name="BKMK_Choose_the_deployment_target"></a> 配置ターゲットを選択する  
  
展開して、Visual Studio コンピューター、接続されたデバイス、ローカル コンピューター、リモートのデバイスまたはエミュレーターでの Visual Studio シミュレーターで UWP アプリをデバッグできます。 右側にドロップダウン リストから配置ターゲットを選択、**プラットフォーム**デバッガーをターゲット**標準**ツールバー。
  
![配置ターゲットを選択します。](../debugger/media/vsrun_select_target_device.png)  
  
次のオプションのいずれかを選択します。  
  
|||  
|-|-|  
|**ローカル コンピューター**|ローカル コンピューターの現在のセッションでアプリをデバッグします。|  
|**シミュレーター**|UWP アプリ用の Visual Studio シミュレーターでアプリをデバッグします。 シミュレーターがデバイスの機能をデバッグできるようにするデスクトップ ウィンドウ-タッチ ジェスチャやデバイスの回転など-ローカル コンピューターで使用できません。 このオプションは使用可能な場合、アプリの**ターゲット プラットフォームの最小値。バージョン**が開発用コンピューターにオペレーティング システム未満です。 参照してください[シミュレーターでアプリの実行の UWP](../debugger/run-windows-store-apps-in-the-simulator.md)します。|  
|**リモート コンピューター**|ローカル コンピューターにイントラネットを介して接続されているかイーサネット ケーブルを使用して直接接続されているデバイス上のアプリをデバッグします。 リモートでデバッグするには、Remote Tools for Visual Studio は、リモート デバイスにインストールして実行する必要があります。 参照してください[リモート マシンでの実行の UWP アプリ](../debugger/run-windows-store-apps-on-a-remote-machine.md)します。|  
|**デバイス**|USB で接続されたデバイスでアプリをデバッグします。 デバイスは、開発者のロックを解除し、画面がロックを解除する必要があります。|  
|**モバイル エミュレーター**|エミュレーターの名で指定した構成でエミュレーターを起動、アプリのデプロイ、デバッグを開始します。 エミュレーターは、HYPER-V が有効になっているマシンでのみ利用します。|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 追加のデバッグ オプションを選択します。  

追加のデバッグ オプションを構成する必要がある場合は、プロジェクトのプロパティ ページを開きます。
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。 ショートカット メニューの **[プロパティ]** をクリックします。  
  
2.  このプロジェクトのデバッグ プロパティ ページを開く操作を行います。  
  
    -   Visual C# アプリと Visual Basic アプリの場合は、 **[デバッグ]** をクリックします。  
  
         ![C&#35; &#47; VB プロジェクト デバッグ プロパティ ページ](../debugger/media/dbg_csvb_debugpropertypage.png)  
  
    -   Visual C と JavaScript アプリでは、展開、**構成プロパティ**ノード選び、**デバッグ**します。  
  
         ![C&#43; &#43; UWP アプリのデバッグ プロパティ ページ](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> 使用するデバッガーを選択する  
既定では、Visual Studio は C# アプリと Visual Basic アプリのマネージド コードをデバッグします。 C# アプリと Visual Basic アプリでは、アプリのマネージド C/C++ コードとネイティブ C/C++ コードの両方をデバッグすることを選択できます。 C++ アプリでの Visual Studio は既定では、ネイティブ コードをデバッグします。 JavaScript アプリの場合は、Visual Studio は既定でスクリプトをデバッグします。 
  
C++ アプリと JavaScript はの代わりに、またはネイティブ コードに加えて、アプリのコンポーネントで特定の種類のコードをデバッグできます。 デバッグするコードは、アプリ プロジェクトの **[デバッグ]** プロパティ ページの **[デバッガーの種類]** の一覧で指定します。  
  
**[アプリケーション プロセス]** の一覧から次のデバッガーのいずれかを選択します。  
  
|||  
|-|-|  
|**マネージドのみ**|アプリのマネージド コードをデバッグします。 JavaScript コードとネイティブ C/C++ コードは無視されます。|  
|**ネイティブのみ**|アプリのネイティブ コードと C/C++ コードをデバッグします。 マネージド コードと JavaScript コードは無視されます。|  
|**混合 (マネージドとネイティブ)**|アプリのネイティブ C/C++ コードとマネージド コードをデバッグします。 JavaScript コードは無視されます。 このオプションの名前は C++ のプロジェクトで **(マネージとネイティブ)** します。|  
|**スクリプトのみ**|アプリの JavaScript コードをデバッグします。 マネージド コードとネイティブ コードは無視されます。|  
|**スクリプトとネイティブ**|ネイティブの C/C++ コードとアプリの JavaScript コードをデバッグします。 マネージ コードは無視されます。 C++ プロジェクトのみで使用できます。|  
|**GPU のみ (C++ AMP)**|GPU (Graphics Processing Unit) で実行されるネイティブ C++ コードをデバッグします。 C++ プロジェクトのみで使用できます。|  

C# および Visual Basic アプリで設定することも、同じ**デバッガーの種類**プロジェクトの一部である任意のバック グラウンド タスクの値。
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (省略可能) デバッグ セッションの開始を遅らせる  
 既定では、Visual Studio はデバッグの開始と同時にアプリを起動します。 デバッグ セッションは開始するが、アプリの起動は遅らせることもできます。 このオプションを選択すると、アプリは、スタート画面から起動されたとき、アクティブ化コントラクトによって起動されたとき、または別のプロセスやメソッドによって起動されたときに、デバッガー内で起動します。 アプリケーション自体が実行されていないときにバックグラウンド タスクをデバッグすると、アプリケーションの起動が遅くなります。  
  
 アプリの起動を遅らせるには:  
  
-   Visual C# アプリと Visual Basic アプリの場合は、 **[デバッグ]** プロパティ ページの **[起動しないが、開始時にコードをデバッグ]** をクリックします。  
  
-   Visual C、および JavaScript のアプリを選択**いいえ**から、**アプリケーションの起動**ボックスの一覧、**デバッグ**プロパティ ページ。  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (省略可能) ネットワーク ループバックを無効にする  
  
 セキュリティ上の理由から、標準的な方法でインストールされている UWP アプリにインストールされて、デバイスへのネットワーク呼び出しは許可されていません。 既定では、Visual Studio による配置では、配置されたアプリに対するこの規則の適用は免除されます。 この免除によって、1 台のコンピューター上で通信プロシージャをテストできます。 Microsoft Store にアプリを送信する前に、この免除なしアプリをテストする必要があります。  
  
 ネットワーク ループバックの免除を削除するには:  
  
-   Visual c# および Visual Basic アプリでは、オフ、**ローカル ネットワーク ループバックの許可**チェック ボックスをオン、**デバッグ**プロパティ ページ。  
  
-   Visual C、および JavaScript のアプリを選択**いいえ**から、**ローカル ネットワークを許可する Loopback**ボックスの一覧、**デバッグ**プロパティ ページ。  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (省略可能) デバッグの開始時にアプリケーションを再インストールする  
 Visual C# または Visual Basic アプリケーションのインストールと初期化に関する問題を診断するには、デバッグの開始時に元のインストールを再作成するように **[デバッグ]** プロパティ ページの **[Uninstall and then reinstall my package]**  (パッケージをアンインストールしてから再インストールする) をクリックします。 このオプションは、Visual C、および JavaScript プロジェクトのご利用いただけません。  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (省略可能) リモート デバッガーを起動するための認証要件を無効にする  
  
 既定では、選択した場合は、リモート デバッガーを実行する資格情報を指定する必要があります**リモート マシン**デプロイ ターゲットとして。
  
> [!IMPORTANT]
>  認証なしでリモート デバッガーを実行することもできますが、このモードはお勧めします。 このモードで実行した場合、ネットワーク セキュリティはまったく提供されません。 認証を選択しないが、ネットワークが悪意のあるコードや悪意のあるトラフィックのリスクがないことを確認する場合にのみです。  
  
 認証要件を削除するには:  
  
1.  Visual c# および Visual Basic アプリでは、次のように選択します**リモート マシン**として、**ターゲット デバイス**上、**デバッグ**プロパティ ページ、および設定して**認証モード。** に**None**または**ユニバーサル (暗号化されていないプロトコル)** します。
  
2.  Visual C と JavaScript アプリでは、次のように選択します**リモート マシン**として、**ターゲット デバイス**上、**デバッグ**プロパティ ページ、および設定して**が必要です。認証**に**None**または**ユニバーサル (暗号化されていないプロトコル)** します。  

    **ユニバーサル (暗号化されていないプロトコル)** は、リモート デバイスに展開する場合に使用します。 現時点では、これは、IoT デバイス、Xbox のデバイスと、HoloLens デバイスだけでなく Creators Update、または新しい Pc。 ユニバーサル (暗号化されていないプロトコル) は、信頼されたネットワークでのみ使用する必要があります。 デバッグ接続がインターセプトし、開発およびリモート コンピューターの間で渡されるデータを変更する悪意のあるユーザーに対して脆弱です。  
  
##  <a name="BKMK_Start_the_debugging_session"></a> デバッグ セッションを開始する  
  
###  <a name="BKMK_Start_debugging__F5_"></a> デバッグを開始する (F5)  
 選択すると**デバッグの開始** (キーボード: F5) で、**デバッグ** メニューの Visual Studio で、アタッチされたデバッガー アプリが起動します。 実行は、ブレークポイントに達するか、実行が手動で中断されるか、例外が発生するか、アプリが終了するまで続行されます。  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> デバッグは開始する (F5 キー) がアプリの起動は遅らせる  
 デバッグ モードで実行されるようにアプリを設定し、デバッガー以外の方法でアプリを起動できます。 たとえば、スタート メニューから、アプリの起動をデバッグするアプリを起動せず、アプリでバック グラウンド プロセスをデバッグまたはたい場合があります。 アプリの起動を遅らせるには、この操作を行います。  
  
- **デバッグ**アプリのプロパティ ページ (**デバッグ**Visual C と JavaScript)  
  
  -   Visual C# アプリと Visual Basic アプリの場合は、 **[起動しないが、開始時にコードをデバッグ]** をクリックします。  
  
  -   Visual C、および JavaScript のアプリを選択**はい**から、**アプリケーションの起動**一覧。  
  
- 選択**デバッグの開始**上、**デバッグ**メニュー (キーボード: F5)。  
  
- [スタート] メニュー、実行コントラクト、または別のプロシージャからアプリを起動します。  
  
  アプリがデバッグ モードで起動します。 実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。  
  
  バック グラウンド タスクのデバッグの詳細については、次を参照してください。[トリガー中断、再開、およびバック グラウンド イベントを UWP アプリ)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)します。  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> デバッガーでインストール済みのアプリを起動する  
F5 キーを使用してデバッグを開始すると、Visual Studio はアプリをビルドして配置し、デバッグ モードで実行されるようにアプリを設定してから起動します。 デバイスに既にインストールされているアプリを起動するには、使用、**インストール済みアプリ パッケージのデバッグ** ダイアログ ボックス。 この手順は、Microsoft Store のからインストールされたアプリをデバッグする必要がある場合、またはアプリでは、ソース ファイルがあるが、アプリ用の Visual Studio プロジェクトがない場合に便利です。 Visual Studio プロジェクトやソリューションを使用しないカスタム ビルド システムがこれに該当します。  
  
アプリはローカル デバイスにインストールすることも、リモート デバイスにインストールすることもできます。  アプリをすぐに起動できます。また、アプリを別のプロセスや方法で起動したときに ([スタート] メニューからの起動や、アクティブ化コントラクトによる起動など)、デバッガーで実行するようにアプリを設定することもできます。アプリを起動せずにバックグラウンド プロセスをデバッグする場合は、デバッグ モードで実行されるようにアプリを設定できます。 詳細については、次を参照してください。[トリガー中断、再開、およびバック グラウンド イベントを UWP アプリ)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)します。  
  
デバッガーでインストール済みのアプリを開始する**デバッグ**、し**他のデバッグ ターゲット**、し**インストール済みアプリ パッケージのデバッグ**します。 詳細については、次を参照してください。 [、インストールされているアプリ パッケージをデバッグ](../debugger/debug-installed-app-package.md)します。

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 実行中の UWP アプリにデバッガーをアタッチします。  

実行中の UWP アプリをデバッグするには、選択**デバッグ**、し**他のデバッグ ターゲット**、し**インストール済みアプリ パッケージのデバッグ**します。 詳細については、次を参照してください。 [、インストールされているアプリ パッケージをデバッグ](../debugger/debug-installed-app-package.md)します。
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 実行中の Windows 8.x アプリにデバッガーをアタッチします。
 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリにデバッガーをアタッチするには、デバッグ可能パッケージ マネージャーを使用して、デバッグ モードで実行するようにアプリを設定する必要があります。 デバッグ可能パッケージ マネージャーは、Visual Studio 用リモート ツールと共にインストールされます。  
  
 アプリへのデバッガーのアタッチは、インストール済みのアプリ ( [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]からインストールされたアプリなど) をデバッグする場合に役に立ちます。 アタッチは、アプリのソース ファイルはあるが、アプリの Visual Studio プロジェクトがない場合に必要です。 Visual Studio プロジェクトやソリューションを使用しないカスタム ビルド システムがこれに該当します。  
  
 アプリにデバッガーをアタッチするには、次の手順に従う必要があります。  
  
1.  デバッグ モードで実行するようにアプリを設定します。 これは、アプリが実行されていないときに行う必要があります。  
  
2.  アプリを起動します。 アプリの起動は、スタート画面、実行コントラクト、または他の方法で実行できます。  
  
3.  実行中のアプリにデバッガーをアタッチします。  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> デバッグ モードで実行するようにアプリを設定する  
  
1.  Visual Studio のアプリがインストールされているデバイスでリモート ツールをインストールします。 参照してください[remote tools のインストール](../debugger/remote-debugging.md)します。  
  
2.  スタート画面で `Debuggable Package Manager` を検索して起動します。  
  
     AppxDebug コマンドレット用に適切に構成された PowerShell ウィンドウが表示されます。  
  
3.  アプリのデバッグを有効にするには、アプリの PackageFullName 識別子を指定する必要があります。 PackageFullName を含むすべてのアプリの一覧を表示するには、PowerShell プロンプトに「 `Get-AppxPackage` 」と入力します。  
  
4.  PowerShell プロンプトに「 `Enable-AppxDebug` *PackageFullName* 」と入力します。 *PackageFullName* はアプリの PackageFullName 識別子です。  
  
####  <a name="BKMK_Attach_the_debugger"></a> デバッガーをアタッチします。  
 デバッガーをアタッチするには:  
  
1. **[デバッグ]** メニューの **[プロセスにアタッチ]** をクリックします  
  
    **[プロセスにアタッチ]** ダイアログ ボックスが表示されます。  
  
2. リモート デバイス上のアプリにアタッチするには、 **[修飾子]** ボックスにリモート デバイスを指定します。 次の操作を行うことができます。  
  
   -   **[修飾子]** ボックスに名前を入力します。  
  
   -   **[修飾子]** ボックスの下向き矢印をクリックし、デバイスの一覧から前にアタッチしたデバイスを選択します。  
  
   -   **[検索]** をクリックし、ローカル サブネットのデバイスの一覧からデバイスを選択します。  
  
3. デバッグするコードの種類を **[アタッチ先]** ボックスに指定します。  
  
    **[選択]** をクリックし、次のいずれかを実行します。  
  
   -   **[デバッグするコードの種類を自動的に判断する]** をクリックします。  
  
   -   **[次のコードの種類をデバッグする]** をクリックし、一覧から 1 つ以上の型を選択します。  
  
4. **[選択可能なプロセス]**  の一覧から、アプリのプロセスを選択します。  

   > [!NOTE]
   >  その他のアプリの種類とは異なりは、JavaScript アプリは、wwahost.exe プロセスのインスタンスで実行します。 アプリにアタッチする際に他の JavaScript アプリが実行されている場合、そのアプリが実行されている wwahost.exe の数値型プロセス ID (PID) を確認する必要があります。  
   >   
   >  このような状況に対処する最も簡単な方法は、他の JavaScript アプリをすべて閉じることです。 別の方法として、アプリを起動する前に Windows タスク マネージャーを開き、wwahost.exe プロセスの ID を確認できます。 アタッチするプロセスを指定すると、**選択可能なプロセス**ダイアログ ボックスで、アプリの wwahost.exe には、メモしたものと異なるは、id が必要があります。  
  
5. **[アタッチ]** をクリックします。  
  
   Visual Studio によって、デバッガーがプロセスにアタッチされます。 実行は、ブレークポイントに達するか、実行が手動で中断されるか、ハンドルされない例外が発生するか、アプリが終了するまで続行されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのアプリのデバッグ](../debugger/debug-store-apps-in-visual-studio.md)   