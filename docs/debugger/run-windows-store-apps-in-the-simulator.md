---
title: "UWP と Windows 8.1 アプリをシミュレーターで実行 |Microsoft ドキュメント"
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
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf4c5d1e71a4d0e0d8ac74ba02bff29ddc1c7477
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-and-windows-81-apps-in-the-simulator"></a>シミュレーターでの UWP と Windows 8.1 アプリの実行
UWP と Windows 8.1 アプリの Visual Studio シミュレーターは、UWP または Windows 8.1 アプリをシミュレートするデスクトップ アプリケーションです。 実行することができます、物理的な画面サイズと解像度をエミュレートするために、アプリケーションを選択します。 一般的なタッチと回転イベントのシミュレーションや、ネットワーク接続のプロパティをシミュレートすることができますも。
  
 シミュレーターを設計、開発、デバッグ、および UWP アプリをテスト環境を提供します。 ただし、Microsoft ストアにアプリを発行する前に、実際のデバイスでアプリをテストする必要があります。  
  
 UWP アプリの Visual Studio シミュレーターは、ローカル コンピューターでは、分離された環境で実行されません。 したがって、シミュレーターで発生したエラー (回復できないシステム エラーなど) がコンピューター全体に影響を与える場合があります。  
  
 Windows Phone について詳しくは、「 [Run Windows Phone apps in the emulator](../debugger/run-windows-phone-apps-in-the-emulator.md) 」を参照してください。  
  
