---
title: Args | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d8a017af5ff5a9c7ca9c0f634e776f8d05b44e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040516"
---
# <a name="args"></a>Args
VSPerfCmd.exe **Args** オプションは、**Launch** サブコマンドの対象アプリケーションに渡される引数のリストを指定します。  
  
 **Args** は、コマンド ラインで **Launch** も指定された場合にのみ使用できます。 **Args** は、**Launch** を指定した場合のオプションです。  
  
## <a name="syntax"></a>構文  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Arguments`  
 **Launch** コマンドのターゲット アプリケーションへの引数のリスト。  
  
## <a name="required-options"></a>必須オプション  
 **Launch:** `AppName`  
 指定したアプリケーションを起動し、サンプリング メソッドでプロファイリングを開始します。  
  
## <a name="example"></a>例  
 次の例では、**Args** オプションを使用して引数を TestApp.exe に渡します。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [サービスのプロファイリング](../profiling/command-line-profiling-of-services.md)