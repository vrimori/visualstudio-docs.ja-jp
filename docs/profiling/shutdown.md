---
title: "Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Shutdown
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Shutdown** オプションは、現在プロファイル中のプロセスが終了するかデタッチされるまで待機して、プロファイラーをオフにし、プロファイル データ ファイルを閉じます。  **Shutdown** オプションは、プロファイリング実行の最後のコマンドとして指定する必要があります。  
  
 タイムアウト パラメーターが指定されていない場合、**Shutdown** オプションは無期限に待機します。  タイムアウト パラメーターが指定されている場合、指定された秒数の経過後に制御が戻りますが、プロファイラーはオフにされず、データ ファイルも閉じられません。  
  
 コマンド ラインで指定するオプションは **Shutdown** オプションのみにする必要があります。  
  
## 構文  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### パラメーター  
 `Timeout`  
 -   \(省略可能\) 指定した場合は、指定した秒数の経過後にオプションから制御が戻りますが、プロファイラーはオフにされず、プロファイル データ ファイルも閉じられません。  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)