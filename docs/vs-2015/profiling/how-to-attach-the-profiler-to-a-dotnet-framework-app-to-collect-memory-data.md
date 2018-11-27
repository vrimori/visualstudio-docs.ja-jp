---
title: '方法: コマンド ラインを使用してプロファイラーをスタンドアロンの .NET Framework アプリケーションにアタッチし、メモリ データを収集する | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de9753b1471cfe90259ab552b38239a2d92a3c67
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766954"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>方法: コマンド ラインを使用してプロファイラーをスタンドアロンの .NET Framework アプリケーションにアタッチし、メモリ データを収集する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックでは、[!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] プロファイル ツールのコマンド ライン ツールを使用して、実行中の .NET Framework のスタンドアロン (クライアント) アプリケーションにプロファイラーをアタッチし、メモリ データを収集する方法について説明します。  

> [!NOTE]
>  プロファイリング ツールのコマンド ライン ツールは、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] インストール ディレクトリの \Team Tools\Performance Tools サブディレクトリにあります。 64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。 プロファイラー コマンド ライン ツールを使用するには、コマンド プロンプト ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。 詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」をご覧ください。  

 .NET Framework アプリケーションにアタッチしてメモリ データを収集するには、対象アプリケーションを起動する前に、[VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) ツールを使用して該当する環境変数を初期化する必要があります。 プロファイラーがアプリケーションにアタッチされている場合は、**VSPerfCmd.exe** ツールを使用してデータ コレクションを一時停止して再開できます。  

 プロファイル セッションを終了するには、プロファイラーをプロファイリング対象のすべてのプロセスからデタッチし、プロファイラーを明示的に終了する必要があります。 ほとんどの場合、セッションの最後にプロファイル環境変数を消去することをお勧めします。  

## <a name="attaching-the-profiler"></a>プロファイラーのアタッチ  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>実行中の .NET Framework アプリケーションにプロファイラーをアタッチするには  

1. コマンド プロンプト ウィンドウを開きます。  

2. プロファイル環境変数を初期化します。 型:  

    **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} **[/samplelineoff]**  

   -   **/samplegc** オプションと **/samplegclife** オプションは、メモリの割り当てデータのみを収集するか、メモリの割り当てデータとオブジェクトの有効期間データの両方を収集するかを指定します。 1 つのオプションのみを指定する必要があります。  

       |オプション|説明|  
       |------------|------------------|  
       |**/samplegc**|メモリの割り当てデータのみを収集します。|  
       |**/samplegclife**|.NET メモリの割り当てデータとオブジェクトの有効期間データの両方を収集します。|  

   -   **/samplelineoff** オプションを指定すると、ソース コードの行番号データの収集が無効になります。  

3. プロファイラーを起動します。 型:  

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]  

   - [/start](../profiling/start.md)**:sample** オプションによってプロファイラーが初期化されます。  

   - **/start** を使用するには、[/output](../profiling/output.md)**:**`OutputFile` オプションを指定する必要があります。 `OutputFile` には、プロファイル データ (.vsp) ファイルの名前と場所を指定します。  

     **/start:sample** オプションを使用する場合は、次のうちいずれかのオプションを指定できます。  

   |                                 オプション                                  |                                                                                                                                                説明                                                                                                                                                 |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |            プロファイリングされたプロセスを所有するアカウントのドメインおよびユーザー名を指定します。 このオプションは、ログオンしているユーザーとは別のユーザーがプロセスを実行している場合にのみ指定する必要があります。 プロセスの所有者は、Windows タスク マネージャーの [プロセス] タブの [ユーザー名] 列に表示されます。             |
   |        [/crosssession &#124; /cs](../profiling/crosssession.md)         | 他のセッションにおけるプロセスのプロファイリングを有効にします。 このオプションは、アプリケーションが別のセッションで実行されている場合に必要です。 セッション ID は、Windows タスク マネージャーの [プロセス] タブの [セッション ID] 列に表示されます。 **/crosssession** の省略形として、**/CS** を指定することができます。 |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                 プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。                                                                                                                  |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                               **/wincounter** との組み合わせでのみ使用します。 Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。 既定値は 500 ミリ秒です。                                                                                |


4. 必要な場合、通常の方法で対象のアプリケーションを起動します。  

5. プロファイラーを対象のアプリケーションにアタッチします。 型:  

    **VSPerfCmd**  [/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  

   -   `PID` には、対象アプリケーションのプロセス ID を指定します。 `ProcessName` には、プロセスの名前を指定します。 `ProcessName` を指定して、同じ名前の複数のプロセスが実行中である場合、結果は予測できません。 Windows タスク マネージャーで、実行中のすべてのプロセスのプロセス ID を参照できます。  

   -   **/targetclr:** `Version` には、アプリケーションに複数のバージョンのランタイムが読み込まれている場合に、プロファイリングを行う共通言語ランタイム (CLR) のバージョンを指定します。 任意。  

## <a name="controlling-data-collection"></a>データ コレクションの制御  
 対象アプリケーションの実行中に、**VSPerfCmd.exe** のオプションを使用してファイルへのデータ書き込みを開始および停止することにより、データ収集を制御できます。 データ コレクションを制御することにより、アプリケーションの起動や終了など、プログラム実行の特定の部分についてのデータ コレクションを行うことができます。  

#### <a name="to-start-and-stop-data-collection"></a>データ収集を開始および停止するには  

-   次に示すオプションの組み合わせにより、データ収集を開始および停止します。 個別のコマンド ラインで各オプションを指定します。 データ収集のオンとオフは複数回切り替えることができます。  

    |オプション|説明|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 (**/globalon**) または停止 (**/globaloff**) します。|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|`PID` で指定されたプロセスのデータ収集を開始 (**/processon**) または停止 (**/processoff**) します。|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** は、`PID` またはプロセス名 (ProcName) で指定したプロセスのデータ収集を開始します。 **/detach** は、指定されたプロセスのデータ収集を停止します。特定のプロセスが指定されていない場合は、すべてのプロセスのデータ収集を停止します。|  

## <a name="ending-the-profiling-session"></a>プロファイル セッションの終了  
 プロファイル セッションを終了するには、プロファイラーをプロファイリング対象のすべてのプロセスからデタッチし、プロファイラーを明示的に終了する必要があります。 サンプリング メソッドを使用してプロファイリングを実行したアプリケーションからプロファイラーをデタッチするには、アプリケーションを終了するか、**VSPerfCmd /detach** オプションを呼び出します。 次に、**VSPerfCmd /shutdown** オプションを呼び出して、プロファイラーをオフにし、プロファイル データ ファイルを閉じます。 **VSPerfClrEnv /off** コマンドは、プロファイル環境変数を消去します。  

#### <a name="to-end-a-profiling-session"></a>プロファイル セッションを終了するには  

1.  対象アプリケーションからプロファイラーをデタッチするには、次のいずれかの手順を実行します。  

    -   **VSPerfCmd /detach** と入力します  

         - または -  

    -   対象アプリケーションを終了します。  

2.  プロファイラーをシャットダウンします。 型:  

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  

3.  (省略可能) プロファイル環境変数を削除します。 型:  

     **VSPerfCmd /off**  

## <a name="see-also"></a>関連項目  
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET メモリのデータ ビュー](../profiling/dotnet-memory-data-views.md)



