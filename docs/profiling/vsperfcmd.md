---
title: "VSPerfCmd | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンド ライン, ツール"
  - "コマンド ライン ツール, VSPerfCmd ツール"
  - "パフォーマンス ツール, VSPerfCmd ツール"
  - "プロファイル ツール, VSPerfCmd"
  - "VSPerfCmd ツール"
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**VSPerfCmd.exe** ツールは、パフォーマンス データ収集を開始および停止するために使用します。  このツールは、次の構文を使います。  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 **VSPerfCmd.exe** ツールのオプションの説明を次の表に示します。  
  
|オプション|説明|  
|-----------|--------|  
|**U**|リダイレクトされたコンソール出力は Unicode として書き込まれます。  最初に指定する必要があります。|  
|[開始](../profiling/start.md) **:** `mode`|プロファイリング サービスを指定されたモードで開始します。|  
|[Output](../profiling/output.md) **:** `filename`|出力ファイル名を指定します。  **Start** でのみ使用します。|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Windows セッション全体でのプロファイリングを有効にします。  **Start**、 **Attach**、 **or Launch** でのみ使用します。|  
|[User](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|プロファイラー サービスに指定したアカウントでアクセスできるようにします。  **Start** でのみ使用します。|  
|[WaitStart](../profiling/waitstart.md)\[**:**`n`\]|データ コレクション ロガーの初期化が完了するのを待ちます。  `n` を指定した場合、**VSPerfCmd** は最大で `n` 秒間待機します。  `n` を指定しなかった場合、**VSPerfCmd** は無期限に待機します。  これにより、バッチ処理の一部として **VSPerfCmd** を利用することが容易になります。|  
|[Counter](../profiling/counter.md) **:** `cfg`|サンプル プロファイリング方式を使用するときは、CPU カウンターおよびサンプリング間隔として使用するイベントの数を指定します。  サンプリングできるカウンター値は 1 つだけです。<br /><br /> インストルメンテーション プロファイリング方式を使用するときに、各インストルメンテーション ポイントで収集する CPU カウンターを指定します。  **Start:**`Trace`、 **Attach**、または **Launch** でのみ使用します。|  
|[QueryCounters](../profiling/querycounters.md)|現在のコンピューターの有効な CPU カウンターの一覧を表示します。|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|プロファイル マーク データと共に含まれる Windows パフォーマンス カウンター イベントを指定します。  **Start** でのみ使用します。|  
|[AutoMark](../profiling/automark.md) **:** *n*|Windows パフォーマンス カウンター データ コレクション イベント間の時間間隔 \(ミリ秒単位\) を指定します。  **WinCounter** で使用します。|  
|[イベント](../profiling/events-vsperfcmd.md) **:** `option`|指定された ETW \(Event Tracing for Windows\) イベントのコレクションを制御します。  ETW データは、プロファイリング データ \(.vsp\) ファイルではない .itl ファイルに収集されます。|  
|[ステータス](../profiling/status.md)|プロファイラーの状態、現在プロファイリングを行っているプロセスに関する情報、およびプロファイラーを制御する権限を持つアカウントを表示します。|  
|[Shutdown](../profiling/shutdown.md)\[**:**`n`\]|プロファイリング データ ファイルを閉じ、プロファイラーをオフにします。|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|**VSPerfCmd GlobalOff** を呼び出した後に、データ収集を再開します。|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|すべてのデータ収集を停止しますが、プロファイリング セッションは終了しません。|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|**VSPerfCmd ProcessOff** の呼び出しによってプロファイリングが停止された後に、指定されたプロセスに対してデータ収集を再開します。|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|指定されたプロセスのデータ収集を停止します。|  
|[ThreadOn と ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|**VSPerfCmd ThreadOff** の呼び出しによってプロファイリングが停止された後に、指定されたプロセスに対してプロファイリングを再開します。  インストルメンテーショ方式でプロファイリングを行っている場合にのみ **ThreadOn** を使用します。|  
|[ThreadOn と ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|指定されたスレッドのプロファイリングを一時停止します。  インストルメンテーショ方式でプロファイリングを行っている場合にのみ **ThreadOff** を使用します。|  
|[Mark](../profiling/mark.md) **:** *MarkNum*\[**,***MarkText***\]**|プロファイリング データ ファイルに、省略可能なテキストと共にマークを挿入します。|  
  
## サンプリング方式のオプション  
 次のオプションは、サンプリング プロファイリング方式を使用している場合にのみ使用できます。  
  
|オプション|説明|  
|-----------|--------|  
|[Launch](../profiling/launch.md) **:** *Executable*|指定されたアプリケーションを起動し、プロファイリングを開始します。|  
|[Args](../profiling/args.md) **:** *Arguments*|起動したアプリケーションに渡されるコマンド ライン引数を指定します。|  
|[Console](../profiling/console.md)|新しいコマンド プロンプト ウィンドウで指定されたコマンドを開始します。|  
|[Attach](../profiling/attach.md) **:** *PID*\[**,***PID*\]|指定されたプロセスのプロファイリングを開始します。  プロセスは、プロセス ID またはプロセス名で識別できます。|  
|[Detach](../profiling/detach.md)\[**:***PID*\[,*PID*\]\]|指定されたプロセスのプロファイリングを停止します。  プロセスは、プロセス ID またはプロセス名で識別できます。  プロセスを指定しない場合、すべてのプロセスに対してプロファイリングが停止されます。|  
|[GC](../profiling/gc-vsperfcmd.md)\[**:**{**Allocation** `&#124;` **Lifetime**}\]|.NET メモリの割り当ておよびオブジェクトの有効期間データを収集します。  **VSPerfCmd Launch** オプションでのみ使用します。|  
  
### サンプリング間隔オプション  
 次のオプションを使用して、サンプリング間隔の種類と期間を指定します。  既定値は、**Timer** です。  **Counter** オプションを使用して間隔として CPU カウンターを指定することもできます。  これらのオプションは **Launch** またはプロファイリング セッションの最初の **Attach** でのみ指定できます。  
  
|オプション|説明|  
|-----------|--------|  
|[PF](../profiling/pf.md)\[**:***n*\]|n 番目のページ フォールトごとにサンプリングを行います \(既定 \= 10\)。|  
|[Sys](../profiling/sys-vsperfcmd.md)\[**:***n*\]|n 番目のシステム コールごとにサンプリングを行います \(既定 \= 10\)。|  
|[Timer](../profiling/timer.md)\[**:***n*\]|n 番目のプロセッサ サイクルごとにサンプリングを行います \(既定 \= 10000000\)。|  
  
## サービス コンポーネントとカーネル モード デバイスのオプション  
 次の Admin オプションは、プロファイリング サービス コンポーネントまたはカーネル モード デバイス ドライバーの管理に使用できます。  Admin オプションを使用して、プロファイリング権限を設定し、プロファイリングを行ったサービスまたはデバイス ドライバーを制御します。  
  
 Admin オプションは、管理者の資格情報で実行されているコマンド プロンプトで実行する必要があります。  
  
|オプション|説明|  
|-----------|--------|  
|**Admin:Security** \<**ALLOW&#124;DENY**\> *Right*\[ *Right*\] \<*User*&#124;*Group*\>|プロファイリング サービスに対して、指定のユーザー アクセスまたはグループ アクセスを許可または拒否します。<br /><br /> `Right` は、以下の値を取ります。<br /><br /> CrossSession \- セッション間プロファイリングを実行するサービスに対するユーザー アクセスを提供します。<br /><br /> SampleProfiling \- サンプリング プロファイルを有効にするドライバーへのユーザー アクセスを提供します。  トレース プロファイル中の、カーネル転送情報へのアクセスにも使用されます。<br /><br /> FullAccess \- CrossSession ユーザー アクセスと SampleProfiling ユーザー アクセスの両方を提供します。|  
|**Admin:Security, List**|プロファイリング サービスの現在の状態を示し、ユーザーのアクセス権を一覧表示します。|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**\>|プロファイリング サービス コンポーネント \(サービス\) またはカーネル モード デバイス ドライバー \(ドライバー\) の開始、停止、インストール、またはアンインストールを行います。|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>**AutoStart** `` \<**ON**&#124;**OFF**\>|再起動後の、プロファイリング サービス \(サービス\) またはカーネル モード デバイス ドライバー \(ドライバー\) の自動的な開始を有効または無効にします。|  
  
## VSPerfCmd \/Driver  
 **VSPerfCmd \/Driver** オプションは、廃止されましたが、互換性のために残されています。  この機能の代わりに **VsPerfCmd Admin** オプションを使用してください。  
  
## 参照  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)