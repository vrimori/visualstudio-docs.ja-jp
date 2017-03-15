---
title: "ThreadOn と ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ThreadOn と ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **ThreadOff** および **ThreadOn** のサブコマンドは、インストルメンテーション メソッドを使用するコマンド ライン プロファイリング セッションでのみ使用できます。  **ThreadOff** と **ThreadOn** は、指定されたスレッドのプロファイリングを一時停止および再開します。  **ThreadOff** がスレッドのプロファイリングを一時停止し、**ThreadOn** がスレッドのプロファイリングを再開します。  
  
 多くの場合、**ThreadOn** または **ThreadOff** を VSPerfCmd.exe コマンド ラインの唯一のオプションとして指定しますが、**GlobalOn**、**GlobalOff**、**ProcessOn**、**ProcessOff** の各サブコマンドと組み合わせて使用することもできます。  
  
 **ThreadOn** サブコマンドと **ThreadOff** サブコマンドは、コマンド ライン プロファイリング セッションのすべてのプロセスについてのデータ収集を制御する **GlobalOn** サブコマンドおよび **GlobalOff** サブコマンド、並びに指定されたプロセスについてのデータ収集を制御する **ProcessOn** サブコマンドおよび **ProcessOff** サブコマンドと対話します。  
  
 **ThreadOff** サブコマンドおよび **ThreadOn** サブコマンドは、プロファイラーの API 関数によって操作されるスレッドの開始\/停止数にも影響します。  
  
-   **ThreadOff** は、スレッドの開始\/停止数を直ちに 0 に設定して、プロファイリングを一時停止します。  
  
-   **ThreadOn** は、スレッドの開始\/停止数を直ちに 1 に設定して、プロファイリングを再開します。  
  
 詳細については、「[プロファイリング ツールの API](../profiling/profiling-tools-apis.md)」を参照してください。  
  
## 構文  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### パラメーター  
 `TID`  
 開始または停止するスレッドの整数の識別子  
  
## 有効なオプション  
 **ThreadOn** と **ThreadOff** は、次のサブコマンドを含むコマンド ラインで指定できます。  
  
 **Start:** `Method`  
 コマンド ライン プロファイル セッションを初期化し、指定されたプロファイル方法を設定します。  
  
 **GlobalOff**&#124;**GlobalOn**  
 コマンド ライン プロファイル セッションのすべてのプロセスのプロファイリングを停止または開始します。  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 指定されたプロセスのプロファイリングを停止または開始します。  
  
## 使用例  
 アプリケーションのスタートアップ データのみが収集されるように、**ThreadOff** サブコマンドを使用してプロファイル データの収集を停止する例を以下に示します。  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)