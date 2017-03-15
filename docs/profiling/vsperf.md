---
title: "VSPerf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# VSPerf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**VsPerf** のコマンド ライン ツールを使用する:  
  
1.  プロファイルのウィンドウは、Visual Studio がデバイスにインストールされていない場合は、コマンド ラインからアプリケーションを保存します。  
  
2.  サンプリング プロファイル方法を使用してデスクトップ アプリケーション、Windows 8 と Windows Server 2012 アプリケーションのプロファイリングを行います。  
  
 プロファイル オプションに関する詳細については、「[Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 このトピックでは、`vsperf.exe` コマンド ライン ツールで使用できるオプションを示します。  このトピックは、次のセクションで構成されています。  
  
 [Windows ストア アプリケーションのみ](#BKMK_windows_store_apps_only)  
  
 [Windows 8 デスクトップ アプリケーション、および Windows Server 2012 のアプリケーションのみ](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [すべてのアプリケーション](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> Windows ストア アプリケーションのみ  
 これらのオプションは、Windows ストア アプリケーションにのみ適用されます。  
  
|||  
|-|-|  
|**\/app:{AppName}**|スタート メニューから起動したアプリケーションのプロファイラーと待機を開始します。<br /><br /> インストール済みアプリケーションのアプリケーションの名前と PackageFullName を表示するに `vsperf /listapps` を実行します。|  
|**\/package:{PackageFullName}**|スタート メニューから起動したアプリケーションのプロファイラーと待機を開始します。<br /><br /> インストール済みアプリケーションのアプリケーションの名前と PackageFullName を表示するに `vsperf /listapps` を実行します。|  
|**\/js**|JavaScript のアプリケーションのプロファイリングを行うために必要です。<br /><br /> JavaScript のアプリケーションからパフォーマンス データを収集します。<br /><br /> \/package または \/attach でのみ使用します。|  
|**\/noclr**|省略可能。  CLR データは収集しません。<br /><br /> \/package または \/attach でのみ使用します。<br /><br /> 最適化で、マネージ シンボルは解決されません。|  
|**\/listapps**|インストール済みアプリケーションの名前と PackageFullNames を一覧表示します。|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Windows 8 デスクトップ アプリケーション、および Windows Server 2012 のアプリケーションのみ  
 これらのオプションは、Windows ストア アプリケーションでは実行されません。  
  
|||  
|-|-|  
|**\/launch:{Executable}**|開始、指定した実行可能ファイルのプロファイリングを開始します。|  
|**\/args:{ExecutableArguments}**|コマンド ライン引数を **\/launch** ターゲットを渡すように指定します。|  
|**\/console**|新しいコマンド ウィンドウの **\/launch** ターゲットが実行されます。|  
  
##  <a name="BKMK_All_applications"></a> すべてのアプリケーション  
 これらのオプションは、Windows 8 または Windows Server 2012 silent アプリケーションに適用されます。  
  
|||  
|-|-|  
|**\/attach:{PID&#124;ProcessName}\[,PID&#124;ProcessName\]...**|指定されたプロセスのデータが収集されます。<br /><br /> プロセス ID \(PID\) と実行中のなアプリケーションのプロセス名を表示 Use Task マネージャー。|  
|**\/file:{ReportName}**|省略可能。  出力ファイル \(既存のファイルの上書き\) を指定します。<br /><br /> \/package または \/attach でのみ使用します。|  
|**\/pause**|一時停止のデータ コレクション。|  
|**\/resume**|データ収集の再開。|  
|**\/stop**|データ収集を停止し、ターゲット プロセスを終了します。|  
|**\/detach**|データ収集を停止しますが、ターゲット プロセスの実行を続けることができます。|  
|**\/status**|プロファイラーの状態を表示します。|  
  
## 参照  
 [Windows 8 および Windows Server 2012 アプリケーションのプロファイリング](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)