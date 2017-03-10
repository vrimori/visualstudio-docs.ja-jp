---
title: "プロセス ビュー | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a1f55111b5fcc8c36a5bfc8f86d25354fa89d8b8
ms.lasthandoff: 02/22/2017

---
# <a name="process-view"></a>プロセス ビュー
プロセス ビューには、プロファイリング実行中に実行されたプロセスとスレッドのプロファイル データが表示されます。  
  
 プロセスは、名前ごとに一覧表示されます。 スレッドは、そのスレッドを作成したプロセスの子ノードとして一覧表示されます。 スレッドには、ストレージを開始した関数の名前、または使用できるシンボルがない場合はラベルの名前 **[ntdll.dll]** が付けられます。  
  
 列を追加または削除するには、ビューを右クリックし、**[列の追加と作業時間]** を選択します。 また、データを並べ替えるには、列名をクリックします。 詳細については、「[方法: レポート ビューの列をカスタマイズする](../profiling/how-to-customize-report-view-columns.md)」を参照してください。  
  
 プロセス ビューの列は、サンプリング メソッドとインストルメンテーション メソッドで生成されたデータ、および .NET メモリ データを含むデータの列と同じです。 次の表に列の値を示します。  
  
|Column|説明|  
|------------|-----------------|  
|**ID (一意)**|プロファイラーによって生成される、プロセスまたはスレッドに固有の ID。|  
|**ID**|システムによって生成される、プロセスまたはスレッドの ID。|  
|**名前**|プロセスまたはスレッドの名前。|  
|**開始時刻**|プロファイリングの開始からプロセスまたはスレッドの開始までの時間 (ミリ秒) またはプロセッサ サイクル数。|  
|**終了時刻**|プロファイリングの開始からプロセスまたはスレッドの終了までの時間 (ミリ秒) またはプロセッサ サイクル数。|  
  
## <a name="see-also"></a>関連項目  
 [サンプリング メソッドのデータ ビュー](../profiling/profiler-sampling-method-data-views.md)   
 [インストルメンテーション メソッドのデータ ビュー](../profiling/instrumentation-method-data-views.md)   
 [.NET メモリのデータ ビュー](../profiling/dotnet-memory-data-views.md)
