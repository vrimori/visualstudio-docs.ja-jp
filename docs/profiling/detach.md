---
title: "Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Detach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe の **Detach** オプションを使用すると、指定したプロセス、またはすべてのプロセス \(何も指定しない場合\) からプロファイラーがデタッチされます。  プロファイリング実行は、サンプリング メソッドを使用して初期化されている必要があります。  
  
 **Launch** オプションまたは **Attach** オプションを指定して開始されたプロファイリング実行は、**Detach** を使用して切り離すことができます。  後で **Attach** コマンドを使用することにより、プロファイラーを再アタッチできます。  
  
 **Detach** は、プロファイル データ ファイルを閉じません。  プロファイリング実行を終了し、データ ファイルを閉じるには、**Shutdown** オプションを使用します。  
  
> [!NOTE]
>  **Start** オプションと共に **Crosssession** オプションが指定されている場合は、**VSPerfCmd \/Attach** または **VSPerfCmd \/Detach** への呼び出しでも **Crosssession** を指定する必要があります。  
  
## 構文  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### パラメーター  
 `PIDs|ProcessNames`  
 `PID` \- 1 つ以上のプロセスの数値のシステム ID。  
  
 `ProcessNames` \- プロセスの名前。  この名前付きのプロセスの複数インスタンスが実行中の場合、結果は予測できません。  
  
 複数のプロセスを指定するときは、コンマで区切ります。  
  
 プロセスが指定されない場合、プロファイルされているすべてのプロセスからプロファイラーがデタッチされます。  
  
## 有効なオプション  
 **Attach** オプションと組み合わせて 1 行のコマンド ラインで指定できる **VSPerfCmd** オプションを次に示します。  
  
 **Crosssession**  
 ログオン セッション以外のセッションにおけるアプリケーションのプロファイリングを有効にします。  **Start** オプションと共に **Crosssession** オプションが指定された場合は必須です。  
  
## 使用例  
 この例では、**Detach** コマンドでプロファイリング実行が中断され、**Shutdown** コマンドでプロファイラー データ ファイルが閉じられます。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)