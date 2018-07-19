---
title: Visual Studio グラフィックス診断の概要 |Microsoft Docs
ms.custom: ''
ms.date: 05/26/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 069dd7638296987c195fbae6cc9d858fdd3421ee
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058673"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio グラフィックス診断の使用を開始する
このセクションでは、まずグラフィックス診断を初めて使用するための準備をしてから、Direct3D アプリケーションのフレームをキャプチャして Graphics Analyzer でそれらを確認します。  
  
## <a name="requirements"></a>必要条件  
 Visual Studio のグラフィックス診断を使用するには、Visual Studio Enterprise、Visual Studio Professional、または Visual Studio Community を使用する必要があります。  Visual Studio のコードを含む、他のエディションでは、この機能は含まれません。
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Windows の 10 の前提条件  
 省略可能な Windows 機能*グラフィックス ツール*Windows 10 でグラフィックス診断に必要なキャプチャと再生のインフラストラクチャを提供します。  
  
 グラフィックス ツールのインストール方法の詳細については、次を参照してください。[グラフィックス ツールの Windows 10 にインストール](#InstallGraphicsTools)します。  
  
##  <a name="InstallGraphicsTools"></a> Windows 10 用グラフィックス ツールをインストールします。  
 オプションと呼ばれる Windows の機能によって、Windows 10 でグラフィックス診断のインフラストラクチャが提供されている*グラフィックス ツール*します。 この機能は、キャプチャするアプリが以前のバージョンの Windows を対象にしているかどうか、またはどのバージョンの Direct3D を使用しているかに関係なく、Windows 10 でグラフィックス情報をキャプチャおよび再生するために必要です。 グラフィック ツール機能を事前にインストールすることができます。それ以外の場合は、Visual Studio からグラフィックス診断セッションを最初に開始するときに、オンデマンドでインストールされます。  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 用のグラフィック ツールをインストールするには  
  
1.  Search では、次のように入力します。**アプリおよび機能**を開き、**アプリと機能**設定します。
  
3.  右側にある、**アプリと機能**ダイアログ ボックスで、選択**省略可能な機能を管理する**(**アプリと機能**)。

    **省略可能な機能を管理する**ダイアログが表示されます。
  
4.  **省略可能な機能を管理する**ダイアログ ボックスで、選択**機能を追加**します。 インストールできるオプション機能の一覧が表示されます。  
  
5.  選択**グラフィックス ツール**、機能の一覧から選択し、**インストール**します。  
  
 グラフィック ツールの機能は Windows 10 SDK をインストールするときにも、自動的にインストールされます。  
  
> [!TIP]
>  Windows 10 のオプションのグラフィック ツール機能は、軽量のキャプチャと再生機能を提供します-コマンド ライン キャプチャ プログラムなど**dxcap.exe**-サポート、テスト、および診断のシナリオで使用できる。開発者ツールがインストールされていないマシン。 詳細については、次を参照してください。、[コマンド ライン キャプチャ ツール](command-line-capture-tool.md)トピック。  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>グラフィックス診断を初めて使用する  
 これで、必要なものがすべて揃い、グラフィックス診断の使用を開始する準備が整いました。 以下の手順に実行します。  
  
### <a name="1---create-a-direct3d-app"></a>1 -、Direct3D アプリを作成する  
 非常に使用すると、グラフィックス診断を探索する独自の Direct3D アプリが既にあります。 場合、 それ以外の場合、次のいずれかを使用します。

- **DirectX 11 アプリ (ユニバーサル Windows)** または**DirectX 12 アプリ (ユニバーサル Windows)** Windows 10 用のプロジェクト テンプレート。
- [Direct3d12 UAP サンプル](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f)Windows 10 用です。  
  
 先に進む前に、アプリをビルドできるかどうかを確認します。  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2-グラフィックス診断セッションを開始する  
 これで、最初のグラフィックス診断のセッションを開始する準備ができました。 Visual Studio のメイン メニューで、選択**デバッグ、グラフィックス、グラフィックス デバッグの開始**、キーを押すか**alt キーを押しながら f5 キー**します。 これで、グラフィックス診断の下でアプリが開始され、Visual Studio の診断セッションのウィンドウが表示されます。  
  
> [!IMPORTANT]
>  Windows 10 でアプリを実行しており、オプションのグラフィック ツール機能をまだインストールしていない場合は、今すぐインストールするよう求められます。 インストールは、Windows 10 でグラフィックス診断を使用する前に済ませておく必要があります。  
  
### <a name="3---capture-frames"></a>3 - フレームをキャプチャする  
 アプリが起動すると、すぐにフレームをキャプチャできます。  
  
#### <a name="to-capture-single-frames"></a>1 つのフレームをキャプチャするには  
  
-   Visual Studio で、選択、**フレームのキャプチャ**グラフィックス ツールバーまたは診断セッション ウィンドウからボタンをクリックします。 または、アプリにフォーカスがある場合は、キーを押す、 **Print Screen**キーボードのキー。
  
#### <a name="to-capture-a-sequence-of-frames"></a>フレームのシーケンスをキャプチャするには  
  
-   Visual Studio での診断セッション ウィンドウで、設定**キャプチャするフレーム**シーケンスでキャプチャするフレームの数、1 つのフレームをキャプチャするための前述の方法のいずれかを使用して、シーケンスをキャプチャします。  
  
     1 つのフレームをもう一度キャプチャするには、次のように設定します。**キャプチャするフレーム**に*1*します。  
  
 単にフレームのキャプチャが完了したら、アプリを終了するか選択、**停止**[グラフィックス] ツールバーまたは診断セッション ウィンドウからボタンをクリックします。  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4-Graphics Analyzer でキャプチャされたフレームを確認します。  
 これで、キャプチャしたフレームを詳しく調べる準備ができました。 フレーム分析を開始するには、診断セッション ウィンドウから確認するフレームのフレーム番号を選択します。 内のフレームが表示されます、 **Graphics Analyzer**、場所、グラフィックス診断ツールを使用して、アプリが Direct3D を使用して、レンダリングの問題を追跡する方法を確認したり、使用、**フレーム分析**ツールそのパフォーマンスを理解します。  
  
 診断セッション ウィンドウで間違ったフレームを選択した場合や、別のフレームを確認する場合は、Graphics Analyzer から新しいフレームを選択できます。 **レンダー ターゲット**グラフィックス ログ ウィンドウのレンダー ターゲットのイメージの下のタブを展開、**フレーム一覧**を確認する別のフレームを選択します。  
  
 Graphics Analyzer ツールを一緒に使用する方法の詳細については、次を参照してください。、[例](graphics-diagnostics-examples.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Direct3D 12 のグラフィックス](/windows/desktop/direct3d12/direct3d-12-graphics)