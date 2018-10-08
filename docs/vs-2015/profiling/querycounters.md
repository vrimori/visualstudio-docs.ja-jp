---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff5cd703a323c93c479d69bbe956855106d80d80
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534830"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[QueryCounters](https://docs.microsoft.com/visualstudio/profiling/querycounters)します。  
  
**QueryCounters** オプションは、コンピューターで使用可能な CPU (ハードウェア) パフォーマンス カウンターをリストします。  
  
 **QueryCounters** は、コマンド ラインで唯一のオプションである必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし  
  
## <a name="remarks"></a>Remarks  
 インストルメンテーション メソッドを使用している場合、プロファイラーは各データ コレクション イベントで 1 つ以上の CPU パフォーマンス カウンターの値を収集できます。 サンプリング プロファイル方法を使用している場合、1 つのカウンター イベントとサンプリング間隔として使用されるイベント出現回数を指定できます。  
  
 プロセッサごとに異なる CPU パフォーマンス カウンターが公開されます。 プロファイラーは、ほぼすべてのプロセッサで使用できる一連の汎用カウンターを定義します。 **QueryCounters** オプションでは、汎用カウンター名と、プロセッサに固有のカウンター名の両方をリストします。  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)



