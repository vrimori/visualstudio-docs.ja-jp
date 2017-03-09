---
title: "GPU コードのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GPU コードのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

グラフィックス処理装置 \(GPU\) で実行されている C\+\+ コードをデバッグできます。  Visual Studio での GPU デバッグのサポートには、競合の検出、プロセスの開始、プロセスへのアタッチ、デバッグ ウィンドウへの統合が含まれます。  
  
## サポートされているプラットフォーム  
 デバッグは [!INCLUDE[win7](../debugger/includes/win7_md.md)]、[!INCLUDE[win8](../debugger/includes/win8_md.md)]、[!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]、[!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] でサポートされています。  ソフトウェア エミュレーターでデバッグするには、[!INCLUDE[win8](../debugger/includes/win8_md.md)] または [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] が必要です。  ハードウェアでデバッグするには、使用するグラフィックス カードのドライバーをインストールする必要があります。  ハードウェア ベンダーによってはデバッガーの一部の機能が実装されていない場合があります。  制限については、ベンダーのドキュメントを参照してください。  
  
> [!NOTE]
>  Visual Studio での GPU デバッグをサポートする独立系ハードウェア ベンダーは、VSD3DDebug インターフェイスを実装し、独自のドライバーを対象とする DLL を作成する必要があります。  
  
## GPU デバッグの構成  
 デバッガーは同じアプリの実行中に CPU コードと GPU コードの両方で中断することはできません。  既定では、デバッガーは CPU コードで中断されます。  GPU コードをデバッグするには、次の 2 つの手順のいずれかを使用します。  
  
-   **\[標準\]** ツール バーの **\[デバッグの種類\]** ボックスの一覧で **\[GPU のみ\]** を選択します。  
  
-   **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューの **\[プロパティ\]** をクリックします。  **\[プロパティ ページ\]** ダイアログ ボックスで **\[デバッグ\]** をクリックし、**\[デバッガーの種類\]** ボックスの一覧で **\[GPU のみ\]** を選択します。  
  
## アプリケーションの起動とアプリケーションへのアタッチ  
 Visual Studio のデバッグ コマンドを使用して GPU デバッグを開始および停止できます。  詳細については、「[デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)」を参照してください。  また、実行中のプロセスに GPU デバッガーをアタッチできます。ただし、そのプロセスが GPU コードを実行している場合に限ります。  詳細については、「[実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)」を参照してください。  
  
## \[現在の Tile をカーソル行の前まで実行\] と \[カーソル行の前まで実行\]  
 GPU でデバッグするとき、カーソル位置まで実行するには 2 つの選択肢があります。  いずれの選択肢のコマンドもコード エディターのショートカット メニューで使用できます。  
  
1.  **\[カーソル行の前まで実行\]** コマンドは、カーソル位置に達するまでアプリケーションを実行してから中断します。  これは、現在のスレッドがカーソル位置まで実行されるという意味ではありません。カーソル位置に達した最初のスレッドが中断されるということです。  「[デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)」を参照してください。  
  
2.  **\[現在の Tile をカーソル行の前まで実行\]** コマンドは、現在の Tile 内のすべてのスレッドがカーソル位置に達するまでアプリケーションを実行してから中断します。  
  
## デバッグ ウィンドウ  
 特定のデバッグ ウィンドウを使用することで、GPU スレッドを調べたり、スレッドにフラグを設定したり、スレッドを凍結したりできます。  詳細については、次のトピックを参照してください。  
  
-   [\[並列スタック\] ウィンドウの使用](../Topic/Using%20the%20Parallel%20Stacks%20Window.md)  
  
-   [\[タスク\] ウィンドウの使用](../Topic/Using%20the%20Tasks%20Window.md)  
  
-   [方法: 並列ウォッチ ウィンドウを使用する](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [スレッドとプロセスの操作](../debugger/debug-threads-and-processes.md) \(\[デバッグの場所\] ツール バー\)  
  
-   [方法: GPU スレッド ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)  
  
## データ同期の例外  
 デバッガーは実行中に複数のデータ同期条件を検出できます。  条件を検出すると、デバッガーは中断状態になります。  **\[中断\]** または **\[続行\]** の 2 つの選択肢があります。  **\[例外\]** ダイアログ ボックスを使用して、デバッガーがこれらの条件を検出するかどうか、どの条件で実行を中断するかを構成できます。  詳細については、「[デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)」を参照してください。  また、**\[オプション\]** ダイアログ ボックスを使用して、データが書き込まれてもデータの値が変更されない場合にデバッガーが例外を無視するように指定できます。  詳細については、「[\[全般\] \(\[オプション\] ダイアログ ボックス \- \[デバッグ\]\)](../Topic/General,%20Debugging,%20Options%20Dialog%20Box.md)」を参照してください。  
  
## トラブルシューティング  
  
### アクセラレータの指定  
 GPU コード内のブレークポイントがヒットするのは、コードが [accelerator::direct3d\_ref](../Topic/accelerator::direct3d_ref%20Data%20Member.md) \(REF\) アクセラレータで実行されている場合のみです。  コード内でアクセラレータを指定していない場合は、REF アクセラレータがプロジェクトのプロパティの **\[デバッグ アクセラレータの種類\]** で自動的に選択されます。  コード内でアクセラレータを明示的に選択している場合、REF アクセラレータはデバッグ中に使用されません。GPU ハードウェアがデバッグをサポートしていない限り、ブレークポイントがヒットすることはありません。  この問題を解決するには、デバッグ中に REF アクセラレータを使用するようにコードを記述します。  詳細については、プロジェクトのプロパティおよび「[アクセラレータおよび accelerator\_view オブジェクトの使用](/visual-cpp/parallel/amp/using-accelerator-and-accelerator-view-objects)」と「[C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)」を参照してください。  
  
### 条件付きブレークポイント  
 GPU コード内の条件付きブレークポイントはサポートされていますが、すべての式をデバイス上で評価できるとは限りません。  式はデバイスで評価できないと、デバッガーで評価されます。  デバッガーでの処理はデバイスでの処理よりも遅くなる可能性があります。  
  
### エラー: 選択されたデバッグ アクセラレータの種類には、構成に関する問題があります。  
 プロジェクトの設定とデバッグ中の PC の設定との間に矛盾があると、このエラーが発生します。  詳細については、「[C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)」を参照してください。  
  
### エラー: 選択されたデバッグ アクセラレータの種類に対応するデバッグ ドライバーがターゲット コンピューターにインストールされていません。  
 リモート PC でデバッグしている場合に、このエラーが発生します。  デバッガーは、ドライバーがリモート PC にインストールされているかどうかを実行時まで判別できません。  ドライバーはグラフィックス カードの製造元から入手できます。  
  
### エラー: リモート サイトでタイムアウト検出と復旧 \(TDR\) を無効にする必要があります。  
 Windows のタイムアウト検出と復旧 \(TDR\) で設定されている既定の時間間隔より、C\+\+ AMP の計算が長くかかっている可能性があります。  その場合、計算は取り消され、データは失われます。  詳細については、「[Handling TDRs in C\+\+ AMP \(C\+\+ AMP での TDR の処理\)](http://go.microsoft.com/fwlink/p/?LinkId=249154)」を参照してください。  
  
## 参照  
 [チュートリアル : C\+\+ AMP アプリケーションのデバッグ](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)   
 [C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Start GPU Debugging in Visual Studio \(Visual Studio で GPU デバッグを開始する\)](http://go.microsoft.com/fwlink/p/?LinkId=255381)