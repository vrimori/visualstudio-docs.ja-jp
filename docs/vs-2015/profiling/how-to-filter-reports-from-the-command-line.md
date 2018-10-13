---
title: '方法: コマンド ラインからレポートをフィルター処理する | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a93e1bb2e1d3a65d82a4a0ac54e903ee20553d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290148"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>方法: コマンド ラインからレポートをフィルター処理する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VSPerfReport** コマンドのオプションを利用すると、レポートをフィルター処理し、プロファイリング データ ファイルの特定の時間区分に絞り込むか、1 つ以上のプロセスまたはスレッドに絞り込むことができます。 このコマンドの詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  
  
|オプション|説明|  
|-------------|-----------------|  
|**StartTime:**[*Value*]|ミリ秒単位の時間 (value) よりも後に収集されたデータのみを表示します。|  
|**EndTime:**[*Value*]|ミリ秒単位の時間 (value) よりも前に収集されたデータのみを表示します。|  
|**FilterFile:** `VSPFFile`|Visual Studio の **[パフォーマンス レポート]** ウィンドウから生成されたフィルター ファイルの場所を指定します。|  
|**MsFilter:**[*StartTime,Duration*]|開始時刻 (`StartTime`) からミリ秒単位の時間 (`Duration`) 内のみのデータを表示します。|  
|**Process:**[*Pid*]|指定されたプロセスのデータのみを表示します。|  
|**Thread:**[*ThreadID*]|指定されたスレッドのデータのみを表示します。|  
|**Thread:**[*ThreadID,ProcessID*]|指定されたプロセスに関連付けられている指定されたスレッドのデータのみを表示します。|



