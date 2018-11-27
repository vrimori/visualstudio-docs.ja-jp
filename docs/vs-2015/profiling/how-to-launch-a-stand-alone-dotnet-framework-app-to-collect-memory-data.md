---
title: '方法: コマンド ラインを使用してプロファイラーによってスタンドアロンの .NET Framework アプリケーションを起動し、メモリ データを収集する | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 207fc9a02be3557341bfad95d6fd32943557478a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757441"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>方法: コマンド ラインを使用してプロファイラーによってスタンドアロンの .NET Framework アプリケーションを起動し、メモリ データを収集する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ここでは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイリング ツールのコマンド ライン ツールを使用して、.NET Framework のスタンドアロン (クライアント) アプリケーションを起動し、メモリ データを収集する方法について説明します。  

 プロファイル セッションには、3 つの部分があります。  

-   プロファイラーを使用してアプリケーションを起動する。  

-   プロファイル データを収集する。  

-   プロファイル セッションを終了する。  

> [!NOTE]
>  プロファイリング ツールのコマンド ライン ツールは、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] インストール ディレクトリの \Team Tools\Performance Tools サブディレクトリにあります。 64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。 プロファイラー コマンド ライン ツールを使用するには、コマンド プロンプト ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。 詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」をご覧ください。  

## <a name="starting-the-application-with-the-profiler"></a>プロファイラーによるアプリケーションの起動  
 プロファイラーを使用して対象アプリケーションを起動するには、**VSPerfCmd.exe/start** オプションと **/launch** オプションを使用して、プロファイラーを初期化し、アプリケーションを起動します。 **/start** と **/launch**、およびそれぞれのオプションは、1 つのコマンド ラインで指定できます。  

 **/globaloff** オプションを追加して、対象アプリケーションの起動時にデータ収集を一時停止することもできます。 次に、**/globalon** を使用してデータの収集を開始します。  

#### <a name="to-start-an-application-by-using-the-profiler"></a>プロファイラーを使用してアプリケーションを起動するには  

1. コマンド プロンプト ウィンドウを開きます。  

2. プロファイラーを起動します。 型:  

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]  

   - [/start](../profiling/start.md)**:sample** オプションによってプロファイラーが初期化されます。  

   - **/start** を使用するには、[/output](../profiling/output.md)**:**`OutputFile` オプションを指定する必要があります。 `OutputFile` には、プロファイル データ (.vsp) ファイルの名前と場所を指定します。  

     **/start:sample** オプションを使用する場合は、次のうちいずれかのオプションを指定できます。  

   |                              オプション                              |                                                                  説明                                                                  |
   |------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` |                                   プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。                                   |
   |      [/automark](../profiling/automark.md) **:** `Interval`      | **/wincounter** との組み合わせでのみ使用します。 Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。 既定値は 500 ミリ秒です。 |


3. 対象アプリケーションを起動します。 型:  

    **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `appName` **/gc:**{**allocation**&#124;**lifetime**}[`Options`]  

   - [/gc](../profiling/gc-vsperfcmd.md)**:**`Keyword` オプションは、.NET Framework メモリ データを収集するために必要です。 keyword パラメーターは、メモリの割り当てデータを収集するのか、メモリの割り当てデータとオブジェクトの有効期間データの両方を収集するのかを指定します。  

     |キーワード|説明|  
     |-------------|-----------------|  
     |**allocation**|メモリの割り当てデータのみを収集します。|  
     |**lifetime**|.NET メモリの割り当てデータとオブジェクトの有効期間データの両方を収集します。|  

     **/launch** オプションを使用する場合は、次のうちどのオプションでも指定できます。  

   |オプション|説明|  
   |------------|-----------------|  
   |[/args](../profiling/args.md) **:** `Arguments`|対象アプリケーションへ渡されるコマンド ライン引数を格納する文字列を指定します。|  
   |[/console](../profiling/console.md)|対象のコマンド ライン アプリケーションを別のウィンドウで起動でします。|  
   |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|プロファイリング実行中に収集する ETW (Event Tracing for Windows) イベントを指定します。 ETW イベントは独立した (.etl) ファイルに収集されます。|  
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|アプリケーションに複数バージョンのランタイムが読み込まれている場合に、プロファイリングを行う共通言語ランタイム (CLR: Common Language Runtime) のバージョンを指定します。|  

## <a name="controlling-data-collection"></a>データ コレクションの制御  
 対象アプリケーションの実行中に、**VSPerfCmd.exe** のオプションを使用してファイルへのデータ書き込みを開始および停止することにより、データ収集を制御できます。 データ コレクションを制御することにより、アプリケーションの起動や終了など、プログラム実行の特定の部分についてのデータ コレクションを行うことができます。  

#### <a name="to-start-and-stop-data-collection"></a>データ収集を開始および停止するには  

-   次に示すオプションの組み合わせにより、データ収集を開始および停止します。 個別のコマンド ラインで各オプションを指定します。 データ収集のオンとオフは複数回切り替えることができます。  

    |オプション|説明|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 (**/globalon**) または停止 (**/globaloff**) します。|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|プロセス ID (`PID`) で指定されたプロセスのデータ収集を開始 (**/processon**) または停止 (**/processoff**) します。|  
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** は、`PID` (プロセス ID) で指定したプロセスのデータ収集を開始します。 **/detach** は、すべてのプロセスのデータ収集を停止します。|  

-   **VSPerfCmd.exe**[/mark](../profiling/mark.md) オプションを使用して、データ ファイルにプロファイル マークを挿入することもできます。 **/mark** コマンドは、識別子、タイム スタンプ、およびオプションのユーザー定義文字列を追加します。 マークは、データをフィルター処理するために使用できます。  

## <a name="ending-the-profiling-session"></a>プロファイル セッションの終了  
 プロファイル セッションを終了するには、プロファイラーをプロファイリング対象のすべてのプロセスからデタッチし、プロファイラーを明示的に終了する必要があります。 サンプリング メソッドを使用してプロファイリングを実行したアプリケーションからプロファイラーをデタッチするには、アプリケーションを終了するか、**VSPerfCmd /detach** オプションを呼び出します。 次に、**VSPerfCmd /shutdown** オプションを呼び出して、プロファイラーをオフにし、プロファイル データ ファイルを閉じます。 **VSPerfClrEnv /off** コマンドは、プロファイル環境変数を消去します。  

#### <a name="to-end-a-profiling-session"></a>プロファイル セッションを終了するには  

1.  対象アプリケーションからプロファイラーをデタッチするには、次のいずれかの手順を実行します。  

    -   対象アプリケーションを終了します。  

         - または -  

    -   **VSPerfCmd /detach** と入力します  

2.  プロファイラーをシャットダウンします。 型:  

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>関連項目  
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET メモリのデータ ビュー](../profiling/dotnet-memory-data-views.md)



