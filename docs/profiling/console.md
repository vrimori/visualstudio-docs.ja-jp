---
title: コンソール | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9450254620fff8981aa9330dc41535ec69c0d842
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944140"
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
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [サービスのプロファイリング](../profiling/command-line-profiling-of-services.md)