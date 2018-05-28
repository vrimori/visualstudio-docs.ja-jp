---
title: コンソール | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7fb90261453caab8dbe54fce79605c1d891d537
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2018
---
# <a name="console"></a>コンソール
VSPerfCmd.exe で **Console** オプションを指定すると、新しいコマンド プロンプト ウィンドウで指定のアプリケーションが開始します。 **Console** オプションは、VSPerfCmd の **Launch** オプションとの併用でのみ使用できます。 アプリケーションがコマンドライン アプリケーションではない場合、**Console** を指定しても何も起こりません。  
  
## <a name="syntax"></a>構文  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし  
  
## <a name="required-options"></a>必須オプション  
 **Console** オプションは、**Launch** オプションも含むコマンド ラインでのみ指定できます。  
  
 **Launch:** `AppName`  
 プロファイラーと、`AppName` で指定されたアプリケーションを起動します。  
  
## <a name="see-also"></a>参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)