---
title: "Console | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Console
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **Console** オプションを使用すると、新しいコマンド プロンプト ウィンドウで指定したアプリケーションが起動します。  **Console** オプションと共に使用できるオプションは、VSPerfCmd の **Launch** オプションのみです。  アプリケーションがコマンド ライン アプリケーションでない場合、**Console** を指定しても何も実行されません。  
  
## 構文  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### パラメーター  
 なし。  
  
## 必須のオプション  
 **Console** オプションは、**Launch** オプションが含まれたコマンド ラインでのみ指定できます。  
  
 **Launch:** `AppName`  
 プロファイラーと、`AppName` で指定したアプリケーションを起動します。  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)