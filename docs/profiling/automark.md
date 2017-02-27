---
title: "AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**AutoMark** オプションは、Windows ソフトウェア パフォーマンス カウンターのイベントを収集する間隔をミリ秒単位で指定します。  Windows パフォーマンス カウンターは **WinCounter** オプションで指定します。  
  
 コマンド ラインに指定できる **AutoMark** オプションは 1 つのみです。  **AutoMark** によって指定された **WinCounter** のサンプリング間隔は、メイン サンプリング間隔には依存しません。  
  
## 構文  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### パラメーター  
 `Milliseconds`  
 Windows パフォーマンス カウンターのイベントを収集する間隔をミリ秒単位で指定します。  
  
## 必須のオプション  
 **WinCounter:** `Path`  
 収集する Windows パフォーマンス カウンターを指定します。  インストルメンテーション メソッドを使用している場合は、複数の Windows カウンターを指定できます。  サンプリング メソッドを使用している場合は、1 つのソフトウェア カウンターのみを指定できます。  **WinCounter** オプションは、**Start** オプションが含まれたコマンド ラインで指定する必要があります。  
  
## 使用例  
 この例では、2 つの Windows パフォーマンス カウンターのサンプリング間隔として 1000 ミリ秒が設定されます。  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)