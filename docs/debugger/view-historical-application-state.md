---
title: IntelliTrace を使用して以前のアプリケーション状態を表示します。
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d43e1a04570d68ce69f283cde264280fc24865a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846864"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>Visual Studio の IntelliTrace ステップ バックを使用して前のアプリ状態を調べる

IntelliTrace ステップ バックでは、ステップ イベント、アプリケーションのすべてのブレークポイントとデバッガーのスナップショットが自動的に取得します。 記録されたスナップショットにより、前のブレークポイントまたはステップに戻り、過去の時点でのアプリケーションの状態を確認できるようになります。 IntelliTrace ステップ バックでは、以前のアプリケーションの状態を確認したいが、デバッグの再開や必要なアプリ状態の再作成は必要でない場合に時間を節約できます。

IntelliTrace ステップ バックでは、Visual Studio Enterprise 2017 バージョン 15.5 以降から使用できます。 また必要が Windows 10 Anniversary Update 以降。 ASP.NET、WinForms、WPF、マネージ コンソール アプリ、およびマネージ クラス ライブラリのデバッグ機能がサポートされている現在。 Visual Studio 2017 Enterprise バージョン 15.7 以降、ASP.NET Core と .NET Core の機能はサポートも。 以降では、Visual Studio 2017 Enterprise バージョン 15.9 Preview 2 では、この機能も Windows を対象とするネイティブ アプリのサポートします。 UWP アプリケーションのデバッグは現在サポートされていません。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * Intellitrace イベントとスナップショットを有効にします。
> * ステップ バックとステップ転送のコマンドを使用してイベントを移動します。
> * イベントのスナップショットの表示
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace イベントとスナップショット モードを有効にします。 

1. Visual Studio Enterprise では、プロジェクトを開きます。

1. 開いている**ツール** > **オプション** > **IntelliTrace** 、オプションを選択し、設定**IntelliTrace イベントとスナップショット**. 

    Preview 2 では、このオプションは、以降では、Visual Studio 2017 Enterprise バージョン 15.9 **IntelliTrace スナップショット (マネージとネイティブ)** します。 

    ![IntelliTrace イベントとスナップショット モードを有効にする](../debugger/media/intellitrace-enable-snapshots.png "を有効にする IntelliTrace イベントとスナップショット モード")

