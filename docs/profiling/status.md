---
title: "ステータス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# ステータス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **Status** オプションを使用すると、プロファイラーの状態、および現在プロファイルを実行中の任意のプロセスに関する情報が表示されます。  
  
 コマンド ラインで指定するオプションは **Status** のみにする必要があります。  状態を表示するには、VSPerfCmd.exe の **Start** オプションを使用してプロファイラーを初期化しておく必要があります。  
  
## 構文  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### パラメーター  
 なし。  
  
## 解説  
 **Status** オプションを使用すると、プロファイラーに関して、次の状態情報が表示されます。  
  
 **Output File Name**  
 現在のプロファイラー データ ファイルのパスとファイル名。  
  
 **Collection Mode**  
 SAMPLE または TRACE。  
  
 **Maximum Processes**  
 同時にプロファイルできる最大プロセス数と、現在アクティブなプロセス数。  
  
 **Maximum Threads**  
 同時にプロファイルできる最大スレッド数。  
  
 **Number of Buffers**  
 プロファイル データの書き込み専用のメモリ バッファー数。  
  
 **Size of Buffers**  
 メモリ バッファーのサイズ \(バイト単位\)。  
  
 **Status** オプションを使用すると、現在プロファイルされている各プロセスに関して、次の状態情報が表示されます。  
  
 **Process**  
 プロファイルされているプロセスの名前。  
  
 **Process ID**  
 プロセスのシステム ID。  
  
 **Num Threads**  
 現在実行中のスレッド数。  
  
 **Start\/Stop Count**  
 このプロセスに対するデータ収集を制御するプライマリ内部プロファイラー カウント。  データを収集するには、このカウントが 1 である必要があります。  開始\/停止数は、プロファイラー API、および VSPerfCmd オプションである **GlobalOn**、**GlobalOff**、**ProcessOn**、**ProcessOff**、**ThreadOn**、および **ThreadOff** によって操作できます。  
  
 **Suspend\/Resume Count**  
 このプロセスに対するデータ収集を制御するセカンダリ内部プロファイラー カウント。  データを収集するには、このカウントが 0 以下である必要があります。  **Suspend\/Resume**数は、プロファイラー API によってのみ操作できます。  
  
 **Users with access rights to monitor**  
 プロファイラーにアクセスできるユーザーの名前を一覧表示します。  VSPerfCmd.exe の **Admin** オプションを使用して、追加のユーザーにアクセスを許可できます。  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)