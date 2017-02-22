---
title: "PF | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# PF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **PF** オプションは、ページ フォールトでサンプリングされるプロファイル イベントを設定し、オプションで、サンプリング間隔のページ フォールト数を既定の 10 から変更します。  
  
> [!NOTE]
>  PF を 64 ビット システムで使用することはできません。  
  
 **メモ**  
 **PF** は 64 ビット コンピューターではサポートされていません。**PF** は、**Launch** オプションまたは **Attach** オプションを含むコマンド ラインでのみ使用できます。  
  
 既定では、サンプリング イベントはプロセッサのクロック サイクル数 \(停止なし\) に設定され、サンプリング間隔は 10,000,000 に設定されます。  **Timer**、**PF**、**Sys**、**Counter** の各オプションを使用すると、サンプリング イベントおよびサンプリング間隔を設定できます。  **GC** オプションは、各割り当ての .NET メモリ データおよびガベージ コレクション イベントを収集します。  コマンド ラインでは、これらのオプションのうち 1 つのみを指定できます。  
  
 サンプリング イベントおよびサンプリング間隔は、**Launch** オプションまたは **Attach** オプションを含む最初のコマンド ラインでのみ設定できます。  
  
## 構文  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### パラメーター  
 `Events`  
 サンプリング間隔におけるページ フォールト数を指定する整数値。  `Events` を指定しない場合、間隔は 10 に設定されます。  
  
## 必須のオプション  
 **PF** は次のオプションのうちのいずれか 1 つを含むコマンド ラインでのみ指定できます。  
  
 **Launch:** `AppName`  
 プロファイラーと、AppName で指定したアプリケーションを起動します。  
  
 **Attach:** `PID`  
 プロファイラーを AppName で指定されたプロセスにアタッチします。  
  
## 無効なオプション  
 以下のオプションは、コマンド ラインで **PF** と同時には指定できません。  
  
 **Timer**\[**:**`Cycles`\]  
 サンプリング イベントをプロセッサのクロック サイクルに設定し、オプションでサンプリング間隔を `Cycles` に設定します。  既定の Timer 間隔は 10,000,000 です。  
  
 **Sys**\[**:**`Events`\]  
 サンプリング イベントを、プロファイリングされたアプリケーションからオペレーティング システムのカーネル \(syscalls\) への呼び出しに設定し、オプションでサンプリング間隔を `Events` に設定します。  既定の Sys 間隔は 10 です。  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 サンプリング イベントを `Name` で指定した CPU パフォーマンス カウンターに設定し、サンプリング間隔を `Reload` に設定します。  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 .NET メモリ データを収集します。  既定 \(**Allocation**\) では、データはメモリの割り当てイベントごとに収集されます。  **Lifetime** パラメーターが指定された場合、ガベージ コレクション イベントごとのデータも収集されます。  
  
## 使用例  
 この例では、プロファイリング サンプル イベントをページ フォールトに設定し、サンプリング間隔を 20 のページ フォールトに設定する方法を示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)