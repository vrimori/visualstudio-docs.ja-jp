---
title: "Output | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Output
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Output** オプションには、パフォーマンス セッションのプロファイル データ ファイルの名前と場所を指定します。  **Output** は **Start** オプションと共に使用する必要があります。  
  
## 構文  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### パラメーター  
 `FileName`  
 データ ファイルの名前。  完全パスまたは部分パスで指定できます。  パスの指定を省略すると、ファイルは現在のディレクトリに作成されます。  
  
## 必須のオプション  
 **Output** は **Start** オプションと共に使用する必要があります。  
  
 **Start:** `Method`  
 出力ファイル名を指定します。  
  
## 使用例  
 現在のディレクトリにプロファイル データ ファイルを作成する例を以下に示します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)