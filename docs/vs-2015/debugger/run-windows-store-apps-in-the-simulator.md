---
title: Windows ストア アプリの実行、シミュレーターで |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3007d0e6ea7a835cd9147f5f5ff94c91f9f7bda4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544364"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>シミュレーターでの Windows ストア アプリの実行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Windows ストア アプリの実行、シミュレーターで](https://docs.microsoft.com/visualstudio/debugger/run-windows-store-apps-in-the-simulator)します。  
  
Windows ストア アプリ用の Visual Studio シミュレーターは、Windows ストア アプリをシミュレートするデスクトップ アプリケーションです。 開発者は、アプリケーションの実行と、一般的なタッチと回転イベントのシミュレーションを開発用コンピューター上で行うことができます。 また、エミュレートする物理的な画面サイズと解像度を選択したり、ネットワーク接続のプロパティをシミュレートしたりすることもできます。  
  
 シミュレーターは、Windows ストア アプリを設計、開発、デバッグ、テストできる環境を提供します。 ただし、Windows ストアにアプリを公開する前に、実際のデバイスでアプリをテストする必要があります。  
  
 Windows ストア アプリ用の Visual Studio シミュレーターは、ローカル コンピューターの分離環境では実行されません。 したがって、シミュレーターで発生したエラー (回復できないシステム エラーなど) がコンピューター全体に影響を与える場合があります。  
  
 Windows Phone について詳しくは、「 [Run Windows Phone apps in the emulator](../debugger/run-windows-phone-apps-in-the-emulator.md) 」を参照してください。  
  