1. 例外で表示するスナップショットのオプションを構成する場合は、選択**IntelliTrace** > **詳細**から、**オプション** ダイアログ ボックス。

    これらのオプションは、Visual Studio 2017 enterprise バージョン 15.7 以降使用できます。

    ![例外のスナップショットの動作を構成します。](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    イベントとスナップショットを有効にすると例外でのスナップショットの取得も既定で有効にします。 選択を解除して例外のスナップショットを無効にできます**例外イベントでスナップショットを収集**します。 この機能を有効にすると、未処理の例外のスナップショットが取得されます。 処理済み例外の例外がスローされた場合にのみ、以前にスローされる例外の再スローがない場合にスナップショットが作成します。 例外のスナップショットの最大数を設定するには、ドロップダウン リストから値を選択します。 アプリが (ときに、アプリでは、ブレークポイントがヒット) など、中断モードになることになるたびに、最大値が適用されます。

    > [!NOTE]
    > スナップショットは、IntelliTrace で記録する例外イベントの場合のみ表示されます。 マネージ コードは、どのようなイベントを IntelliTrace で記録を選択して指定できます**ツール** > **オプション** > **IntelliTrace イベント**します。

1. プロジェクトで、1 つまたは複数のブレークポイントを設定し、デバッグを開始 (キーを押して**f5 キーを押して**)、コードをステップ実行してデバッグを開始または (**F10**または**F11**)。

    IntelliTrace は、各デバッガー ステップ、ブレークポイント イベント、および未処理の例外イベントに、アプリケーションのプロセスのスナップショットを取得します。 これらのイベントに記録されます、**イベント** タブで、**診断ツール**ウィンドウで、その他の IntelliTrace イベントと共にします。 このウィンドウを開くには、次のように選択します。**デバッグ** > **Windows** > **診断ツールの表示**します。

    スナップショットが使用可能なイベントの横にあるカメラ アイコンが表示されます。 

    ![イベントがスナップショットを使用したタブ](../debugger/media/intellitrace-events-tab-with-snapshots.png "ブレークポイントやステップ実行のスナップショットを使用したイベント タブ")

    パフォーマンス上の理由から、非常に高速にステップするときに、スナップショットは取得されません。 ステップの横にあるカメラ アイコンが表示されない場合より緩やかに変化をステップ実行してみてください。

## <a name="navigate-and-view-snapshots"></a>移動し、スナップショットの表示

1. 使用してイベント間を移動、**戻る (Alt + [)** と**進む (Alt +])** デバッグ ツールバーのボタン。

    これらのボタンに表示されるイベントの移動、**イベント** タブで、**診断ツール ウィンドウ**します。 イベントに戻るまたは進むを自動的にステップをアクティブに[デバッグ履歴](../debugger/historical-debugging.md)で選択したイベント。

    ![戻るボタンと進むボタン](../debugger/media/intellitrace-step-back-icons-description.png "戻る、進むボタン")

    元に戻してまたはステップ前進するときに Visual Studio はデバッグ履歴モードになります。 このモードでは、デバッガーのコンテキストは、選択したイベントが記録された時刻に切り替わります。 Visual Studio は、ソース ウィンドウ内のコードの対応する行にも、ポインターを移動します。 

    このビューから、内の値を検査することができます、**呼び出し履歴**、**ローカル**、 **[自動変数]**、および**ウォッチ**windows。 データヒントを表示し、式の評価でを実行する変数もポイントすることができます、**イミディ エイト**ウィンドウ。 表示されるデータはその時点で作成されたアプリケーションのプロセスのスナップショットです。

    そのため、たとえば、ブレークポイントにヒットし、手順を実行した場合 (**F10**)、**戻る** で、ブレークポイントに対応するコードの行で履歴モードで Visual Studio に配置します。 

    ![スナップショットを使用してイベントをライセンス認証の履歴モード](../debugger/media/intellitrace-historical-mode-with-snapshot.png "ライセンス履歴スナップショットを使用してイベント モード")

2. ライブ実行に戻り、次のように選択します。**続行 (F5)**  をクリックまたは、**ライブ デバッグに戻って**情報バーにリンクします。 

3. スナップショットを表示することも、**イベント**タブ。これを行うには、スナップショットを使用してイベントを選択し、をクリックして**履歴デバッグの有効化**します。

    ![デバッグ履歴をアクティブ化イベントを](../debugger/media/intellitrace-activate-historical-debugging.png "イベント履歴デバッグの有効化")

    異なり、**次のステートメントの設定**スナップショットを表示するコマンドは、コードを再実行されない; にビューを提供する静的アプリケーションの状態の時点で時間が過去に発生したことにします。

    ![IntelliTrace ステップ バックの概要](../debugger/media/intellitrace-step-back-overview.png "概要の IntelliTrace ステップ バック")

    Visual Studio での変数を検査する方法の詳細については、次を参照してください[デバッガー機能ツアー。](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>よく寄せられる質問

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>IntelliTrace ステップ バックが IntelliTrace イベントのみのモードからさまざまな方法

IntelliTrace イベントのみのモードでは、デバッガーのステップとブレークポイントでデバッグ履歴をアクティブ化することは許可します。 ただし、IntelliTrace は、内のデータのみをキャプチャ、**ローカル**と **[自動変数]** ウィンドウが開いて、および拡張データのみをキャプチャする場合に、windows と表示します。 イベントのみのモードで多くの場合がありません、変数と複雑なオブジェクトの完全なビュー。 さらに、式の評価とデータの表示で、**ウォッチ**ウィンドウがサポートされていません。 

イベントとスナップショット モードでは、IntelliTrace は、複雑なオブジェクトを含む、アプリケーションのプロセスの全体のスナップショットをキャプチャします。 コードの行をブレークポイントで停止された (および情報を展開していたかどうかは関係ありません) かのように、同じ情報を確認できます。 式の評価には、スナップショットを表示するときにもサポートされます。  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>この機能のパフォーマンスに与える影響とは何ですか。 

ステップ実行の全体的なパフォーマンスに対する影響は、アプリケーションによって異なります。 スナップショットにかかるオーバーヘッドは、約 30 ミリ秒です。 スナップショットを取得するとアプリのプロセスがフォーク、フォークしたコピーが中断されます。 スナップショットを表示するときに Visual Studio は、プロセスのフォークしたコピーをアタッチします。 各スナップショットについては、Visual Studio は、ページのテーブルのみをコピーし、ページをコピー オン ライトに設定します。 関連付けられているスナップショット デバッガーのステップの間でヒープのオブジェクトを変更する場合、それぞれのページ テーブルは、コピーされ、最小限のメモリ コスト。 Visual Studio では、スナップショットを取得するための十分なメモリはいないことが検出された場合に、なりません 1 つ。
 
## <a name="known-issues"></a>既知の問題  
* Windows 10 Fall Creators Update (RS3) よりも古い Windows のバージョンの IntelliTrace イベントとスナップショット モードを使用している場合、およびアプリケーションのデバッグ プラットフォーム ターゲットを x86 に設定されている場合は、IntelliTrace はスナップショットを取得しません。

    回避策:
  * お客様が Windows 10 Anniversary Update (RS1) にあり、10.0.14393.2273、バージョンを下回る場合[インストール KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720)します。 
  * お客様が Windows 10 Creators Update (RS2) にあり、10.0.15063.1112、バージョンを下回る場合[インストール KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722)します。
  * インストールまたは Windows 10 Fall Creators Update (RS3) にアップグレードします。 
  * 別の方法として。 
    1. Visual Studio インストーラーからデスクトップ (x86、x64) コンポーネント用の VC++ 2015.3 v140 ツールセットをインストールします。
    2. 対象アプリケーションをビルドします。
    3. 、コマンドラインから editbin ツールを使用して設定を、`Largeaddressaware`実行可能ファイルのターゲットのフラグ。 たとえば、このコマンドを使用して (パスを更新するには) した後可能性があります:"C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe"/Largeaddressaware"C:\Path\To\Application\app.exe"。
    4. デバッグを開始するには、**F5** キーを押します。 ここで、デバッガーのステップとブレークポイントでスナップショットが作成します。

       > [!Note]
       > `Largeaddressaware`実行可能ファイルが変更を再構築するたびにフラグを設定する必要があります。

* アプリケーションのプロセスのスナップショットは、永続化メモリ マップト ファイルを使用するアプリケーションを実行した、ときに、スナップショットを使用して、プロセスは (親プロセスには、そのロックがリリースされました) の後も、メモリ マップト ファイルに排他的ロックを保持します。 他のプロセスは、まだただし、読み取るだけで、メモリ マップト ファイルに書き込まれません。

    回避策:
    * すべてのスナップショットをオフするには、デバッグ セッションを終了します。 

* あるプロセスが多数のアプリケーションでは、Dll の数が多いなどの一意のメモリ領域、アプリケーションをデバッグするときにスナップショットが有効になっているとパフォーマンスをステップ実行受ける可能性があります。 この問題は、Windows の将来のバージョンで対処されます。 この問題が発生する場合をお送りいただくご連絡stepback@microsoft.comします。 

* ファイルを保存するときに**デバッグ > IntelliTrace > の保存の IntelliTrace セッション**イベントとスナップショット モードの場合、追加のスナップショットからキャプチャされたデータは .itrace ファイルにします。 ブレークポイントとステップのイベントには、IntelliTrace イベントのみのモードでファイルを保存してある場合と同じ情報が表示されます。 

## <a name="next-steps"></a>次の手順

このチュートリアルでは、IntelliTrace ステップ バックを使用する方法を学習できました。 詳細については、その他の IntelliTrace の機能はたい場合があります。

> [!div class="nextstepaction"]
> [IntelliTrace の機能](../debugger/intellitrace-features.md)
