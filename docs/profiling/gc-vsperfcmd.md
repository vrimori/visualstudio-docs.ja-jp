---
title: "GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**GC** オプションを使用すると、.NET Framework のメモリの割り当てデータとオブジェクトの有効期間データを収集できます。  **GC** オプションは、サンプリング プロファイル方法でのみ使用でき、一緒に使用できるオプションは **Launch** オプションのみです。  
  
 **GC** オプションを使用する場合、VSPerfClrEnv **\/sampleon** コマンドは必要ありません。  
  
 パラメーターを指定しない場合、または **Allocation** パラメーターが指定されている場合は、.NET Framework のメモリの割り当てデータだけが収集されます。  **Lifetime** パラメーターが指定されている場合は、.NET Framework のメモリの割り当てデータと .NET Framework のオブジェクトの有効期間データの両方が収集されます。  
  
## 構文  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### パラメーター  
 **Allocation**  
 既定値です。  .NET Framework のメモリの割り当てデータを収集します。  
  
 **Lifetime**  
 .NET Framework のメモリの割り当てデータと .NET Framework のオブジェクトの有効期間データの両方を収集します。  
  
## 必須のオプション  
 **GC** オプションと共に使用できるオプションは  **Launch** オプションのみです。  
  
 **Launch:** `AppName`  
 指定されたアプリケーションを起動し、サンプリング メソッドを使用してプロファイリングを開始します。  
  
## 使用例  
 次の例では、アプリケーションを起動し、.NET Framework のメモリの割り当てデータを収集します。  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)