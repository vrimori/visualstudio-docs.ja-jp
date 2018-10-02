---
title: Visual Studio グラフィックス診断の概要 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08cff13bedd8a53ec5172acd6866a912a38b620c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548219"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio グラフィックス診断の使用を開始する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio グラフィックス診断の概要](https://docs.microsoft.com/visualstudio/debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics)します。  
  
このセクションでは、まずグラフィックス診断を初めて使用するための準備をしてから、Direct3D アプリケーションのフレームをキャプチャして Graphics Analyzer でそれらを確認します。  
  
## <a name="requirements"></a>要件  
 Visual Studio 2015 でグラフィックス診断を使用するには、次のいずれかのエディションが必要です。  
  
-   Visual Studio 2015 Enterprise  
  
-   Visual Studio 2015 Professional  
  
-   Visual Studio 2015 Community  
  
 [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]  
  
### <a name="windows-10-prerequisites"></a>Windows の 10 の前提条件  
 省略可能な Windows 機能*グラフィックス ツール*Windows 10 でグラフィックス診断に必要なキャプチャと再生のインフラストラクチャを提供します。  
  
 グラフィックス ツールのインストール方法の詳細については、次を参照してください。[グラフィックス ツールの Windows 10 にインストール](#InstallGraphicsTools)します。  
  
### <a name="windows-81-prerequisites"></a>Windows 8.1 の前提条件  
 Windows 8.1 の Windows Software Development Kit (SDK) は、Windows 8.1 のグラフィックス診断に必要なキャプチャと再生のインフラストラクチャを提供し、Windows 8.1 と Windows 8 用の開発をサポートします。  
  
 [Windows 8.1 用 Windows ソフトウェア開発キット (SDK) のダウンロードします。](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)  
  
 Windows 8.1 を実行する開発用コンピューターから、Windows 10 を実行しているリモート再生コンピューターを使用するには、開発用コンピューターに Windows 10 SDK をインストールして、再生コンピューターにオプションのグラフィック ツール機能をインストールする必要があります。  
  
##  <a name="InstallGraphicsTools"></a> Windows 10 用グラフィックス ツールをインストールします。  
 オプションと呼ばれる Windows の機能によって、Windows 10 でグラフィックス診断のインフラストラクチャが提供されている*グラフィックス ツール*します。 この機能は、キャプチャするアプリが以前のバージョンの Windows を対象にしているかどうか、またはどのバージョンの Direct3D を使用しているかに関係なく、Windows 10 でグラフィックス情報をキャプチャおよび再生するために必要です。 グラフィック ツール機能を事前にインストールすることができます。それ以外の場合は、Visual Studio からグラフィックス診断セッションを最初に開始するときに、オンデマンドでインストールされます。  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 用のグラフィック ツールをインストールするには  
  
1.  **開始**] メニューの [選択**設定**します。 **設定**ダイアログが表示されます。  
  
2.  **設定**ダイアログ ボックスで、選択**システム**を選択し、**アプリがインストールされている**システム設定の一覧から。  
  
3.  右側にある、**設定**ダイアログ ボックスで、選択**省略可能な機能を管理する****アプリおよび機能がインストールされている**します。 **省略可能な機能を管理する**ダイアログが表示されます。  
  
4.  **省略可能な機能を管理する**ダイアログ ボックスで、選択**機能を追加**します。 インストールできるオプション機能の一覧が表示されます。  
  
5.  選択**グラフィックス ツール**、機能の一覧から選択し、**インストール**します。  
  
 グラフィック ツールの機能は Windows 10 SDK をインストールするときにも、自動的にインストールされます。  
  
> [!TIP]
>  Windows 10 のオプションのグラフィック ツール機能は、軽量のキャプチャと再生機能を提供します-コマンド ライン キャプチャ プログラムなど**dxcap.exe**-サポート、テスト、および診断のシナリオで使用できる。開発者ツールがインストールされていないマシン。 詳細については、次を参照してください。、[コマンド ライン キャプチャ ツール](../debugger/command-line-capture-tool.md)トピック。  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>グラフィックス診断を初めて使用する  
 これで、必要なものがすべて揃い、グラフィックス診断の使用を開始する準備が整いました。 以下の手順に実行します。  
  
### <a name="1---create-a-direct3d-app"></a>1 -、Direct3D アプリを作成する  
 独自の Direct3D アプリが既にある場合は、グラフィックス診断を試すことができます。 そうでない場合は、コード ギャラリーの使用可能な Direct3D サンプルの 1 つを使用できます。  
  
-   Visual Studio 2015 を使用して Windows 10 では、direct3d12 のグラフィックス診断を試すを再試行してください、 [direct3d12 UAP サンプル](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f)Windows 10 用です。  
  
-   グラフィックス診断と direct3d11 を Windows 10 または Windows 8.1 には、使用することができます、 **DirectX アプリ (ユニバーサル Windows)** または**DirectX アプリ (Windows 8.1)** プロジェクト テンプレート。 または、さらに興味深いものに試してみて、 [DirectX marble maze ゲームのサンプル](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)Windows 8.1 用。  
  
 先に進む前に、アプリをビルドできるかどうかを確認します。  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2-グラフィックス診断セッションを開始する  
 これで、最初のグラフィックス診断のセッションを開始する準備ができました。 Visual Studio のメイン メニューで、選択**デバッグ、グラフィックス診断の開始**、キーを押すか**alt キーを押しながら f5 キー**します。 これで、グラフィックス診断の下でアプリが開始され、Visual Studio の診断セッションのウィンドウが表示されます。  
  
> [!IMPORTANT]
>  Windows 10 でアプリを実行しており、オプションのグラフィック ツール機能をまだインストールしていない場合は、今すぐインストールするよう求められます。 インストールは、Windows 10 でグラフィックス診断を使用する前に済ませておく必要があります。  
  
### <a name="3---capture-frames"></a>3 - フレームをキャプチャする  
 アプリが起動すると、すぐにフレームをキャプチャできます。  
  
##### <a name="to-capture-single-frames"></a>1 つのフレームをキャプチャするには  
  
-   Visual Studio で、選択、**フレームのキャプチャ**グラフィックス ツールバーまたは診断セッション ウィンドウからボタンをクリックします。 または、アプリにフォーカスがある場合は、キーを押す**Print Screen**します。  
  
##### <a name="to-capture-a-sequence-of-frames"></a>フレームのシーケンスをキャプチャするには  
  
-   Visual Studio での診断セッション ウィンドウで、設定**キャプチャするフレーム**シーケンスでキャプチャするフレームの数、1 つのフレームをキャプチャするための前述の方法のいずれかを使用して、シーケンスをキャプチャします。  
  
     1 つのフレームをもう一度キャプチャするには、次のように設定します。**キャプチャするフレーム**に`1`します。  
  
 単にフレームのキャプチャが完了したら、アプリを終了するか選択、**停止**[グラフィックス] ツールバーまたは診断セッション ウィンドウからボタンをクリックします。  
  
### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4 – Graphics Analyzer でキャプチャされたフレームを確認する  
 これで、キャプチャしたフレームを詳しく調べる準備ができました。 フレーム分析を開始するには、診断セッション ウィンドウから確認するフレームのフレーム番号を選択します。 内のフレームが表示されます、 **Graphics Analyzer**、場所、グラフィックス診断ツールを使用して、アプリが Direct3D を使用して、レンダリングの問題を追跡する方法を確認したり、使用、**フレーム分析**ツールそのパフォーマンスを理解します。  
  
 診断セッション ウィンドウで間違ったフレームを選択した場合や、別のフレームを確認する場合は、Graphics Analyzer から新しいフレームを選択できます。 **レンダー ターゲット**グラフィックス ログ ウィンドウのレンダー ターゲットのイメージの下のタブを展開、**フレーム一覧**を確認する別のフレームを選択します。  
  
 Graphics Analyzer ツールを一緒に使用する方法の詳細については、次を参照してください。、[例](../debugger/graphics-diagnostics-examples.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Direct3D 12 のグラフィックス](http://msdn.microsoft.com/en-us/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)






