---
title: "Sys (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **Sys** オプションは、システム コール イベント \(プロファイリングされたアプリケーションからオペレーティング システムへの関数呼び出し\) でサンプリングされるプロファイリング イベントを設定し、必要に応じて、サンプリング間隔のシステム コール数を既定値の 10 から変更します。  
  
 **Sys** は、**Launch** オプションまたは **Attach** オプションも含むコマンド ラインでのみ使用できます。  
  
 既定では、プロファイラーのサンプリング イベントはプロセッサのクロック サイクルに設定され、サンプリング間隔は 10,000,000 に設定されます。  **Timer**、**PF**、**Sys**、**Counter** の各オプションを使用すると、サンプリング イベントおよびサンプリング間隔を設定できます。  **GC** オプションは、各割り当ての .NET メモリ データおよびガベージ コレクション イベントを収集します。  コマンド ラインでは、これらのオプションのうち 1 つのみを指定できます。  
  
 サンプリング イベントおよびサンプリング間隔は、**Launch** オプションまたは **Attach** オプションを含む最初のコマンド ラインでのみ設定できます。  
  
## 構文  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### パラメーター  
 `Events`  
 サンプリング間隔におけるシステム コール イベント数を指定する整数値。  `Events` を指定しない場合、間隔は 10 に設定されます。  
  
## 必須のオプション  
 **Sys** では、次のオプションのいずれかを指定する必要があります。  
  
 **Launch:** `AppName`  
 プロファイラーと、`AppName` で指定したアプリケーションを起動します。  
  
 **Attach:** `PID`  
 プロファイラーを `PID` で指定されたプロセスにアタッチします。  
  
## 無効なオプション  
 以下のオプションは、コマンド ラインで **Sys** と同時には指定できません。  
  
 **PF**\[**:**`Events`\]  
 サンプリング イベントをページ フォールトに設定し、オプションでサンプリング間隔を `Events` に設定します。  既定の PF 間隔は 10 です。  
  
 **Timer**\[**:**`Cycles`\]  
 サンプリング イベントをプロセッサのクロック サイクルに設定し、オプションでサンプリング間隔を `Cycles` に設定します。  既定の Timer 間隔は 10,000,000 です。  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 サンプリング イベントを `Name` で指定した CPU パフォーマンス カウンターに設定し、サンプリング間隔を `Reload` に設定します。  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 .NET メモリ データを収集します。  既定 \(**Allocation**\) では、データはメモリの割り当てイベントごとに収集されます。  **Lifetime** パラメーターが指定された場合、ガベージ コレクション イベントごとのデータも収集されます。  
  
## 使用例  
 この例では、プロファイラーのサンプリング イベントをシステム コールに設定し、サンプリング間隔をサンプルごとに 20 のコールに設定する方法を示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)