> [!IMPORTANT]
>  Visual Studio 2015 シミュレーターには、位置情報ボタンがありません。 これは、Windows 10 シミュレーターに位置情報シミュレーションが含まれていないためです。 この種のシミュレーションを行う必要がある場合は、Windows 8.1 以前のオペレーティング システム上で Visual Studio 2013 シミュレーターを使用できます。  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> シミュレーターをターゲットとして設定する  
 UWP アプリをシミュレーターで実行するには、選択**シミュレーター**ドロップ ダウン リストから次に、**デバッグの開始**デバッガーのボタン**標準**ツールバー。  
  
 ![シミュレーターで実行されている](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> 対話モードを選択する  
 次の対話モードを選択できます。  
  
-   ![マウス モード ボタン](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn")マウス モード: 対話モードをマウス ジェスチャに設定します。 マウス ジェスチャには、クリック、ダブルクリック、およびドラッグがあります。  
  
-   ![タッチ エミュレーション [スタート] ボタン](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn")タッチ エミュレーションの開始: 対話モードの 1 本の指によるタッチ ジェスチャに設定します。 1 本指のイベントには、タップ、ドラッグ、およびスワイプがあります。  
  
     ![シミュレーターの 1 本の指のターゲット](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")シングル ターゲット アイコンは、シミュレーター内のイベントの場所を示します。 ポインターを配置するには、マウスを使用します。  
  
     ![1 本指タッチのターゲット](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")タッチ モードをアクティブにマウスの左ボタンを押します。 たとえば、タップをシミュレートする場合はボタンをクリックし、ドラッグまたはスワイプする場合はボタンを長押しします。  
  
## <a name="pinch-and-zoom"></a>ピンチとズーム  
 対話モードを、2 本の指によるピンチ ジェスチャとズーム ジェスチャに設定します。  
  
-   ![シミュレーターの 2 本指のターゲット](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     ダブル ターゲット アイコンは、デバイス画面上の 2 本の指の位置を示します。  
  
    -   デバイス画面上のオブジェクトの上にアイコンを配置するには、マウスを移動します。  
  
    -   ピンチまたはズームを実行する前の 2 本の指のシミュレートされる距離を変更するは、マウス ホイールを前方または後方に回転させます。  
  
-   -   ![ピンチ、ズーム、およびターゲットを回転](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
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
>  ビットマップ イメージのスケーリングされたバージョンをアプリに保存できます。Windows は、現在のスケールで正しいイメージを読み込みます。 詳細については、次を参照してください。[デザインと UI 出だし](/windows/uwp/layout/design-and-ui-intro)です。 ただし、Windows によって解像度に合ったイメージが選択されるようにシミュレーターの解像度を変更した場合、新しいイメージを表示するにはデバッグ セッションを停止して再度開始する必要があります。  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Microsoft Store に送信するアプリのスクリーン ショットをキャプチャします。  
 Microsoft ストアにアプリを送信するときに、アプリのスクリーン ショットを含める必要があります。  
  
> [!NOTE]
>  スクリーンショットは、シミュレーターの現在の解像度で保存されます。 解像度を変更するには、 **[解像度の変更]** ボタンをクリックします。  
  
-   シミュレーターからアプリのスクリーンショットを作成するには、 **[クリップボードにスクリーンショットをキャプチャします]** ボタンをクリックします。  
  
-   スクリーンショットの配置場所を設定するには、 **[スクリーンショットの設定]** ボタンをクリックし、ショートカット メニューから場所を選択します。  
  
     ![スクリーン ショットの設定のコンテキスト メニュー](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> ネットワーク接続のプロパティをシミュレートする  
 ローミングやを超えるのための追加コストを避けるためにこの情報を使用するアプリを有効にして、ネットワーク接続コストやデータ プランの状態の変更の認識従量制ネットワーク接続のコストを管理、アプリのユーザーを支援することができます、指定したデータ転送の制限。 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) Api に応答できます。 [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation)と[TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger)署名を行うイベント。 「 [従量制課金接続のコスト制約を管理する方法 (HTML)](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)」をご覧ください。  
  
 シミュレーターをデバッグまたはネットワーク コストを認識するコードをテスト、を通じて公開されるネットワークのプロパティを模倣できます、 [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile)によって返されるオブジェクト[GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation)です。
  
 ネットワークのプロパティをシミュレートするには、次のようにします。  
  
1.  シミュレーターのツール バーの **[ネットワーク プロパティの変更]** ボタンをクリックします。  
  
2.  **[ネットワーク プロパティの設定]** ダイアログ ボックスの **[シミュレートされたネットワーク プロパティの使用]**をクリックします。  
  
     チェック ボックスをオフにしてシミュレーションを削除し、現在接続されているインターフェイスのネットワーク プロパティに戻ります。  
  
3.  シミュレートされたネットワークの **[プロファイル名]** を入力します。 シミュレーションを識別するのに使用できる一意の名前を使用することをお勧め、 [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile)のプロパティ、 [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile)オブジェクト。  
  
4.  選択、 [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype)からプロファイルの値、**ネットワーク コストの種類** ボックスの一覧です。  
  
5.  **データの限度の状態フラグ**] ボックスの一覧を設定できます、 [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost)プロパティまたは[OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost)プロパティを true にするか選択できます**データの制限 [**両方の値を false に設定します。  
  
6.  **ローミングの状態**一覧で、設定、[ローミング](/uwp/api/windows.networking.connectivity.connectioncost)プロパティです。  
  
7.  選択**プロパティの設定**、前景をトリガーすることによって、ネットワークのプロパティをシミュレートする[NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation)イベントとバック グラウンド[SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger)型の**NetworkStateChange**です。  
  
 **ネットワーク接続の管理の詳細について**  
  
 [従量制課金接続のコスト制約を管理する方法 (HTML)](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [ネットワーク情報のサンプル](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [エネルギー使用を分析します。](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
 [バックグラウンド タスクでシステム イベントに応答する方法](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [トリガーする方法を中断、再開、およびバック グラウンド イベントを UWP アプリ](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> キーボードを使用してシミュレーター内を移動する  
 キーを押してシミュレーター ツールバー内を移動できます**CTRL + ALT + ↑**シミュレーター ウィンドウからシミュレーター ツールバーにフォーカスを移動します。 ツール バーのボタンの間を移動するには、 **上向きの矢印** と **下向きの矢印** を使用します。  
  
 シミュレーターを終了するには、キーを押して**ctrl キーと alt キーを押しながら F4**です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio からアプリを実行します。](../debugger/run-store-apps-from-visual-studio.md)