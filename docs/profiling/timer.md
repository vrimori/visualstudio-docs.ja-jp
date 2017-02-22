---
title: "Timer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Timer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Timer** オプションは、サンプリングするプロファイリング イベントをプロセッサのクロック サイクルに設定します。また、オプションで、サンプリング間隔のサイクル数を既定の 10,000,000 から変更します。  1 GHz のプロセッサでは、クロック サイクル数 10,000,000 の場合、1 秒あたりのサンプル数は約 100 になります。  指定できる最小サイクル数は、50,000 です。  
  
 **Timer** を使用できるのは、サンプリング プロファイリング メソッドを使用する場合のみです。この場合、**Launch** または **Attach** オプションも指定したコマンド ラインでのみ使用できます。  
  
 既定では、プロファイラーのサンプリング イベントは、プロセッサのクロック サイクルに設定され、サンプリング間隔は 10,000,000 に設定されます。  **Timer**、**PF**、**Sys**、および **Counter** オプションを使用すると、サンプリング イベントおよびサンプリング間隔を設定できます。  **GC** オプションは、割り当ておよびガベージ コレクション イベントが発生するたびに、.NET メモリ データを収集します。  コマンド ラインには、上記のオプションのいずれか 1 つだけを指定できます。  
  
 サンプリング イベントとサンプリング間隔を設定できるのは、**Launch** または **Attach** オプションを指定した最初のコマンド ラインのみです。  
  
## 構文  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### パラメーター  
 `Cycles`  
 サンプリング間隔でのプロセッサのクロック サイクル数を指定する整数の値。  ‎`Cycles` が指定されていない場合、間隔は 10,000,000 に設定されます。  コンマを含めずに値を指定してください。  
  
## 必須オプション  
 **Timer** を指定できるのは、以下のいずれかのオプションを指定したコマンド ラインのみです。  
  
 **Launch:** `AppName`  
 プロファイラーと、`AppName` で指定されたアプリケーションを起動します。  
  
 **Attach:** `PID`  
 プロファイラーをプロセス ID \(`PID`\) で指定されたプロセスにアタッチします。  
  
## 無効なオプション  
 以下のオプションを同じコマンド ラインに **Timer** として指定することはできません。  
  
 **PF**\[**:**`Events`\]  
 サンプリング イベントをページ フォールトに設定します。オプションで、サンプリング間隔を `Events` に設定します。  既定の PF 間隔は 10 です。  
  
 **Sys**\[**:**`Events`\]  
 サンプリング イベントをオペレーティング システムの呼び出しに設定します。オプションで、サンプリング間隔を `Events` に設定します。  既定の Sys 間隔は 10 です。  
  
 **Counter**\[**:**`Name,Reload,FriendlyName`\]  
 サンプリング イベントを、`Name` で指定された CPU パフォーマンス カウンターに設定し、サプリング間隔を `Reload` に設定します。  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 .NET メモリ データを収集します。  既定 \(**Allocation**\) では、データはメモリ割り当てイベントで収集されます。  **Lifetime** パラメータが指定されている場合、各ガーベッジ コレクション イベントでも、データが収集されます。  
  
## 使用例  
 プロファイラーのサンプリング間隔をプロセッサ サイクル数 1,000,000 に設定する方法を次の例に示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)