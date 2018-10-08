---
title: Shutdown | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7e351050859a96ca95c267bdcbe34ee19e7f87f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537301"
---
# <a name="shutdown"></a>シャットダウン
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[シャット ダウン](https://docs.microsoft.com/visualstudio/profiling/shutdown)します。  
  
**Shutdown** オプションは、現在プロファイル中のプロセスが終了するかデタッチされるまで待機して、プロファイラーをオフにし、プロファイル データ ファイルを閉じます。 **Shutdown** オプションは、プロファイル実行の最後のコマンドである必要があります。  
  
 タイムアウト パラメーターが指定されていない場合、**Shutdown** オプションは無期限に待機します。 タイムアウト パラメーターが指定されている場合、指定された秒数の経過後にオプションから制御が戻りますが、プロファイラーはオフにされず、データ ファイルも閉じられません。  
  
 コマンド ラインで指定するオプションは **Shutdown** オプションのみにする必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Timeout`  
 -   (省略可能) 指定した場合は、指定した秒数の経過後にオプションから制御が戻りますが、プロファイラーはオフにされず、プロファイル データ ファイルも閉じられません。  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)



