---
title: Detach | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97e5e64947f2d2807e2d3e34d50827e989ea18e2
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804722"
---
# <a name="detach"></a>Detach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Detach** オプションを使用すると、何も指定されていない場合、プロファイラーが指定のプロセスまたはすべてのプロセスから切断されます。 サンプリング方法を利用し、プロファイリングを初期化しておく必要があります。  
  
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



