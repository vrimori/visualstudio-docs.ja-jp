---
title: "ProcessOn と ProcessOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ProcessOn と ProcessOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **ProcessOff** サブコマンドと **ProcessOn** サブコマンドは、コマンド ライン プロファイル セッションの指定されたプロセスのプロファイリングを一時停止および再開するために使用されます。  **ProcessOff** がプロセスのプロファイリングを一時停止し、**ProcessOn** がプロセスのプロファイリングを再開します。  
  
 多くの場合、**ProcessOn** または **ProcessOff** を VSPerfCmd.exe コマンド ラインの唯一のオプションとして指定しますが、これらを **GlobalOn**、**GlobalOff**、**ThreadOn**、および **ThreadOff** の各サブコマンドと組み合わせて使用することもできます。  
  
 **ProcessOn** サブコマンドと **ProcessOff** サブコマンドは、コマンド ライン プロファイル セッションのすべてのプロセスについてのデータ収集を制御する **GlobalOn** サブコマンドおよび **GlobalOff** サブコマンド、並びに指定されたスレッドについてのデータ収集を制御する **ThreadOn** サブコマンドおよび **ThreadOff** サブコマンドと対話します。  
  
 **ProcessOff** サブコマンドおよび **ProcessOn** サブコマンドは、プロファイラーの API 関数によって操作されるプロセスの開始\/停止数にも影響します。  
  
-   **ProcessOff** は、プロセスの開始\/停止数を直ちに 0 に設定して、プロファイリングを一時停止します。  
  
-   **ProcessOn** は、プロセスの開始\/停止数を直ちに 1 に設定して、プロファイリングを再開します。  
  
 詳細については、「[プロファイリング ツールの API](../profiling/profiling-tools-apis.md)」を参照してください。  
  
## 構文  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### パラメーター  
 `PID`  
 開始または停止するプロセスの整数の ID。  プロセス ID は、Windows タスク マネージャーの \[プロセス\] タブに表示されます。  
  
## 必須のサブコマンド  
 なし。  
  
## 有効なサブコマンド  
 **ProcessOn** と **ProcessOff** は、次のサブコマンドを含むコマンド ラインで指定できます。  
  
 **Start:** `Method`  
 コマンド ライン プロファイル セッションを初期化し、指定されたプロファイル方法を設定します。  
  
 **Launch:** `AppName`  
 指定されたアプリケーションを起動し、サンプリング メソッドを使用してプロファイリングを開始します。  
  
 **Attach:** `PID`  
 指定されたプロセスのプロファイリングを開始します。  
  
 **GlobalOff**&#124;**GlobalOn**  
 コマンド ライン プロファイル セッションのすべてのプロセスのプロファイリングを停止または開始します。  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 指定されたスレッドのプロファイリングを停止または開始します \(インストルメンテーション メソッドのみ\)。  
  
## 使用例  
 この例では、**ProcessOff** サブコマンドを使用してアプリケーション起動のプロファイル データを収集します。  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)