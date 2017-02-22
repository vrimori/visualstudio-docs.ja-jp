---
title: "WinCounter | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# WinCounter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**WinCounter** オプションは、プロファイル実行中に一定間隔で収集する Windows またはアプリケーションのパフォーマンス カウンターを指定します。  Windows とアプリケーションのパフォーマンス カウンターは、プロファイル データ ファイルにマークとして一覧表示されます。  別個のオプションで収集する複数のパフォーマンス カウンターを指定できます。  
  
 既定では、カウンターは 500 ミリ秒ごとに収集されます。  別の収集間隔を指定するには、**AutoMark** オプションを使用します。  
  
 **AutoMark** オプションは 1 つしか使用できません。  複数の **AutoMark** オプションを指定した場合は、最後のオプションが使用されます。  
  
 **WinCounter** オプションと共に使用できるオプションは **Start** オプションのみです。  
  
## 構文  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### パラメーター  
 `Path`  
 PDH カウンター パス形式の Windows パフォーマンス カウンター。  
  
## 必須のオプション  
 **WinCounter** オプションと共に使用できるオプションは **Start** オプションのみです。  
  
 **Start:** `Method`  
 **Start** オプションは、指定したプロファイル方法にプロファイラーを初期化します。  
  
## 排他的オプション  
 **AutoMark** オプションと共に使用できるオプションは **WinCounter** オプションのみです。  
  
 **AutoMark:** `Milliseconds`  
 Windows パフォーマンス カウンター データ収集の間隔をミリ秒単位で指定します。  
  
## 使用例  
 次の例では、1000 ミリ秒間隔で収集される 2 つの Windows パフォーマンス カウンターが指定されています。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)