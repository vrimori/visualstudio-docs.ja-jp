---
title: コンソール | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed90d282841cf8c066f1b8496e1778939ef9ad6c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305315"
---
# <a name="console"></a>コンソール
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe で **Console** オプションを指定すると、新しいコマンド プロンプト ウィンドウで指定のアプリケーションが開始します。 **Console** オプションは、VSPerfCmd の **Launch** オプションとの併用でのみ使用できます。 アプリケーションがコマンドライン アプリケーションではない場合、**Console** を指定しても何も起こりません。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)



