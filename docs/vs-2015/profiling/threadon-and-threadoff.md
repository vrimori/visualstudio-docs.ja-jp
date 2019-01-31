---
title: ThreadOn と ThreadOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77868ea7082c1b9118b70062f19195d94b4ca20a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780787"
---
# <a name="threadon-and-threadoff"></a>ThreadOn と ThreadOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe の **ThreadOff** および **ThreadOn** サブコマンドは、インストルメンテーション メソッドを使用するコマンド ライン プロファイリング セッションでのみ使用できます。 **ThreadOff** および **ThreadOn** は、指定されたスレッドのプロファイリングを一時停止および再開します。 **ThreadOff** がスレッドのプロファイリングを停止し、**ThreadOn** がスレッドのプロファイリングを開始します。  
  
 多くの場合、**ThreadOn** または **ThreadOff** を VSPerfCmd.exe コマンド ラインの唯一のオプションとして指定しますが、**GlobalOn**、**GlobalOff**、**ProcessOn**、**ProcessOff** の各サブコマンドと組み合わせて使用することもできます。  
  
 **ThreadOn** サブコマンドと **ThreadOff** サブコマンドは、コマンド ライン プロファイリング セッションのすべてのプロセスについてのデータ収集を制御する **GlobalOn** サブコマンドと **GlobalOff** サブコマンド、および指定されたプロセスについてのデータ収集を制御する **ProcessOn** サブコマンドと **ProcessOff** サブコマンドと対話します。  
  
 **ThreadOff** サブコマンドおよび **ThreadOn** サブコマンドは、プロファイラー API 関数によって操作されるスレッドの開始/停止数にも影響します。  
  
- **ThreadOff** は、スレッドの開始/停止数を直ちに 0 に設定して、プロファイリングを一時停止します。  
  
- **ThreadOn** は、スレッドの開始/停止数を直ちに 1 に設定して、プロファイリングを再開します。  
  
  詳細については、[「プロファイリング ツールの API」](../profiling/profiling-tools-apis.md) を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 `TID`  
 開始または停止するスレッドの整数の ID。  
  
## <a name="valid-options"></a>有効なオプション  
 **ThreadOn** と **ThreadOff** は、次のサブコマンドも含むコマンド ラインで指定できます。  
  
 **Start:** `Method`  
 コマンド ライン プロファイル セッションを初期化し、指定されたプロファイル方法を設定します。  
  
 **GlobalOff**&#124;**GlobalOn**  
 コマンド ライン プロファイル セッションのすべてのプロセスのプロファイリングを停止または開始します。  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 指定されたプロセスのプロファイリングを停止または開始します。  
  
## <a name="example"></a>例  
 この例では、アプリケーションのスタートアップ データのみが収集されるように、**ThreadOff** サブコマンドを使用してプロファイル データの収集を停止します。  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>「  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)
