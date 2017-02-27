---
title: "Args | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Args
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **Args** オプションは、**Launch** サブコマンドの対象アプリケーションに渡される引数のリストを指定します。  
  
 **Args** は、コマンド ラインで **Launch** も指定する場合にのみ使用できます。  **Launch** を指定する場合、**Args** は省略可能です。  
  
## 構文  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### パラメーター  
 `Arguments`  
 **Launch** コマンドの対象アプリケーションに渡す引数リスト。  
  
## 必須のオプション  
 **Launch:** `AppName`  
 指定されたアプリケーションを起動し、サンプリング メソッドを使用してプロファイリングを開始します。  
  
## 使用例  
 **Args** オプションを使用して、引数を TestApp.exe に渡す例を次に示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)