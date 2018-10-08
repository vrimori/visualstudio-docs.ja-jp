---
title: WinCounter | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9a8e381ed058c30dcbf1760f380cf065c1443cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544970"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[WinCounter](https://docs.microsoft.com/visualstudio/profiling/wincounter)します。  
  
**WinCounter** オプションでは、プロファイルの実行中に一定間隔で収集する Windows またはアプリケーションのパフォーマンス カウンターを指定します。 Windows とアプリケーションのパフォーマンス カウンターは、プロファイル データ ファイルにマークとして一覧表示されます。 収集するパフォーマンス カウンターは、別個のオプションで複数指定できます。  
  
 既定では、カウンターは 500 ミリ秒ごとに収集されます。 別の収集間隔を指定するには、**AutoMark** オプションを使用します。  
  
 **AutoMark** オプションは 1 つしか使用できません。 複数の **AutoMark** オプションを指定した場合は、最後のオプションが使用されます。  
  
 **WinCounter** オプションと共に使用できるオプションは **Start** オプションのみです。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Path`  
 PDH カウンター パス形式の Windows パフォーマンス カウンターです。  
  
## <a name="required-options"></a>必須オプション  
 **WinCounter** オプションと共に使用できるオプションは **Start** オプションのみです。  
  
 **Start:** `Method`  
 **Start** オプションは、指定したプロファイル方法にプロファイラーを初期化します。  
  
## <a name="exclusive-options"></a>排他的なオプション  
 **AutoMark** オプションと共に使用できるオプションは **WinCounter** オプションのみです。  
  
 **AutoMark:** `Milliseconds`  
 Windows パフォーマンス カウンターのデータ収集間隔をミリ秒単位で指定します。  
  
## <a name="example"></a>例  
 次の例では、1000 ミリ秒間隔で収集される 2 つの Windows パフォーマンス カウンターが指定されています。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)



