---
title: "LineOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LineOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

既定では、サンプリング プロファイル方法を使用するときに、プロファイラーがソース コードの行番号と行番号オフセットのデータを収集します。  VSPerfCmd **LineOff** オプションを指定すると、VSPerfCmd を使用してアプリケーションを起動するときに、行番号データの収集が無効になります。  **LineOff** を指定した場合、プロファイル データは関数レベルで収集されます。  
  
 **LineOff** は、**Start**:**Sample** オプションを使用してサンプリングするようにプロファイラーが初期化されている場合に、**Launch** オプションと共にのみ使用できます。  
  
## 構文  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### パラメーター  
 なし。  
  
## 必須のオプション  
 **LineOff** オプションは、**Launch** オプションが含まれたコマンド ラインでのみ使用できます。  
  
 **Launch:** `AppName`  
 指定されたアプリケーションを起動し、サンプリング メソッドを使用してプロファイリングを開始します。  
  
## 使用例  
 この例では、アプリケーションとプロファイラーを起動し、行レベルのサンプリングを無効にします。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)