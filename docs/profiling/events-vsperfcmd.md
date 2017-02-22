---
title: "Events (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **Events** オプションは、Windows イベント トレーシング \(ETW: Event Tracing for Windows\) ログの記録を制御します。  ETW データは、プロファイラー データ ファイルとは別の .etl ファイルに保存されます。  このデータは、[VSPerfReport](../profiling/vsperfreport.md) \/summary:etw コマンドを使用してレポートに表示できます。  
  
 **Events** オプションは、VSPerfCmd の **Shutdown** コマンドを呼び出す前であれば、いつでも呼び出すことができます。  
  
## 構文  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### パラメーター  
 **On**&#124;**Off**  
 イベント データの収集を開始または停止します。  
  
 `Guid`  
 プロバイダー コントロールの GUID。  
  
 `ProviderName`  
 WMI \(Windows Management Instrumentation\) を使用して登録されたプロバイダーの名前。  
  
 `Flags`  
 イベント プロバイダーによって定義された、16 進数の "0x" プレフィックス付きのフラグ値。  
  
 `Level`  
 収集されるデータの量を指定します。  `Level` は、イベント プロバイダーによって定義されます。  
  
 **Events** オプションは、次のカーネルのキーワードをプロバイダー名として認識します。  
  
 **Process**  
 プロセス イベント  
  
 **Thread**  
 スレッド イベント  
  
 **Image**  
 イメージの読み込み\/アンロード イベント  
  
 **Disk**  
 ディスク I\/O イベント  
  
 **File**  
 ファイル I\/O イベント  
  
 **Hardfault**  
 ハード ページ フォールト  
  
 **Pagefault**  
 ソフト ページ フォールト  
  
 **Network**  
 ネットワーク イベント  
  
 **Registry**  
 レジストリ アクセス イベント  
  
 カーネル プロバイダーは、有効化のみが可能です。  モニターがシャットダウンするまでは、無効にしたりそのフラグを変更したりすることはできません。  
  
## 解説  
  
> [!NOTE]
>  CLR ETW イベントを有効にした場合は、追加のスタートアップ データも TraceView レポートに収集されます。  レポートにスタートアップ イベントが出力されないようにするには、次のコマンドを使用します。  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  MOF \(Managed Object Format\) ファイルにスタートアップ イベントがリストされていないという理由でスタートアップ イベントを除外しなかった場合、これらのイベントはレポート内で GUID として表示されます。  詳細については、Microsoft Web サイトのページを参照します: [サンプル Managed Object Format \(MOF\) のファイル](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)