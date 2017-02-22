---
title: "CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **CrossSession** オプションを使用すると、プロファイラーが任意のコンソール セッションからデータを収集できるようになります。  **CrossSession** オプションは **Start** オプションと共に使用する必要があります。  
  
 **CrossSession** の代わりに省略形 **CS** を使用できます。  
  
## 構文  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### パラメーター  
 なし。  
  
## 有効なオプション  
 別のセッションでプロファイリングを有効にするには、**Start** オプションと **CrossSession** オプションを指定する必要があります。  以降のすべての **VSPerfCmd Attach** コマンドおよび **Detach** コマンドでも、**CrossSession** を指定する必要があります。  
  
 **Start:** `Method`  
 **Start** オプションは、指定したプロファイル方法にプロファイラーを初期化します。  
  
 **Attach:** *PID*\[**,***PID*\]  
 指定されたプロセスのプロファイリングを開始します。  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 指定されたプロセスのプロファイリングを停止します。  
  
## 使用例  
 この例では、別のコンソール セッションで開始されたアプリケーションにアタッチするために **CrossSession** オプションが使用されています。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)