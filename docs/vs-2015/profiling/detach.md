---
title: Detach | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56ad870d4638607ad03b60b33bb7d648dbbca424
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539575"
---
# <a name="detach"></a>Detach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デタッチ](https://docs.microsoft.com/visualstudio/profiling/detach)します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)