> [!IMPORTANT]
>  Visual Studio 2015 シミュレーターには、位置情報ボタンがありません。 これは、Windows 10 シミュレーターに位置情報シミュレーションが含まれていないためです。 この種のシミュレーションを行う必要がある場合は、Windows 8.1 以前のオペレーティング システム上で Visual Studio 2013 シミュレーターを使用できます。  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> シミュレーターをターゲットとして設定する  
 Windows ストア アプリをシミュレーターで実行するには、デバッガーの **標準** ツールバーの **[デバッグの開始]** ボタンの横にあるドロップダウン リストの **[シミュレーター]** をクリックします。  
  
 ![シミュレーターで実行されている](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> 対話モードを選択する  
 次の対話モードを選択できます。  
  
-   ![マウス モード ボタン](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn")マウス モード: 対話モードをマウス ジェスチャに設定します。 マウス ジェスチャには、クリック、ダブルクリック、およびドラッグがあります。  
  
-   ![タッチ エミュレーション [スタート] ボタン](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn")タッチ エミュレーションの開始: 対話モードを 1 本の指のタッチ ジェスチャに設定します。 1 本指のイベントには、タップ、ドラッグ、およびスワイプがあります。  
  
     ![シミュレーターの 1 本の指のターゲット](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger")シングル ターゲット アイコンは、シミュレーター内のイベントの場所を示します。 ポインターを配置するには、マウスを使用します。  
  
     ![1 本指タッチのターゲット](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged")タッチ モードをアクティブにマウスの左ボタンを押します。 たとえば、タップをシミュレートする場合はボタンをクリックし、ドラッグまたはスワイプする場合はボタンを長押しします。  
  
## <a name="pinch-and-zoom"></a>ピンチとズーム  
 対話モードを、2 本の指によるピンチ ジェスチャとズーム ジェスチャに設定します。  
  
-   ![シミュレーターの 2 本指のターゲット](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  
  
     ダブル ターゲット アイコンは、デバイス画面上の 2 本の指の位置を示します。  
  
    -   デバイス画面上のオブジェクトの上にアイコンを配置するには、マウスを移動します。  
  
    -   ピンチまたはズームを実行する前の 2 本の指のシミュレートされる距離を変更するは、マウス ホイールを前方または後方に回転させます。  
  
-   -   ![ピンチ、ズーム、およびターゲットを回転](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         縮小 (ピンチ) する場合は、左ボタンを押し、ホイールを後方 (手前) に回転させます。  
  
    -   拡大 (ズーム) する場合は、左ボタンを押し、マウス ホイールを前方 (奥) に回転させます。  
  
## <a name="object-rotation"></a>オブジェクトの回転  
 **[タッチ エミュレーションの回転]** ボタンは、対話モードを、2 本の指による回転ジェスチャに設定します。  
  
-   -   デバイス画面上のオブジェクトの上にアイコンを配置するには、マウスを移動します。  
  
    -   オブジェクトの回転を実行する前の 2 本の指のシミュレートされる方向を変更するは、マウス ホイールを前方または後方に回転させます。  
  
-   -   オブジェクトを反時計回りに回転させる場合は、左ボタンを押し、ホイールを後方 (手前) に回転させます。 マウス ホイールを回転させると、回転の相対サイズを示すために、2 つのターゲット アイコンのいずれかが他方のアイコンを中心として回転します。  
  
    -   オブジェクトを時計回りに回転させる場合は、左ボタンを押し、マウス ホイールを前方 (奥) に回転させます。  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> [常に手前に表示] モードを有効または無効にする  
 シミュレーター ウィンドウが常に他のウィンドウの上に表示されるように設定できます。 **[最前面に表示するウィンドウの切り替え]** ボタンは、シミュレーター ウィンドウの **[常に手前に表示]** モードを有効または無効にします。  
  
##  <a name="BKMK_Change_the_device_orientation"></a> デバイスの方向を変更する  
 シミュレーターを任意の方向に 90 度回転させることで、デバイスの方向を縦長と横長の間で切り替えることができます。  
  
> [!NOTE]
>  シミュレーターでは、プロジェクトのプロパティ [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) は考慮されません。 たとえば、プロジェクトで方向が `Landscape`に設定されている場合でも、シミュレーターの方向を回転させて縦向きにすると、シミュレーターに表示されるイメージも回転され、サイズが変更されます。 実際のデバイスでこれらの設定をテストしてください。  
  
> [!NOTE]
>  シミュレーターを回転させたときに、シミュレーターの 1 つの辺がシミュレーターを表示している画面よりも大きくなる場合、シミュレーターのサイズは画面に収まるように自動的に変更されます。 シミュレーターは、再度回転させた場合でも、元のサイズに戻ることはありません。  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> シミュレートされる画面のサイズと解像度を変更する  
 シミュレートされる画面のサイズと解像度を変更するには、パレットの **[解像度の変更]** ボタンをクリックし、一覧から新しいサイズと解像度を選択します。  
  
 画面サイズと解像度は *画面の幅 (インチ)、ピクセル幅 X ピクセル高さ*で一覧表示されます。 画面のサイズと解像度の両方がシミュレートされます。 シミュレーター上の位置座標は、選択したデバイスのサイズと解像度の座標に変換されます。  
  
> [!NOTE]
>  ビットマップ イメージのスケーリングされたバージョンをアプリに保存できます。Windows は、現在のスケールで正しいイメージを読み込みます。 詳細については、次を参照してください。[レスポンシブ デザイン 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)します。 ただし、Windows によって解像度に合ったイメージが選択されるようにシミュレーターの解像度を変更した場合、新しいイメージを表示するにはデバッグ セッションを停止して再度開始する必要があります。  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Windows ストアに送信するアプリのスクリーンショットをキャプチャする  
 Windows アプリ ストアにアプリを送信するときは、アプリのスクリーンショットを含める必要があります。  
  
> [!NOTE]
>  スクリーンショットは、シミュレーターの現在の解像度で保存されます。 解像度を変更するには、 **[解像度の変更]** ボタンをクリックします。  
  
-   シミュレーターからアプリのスクリーンショットを作成するには、 **[クリップボードにスクリーンショットをキャプチャします]** ボタンをクリックします。  
  
-   スクリーンショットの配置場所を設定するには、 **[スクリーンショットの設定]** ボタンをクリックし、ショートカット メニューから場所を選択します。  
  
     ![設定のコンテキスト メニューのスクリーン ショット](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> ネットワーク接続のプロパティをシミュレートする  
 アプリケーションのユーザーがネットワーク接続コストやデータ プランの状態の変化を認識し、アプリケーションがその情報を使用して、ローミングや指定されたデータ転送の制限の超過による追加コストの発生を避けることにより、アプリケーションのユーザーが従量制課金接続のコストを管理できるようにします。 [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) Api に応答できます。 [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx)と[TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx)署名を行うイベント。 「 [従量制課金接続のコスト制約を管理する方法 (HTML)](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)」をご覧ください。  
  
 シミュレーターをデバッグまたは、ネットワーク コストを認識するコードをテスト、を通じて公開されているネットワークのプロパティを模倣できます、 [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx)によって返されるオブジェクト[GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx).  
  
 ネットワークのプロパティをシミュレートするには、次のようにします。  
  
1.  シミュレーターのツール バーの **[ネットワーク プロパティの変更]** ボタンをクリックします。  
  
2.  **[ネットワーク プロパティの設定]** ダイアログ ボックスの **[シミュレートされたネットワーク プロパティの使用]** をクリックします。  
  
     チェック ボックスをオフにしてシミュレーションを削除し、現在接続されているインターフェイスのネットワーク プロパティに戻ります。  
  
3.  シミュレートされたネットワークの **[プロファイル名]** を入力します。 シミュレーションを識別するために使用できる一意の名前を使用することをお勧めします。、 [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx)のプロパティ、 [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx)オブジェクト。  
  
4.  選択、 [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx)からプロファイルの値、**ネットワーク コストの種類**一覧。  
  
5.  **データの限度の状態フラグ**] ボックスの一覧を設定できます、 [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx)プロパティまたは[OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)プロパティを true を選択または**データの制限 [** 両方の値を false に設定します。  
  
6.  **ローミングの状態**一覧で、設定、[ローミング](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx)プロパティ。  
  
7.  選択**プロパティの設定**、前景をトリガーすることによって、ネットワークのプロパティをシミュレートするために[NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx)イベントとバック グラウンド[SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx)型の**NetworkStateChange**します。  
  
 **ネットワーク接続の管理の詳細について**  
  
 [従量制課金接続のコスト制約を管理する方法 (HTML)](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [ネットワーク情報のサンプル](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [エネルギー使用の分析](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
 [バックグラウンド タスクでシステム イベントに応答する方法](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [Windows ストア アプリの中断イベント、再開イベント、およびバックグラウンド イベントをトリガーする方法](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> キーボードを使用してシミュレーター内を移動する  
 **Ctrl + Alt + 上矢印キー** を押してシミュレーター ウィンドウからシミュレーター ツールバーにフォーカスを切り替えて、シミュレーター ツールバーをナビゲートできます。 ツール バーのボタンの間を移動するには、 **上向きの矢印** と **下向きの矢印** を使用します。  
  
 シミュレーターを終了するには、 **CTRL+ALT+F4**キーを押します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio からアプリを実行](../debugger/run-store-apps-from-visual-studio.md)



