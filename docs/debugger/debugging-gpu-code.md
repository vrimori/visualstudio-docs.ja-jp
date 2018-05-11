---
title: GPU コードのデバッグ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e423a36fd9477c01354c23f31afd686d79a3ba4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-gpu-code"></a>GPU コードのデバッグ
グラフィックス処理装置 (GPU) で実行されている C++ コードをデバッグできます。 Visual Studio での GPU デバッグのサポートには、競合の検出、プロセスの開始、プロセスへのアタッチ、デバッグ ウィンドウへの統合が含まれます。  
  
## <a name="supported-platforms"></a>サポートされているプラットフォーム  
 デバッグは [!INCLUDE[win7](../debugger/includes/win7_md.md)]、[!INCLUDE[win8](../debugger/includes/win8_md.md)]、[!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]、[!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] でサポートされています。 ソフトウェア エミュレーターでデバッグするには、[!INCLUDE[win8](../debugger/includes/win8_md.md)] または [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] が必要です。 ハードウェアでデバッグするには、使用するグラフィックス カードのドライバーをインストールする必要があります。 ハードウェア ベンダーによってはデバッガーの一部の機能が実装されていない場合があります。 制限については、ベンダーのドキュメントを参照してください。  
  
> [!NOTE]
>  Visual Studio での GPU デバッグをサポートする独立系ハードウェア ベンダーは、VSD3DDebug インターフェイスを実装し、独自のドライバーを対象とする DLL を作成する必要があります。  
  
## <a name="configuring-gpu-debugging"></a>GPU デバッグの構成  
 デバッガーは同じアプリの実行中に CPU コードと GPU コードの両方で中断することはできません。 既定では、デバッガーは CPU コードで中断されます。 GPU コードをデバッグするには、次の 2 つの手順のいずれかを使用します。  
  
-   **デバッグの種類**ボックスの一覧、**標準**ツールバーで、選択**GPU のみ**です。  
  
-   **ソリューション エクスプ ローラー**、プロジェクトのショートカット メニューで選択**プロパティ**です。 **プロパティ ページ**ダイアログ ボックスで、**デバッグ**、し、[ **GPU のみ**で、**デバッガーの種類**] ボックスの一覧です。  
  
## <a name="launching-and-attaching-to-applications"></a>アプリケーションの起動とアプリケーションへのアタッチ  
 Visual Studio のデバッグ コマンドを使用して GPU デバッグを開始および停止できます。 詳細については、「[デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)」を参照してください。 また、実行中のプロセスに GPU デバッガーをアタッチできます。ただし、そのプロセスが GPU コードを実行している場合に限ります。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)です。  
  
## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>[現在の Tile をカーソル行の前まで実行] と [カーソル行の前まで実行]  
 GPU でデバッグするとき、カーソル位置まで実行するには 2 つの選択肢があります。 いずれの選択肢のコマンドもコード エディターのショートカット メニューで使用できます。  
  
1.  **カーソルまで実行**コマンドは、カーソル位置に達すると、それを停止するまでに、アプリを実行します。 これは、現在のスレッドがカーソル位置まで実行されるという意味ではありません。カーソル位置に達した最初のスレッドが中断されるということです。 参照してください[デバッガーでのコードを移動します。](../debugger/navigating-through-code-with-the-debugger.md)  
  
2.  **実行現在の Tile をカーソル**コマンドは、すべて現在の tile 内のスレッドのカーソルしてから中断されるまでに、アプリを実行します。  
  
## <a name="debugging-windows"></a>デバッグ ウィンドウ  
 特定のデバッグ ウィンドウを使用することで、GPU スレッドを調べたり、スレッドにフラグを設定したり、スレッドを凍結したりできます。 詳細については次を参照してください:  
  
-   [[並列スタック] ウィンドウの使用](../debugger/using-the-parallel-stacks-window.md)  
  
-   [[タスク] ウィンドウの使用](../debugger/using-the-tasks-window.md)  
  
-   [方法: 並列ウォッチ ウィンドウを使用する](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [スレッドとプロセスをデバッグ](../debugger/debug-threads-and-processes.md)([デバッグの場所] ツールバー)  
  
-   [方法: GPU スレッド ウィンドウを使用する](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## <a name="data-synchronization-exceptions"></a>データ同期の例外  
 デバッガーは実行中に複数のデータ同期条件を検出できます。 条件を検出すると、デバッガーは中断状態になります。 2 つのオプションがある-**中断**または**続行**です。 使用して、**例外**ダイアログ ボックスで、デバッガーはこれらの条件を検出し、またどの条件で実行を中断するかどうかを構成できます。 詳細については、次を参照してください。[デバッガーでは、例外を管理する](../debugger/managing-exceptions-with-the-debugger.md)です。 使用することも、**オプション** ダイアログ ボックスに書き込まれるデータのデータの値が変更されない場合に、デバッガーが例外を無視するように指定します。 詳細については、次を参照してください。 [[全般]、デバッグ、オプションダイアログ ボックス](../debugger/general-debugging-options-dialog-box.md)です。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
  
### <a name="specifying-an-accelerator"></a>アクセラレータの指定  
 コードが実行されている場合、GPU コード内のブレークポイントがヒットのみ、 [accelerator::direct3d_ref](/cpp/parallel/amp/reference/accelerator-class.md#accelerator__direct3d_ref_Data_Member) (REF) アクセラレータです。 コードでアクセラレータを指定しない場合、REF アクセラレータは自動的に選択、**デバッグ アクセラレータの種類**プロジェクトのプロパティです。 コード内でアクセラレータを明示的に選択している場合、REF アクセラレータはデバッグ中に使用されません。GPU ハードウェアがデバッグをサポートしていない限り、ブレークポイントがヒットすることはありません。 この問題を解決するには、デバッグ中に REF アクセラレータを使用するようにコードを記述します。 詳細については、「プロジェクトのプロパティと[アクセラレータおよび accelerator_view オブジェクトを使用して](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects)と[C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)です。  
  
### <a name="conditional-breakpoints"></a>条件付きブレークポイント  
 GPU コード内の条件付きブレークポイントはサポートされていますが、すべての式をデバイス上で評価できるとは限りません。 式はデバイスで評価できないと、デバッガーで評価されます。 デバッガーでの処理はデバイスでの処理よりも遅くなる可能性があります。  
  
### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>エラー: 選択されたデバッグ アクセラレータの種類には、構成に関する問題があります。  
 プロジェクトの設定とデバッグ中の PC の設定との間に矛盾があると、このエラーが発生します。 詳細については、次を参照してください。 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)です。  
  
### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>エラー: 選択されたデバッグ アクセラレータの種類に対応するデバッグ ドライバーがターゲット コンピューターにインストールされていません。  
 リモート PC でデバッグしている場合に、このエラーが発生します。 デバッガーは、ドライバーがリモート PC にインストールされているかどうかを実行時まで判別できません。 ドライバーはグラフィックス カードの製造元から入手できます。  
  
### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>エラー: リモート サイトでタイムアウト検出と復旧 (TDR) を無効にする必要があります。  
 Windows のタイムアウト検出と復旧 (TDR) で設定されている既定の時間間隔より、C++ AMP の計算が長くかかっている可能性があります。 その場合、計算は取り消され、データは失われます。 詳細については、次を参照してください。 [C++ AMP で処理 TDRs](http://go.microsoft.com/fwlink/p/?LinkId=249154)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: C++ AMP アプリケーションのデバッグ](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Visual Studio での GPU デバッグを開始します。](http://go.microsoft.com/fwlink/p/?LinkId=255381)