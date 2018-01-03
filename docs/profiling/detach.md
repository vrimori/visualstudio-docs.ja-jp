---
title: Detach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eba6a028e1a4431be0338ea76874019ed53f23ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="detach"></a>Detach
VSPerfCmd.exe **Detach** オプションは、何も指定されていない場合、プロファイラーを指定のプロセスまたはすべてのプロセスから切断します。 サンプリング方法を利用し、プロファイリングを初期化しておく必要があります。  
  
 **Launch** オプションまたは **Attach** オプションを指定して開始したプロファイリングは、**Detach** で切断できます。 後続の **Attach** コマンドでプロファイラーを再接続できます。  
  
 **Detach** では、プロファイリング データ ファイルは閉じられません。 プロファイリングを終了し、データ ファイルを閉じるには、**Shutdown** オプションを使用します。  
  
> [!NOTE]
>  **Start** オプションを **Crosssession** オプションと共に指定した場合、**VSPerfCmd /Attach** または **VSPerfCmd /Detach** を呼び出すには **Crosssession** も指定する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `PIDs|ProcessNames`  
 `PID` - 1 つまたは複数のプロセスの数字のシステム識別子。  
  
 `ProcessNames` - プロセスの名前。 名前付きプロセスの複数のインスタンスが実行されている場合、結果は予想できません。  
  
 複数のプロセスを指定するときは、コンマで区切ります。  
  
 プロセスが指定されていない場合、プロファイリングされているすべてのプロセスからプロファイラーが切断されます。  
  
## <a name="valid-options"></a>有効なオプション  
 **Attach** オプションと組み合わせて単一コマンド ラインで指定できる **VSPerfCmd** オプションを以下に示します。  
  
 **Crosssession**  
 ログオン セッション以外のセッションでプロファイリング アプリケーションを有効にします。 **Start** オプションが **Crosssession** オプションと共に指定された場合、必須です。  
  
## <a name="example"></a>例  
 この例では、**Detach** コマンドはプロファイリングを一時停止します。**Shutdown** コマンドはプロファイラー データ ファイルを閉じます。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)