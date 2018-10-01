---
title: 関数ビュー - 競合データ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1250dfc781b57f3b289cbafc9d386b27b669ddf7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537180"
---
# <a name="functions-view---contention-data"></a>関数ビュー - 競合データ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[関数ビュー - 競合データ](https://docs.microsoft.com/visualstudio/profiling/functions-view-contention-data)します。  
  
競合データの関数レポート ビューには、プロファイリング実行中に実行がブロックされた関数が一覧表示されます。  
  
 コンカレンシー メソッドで収集されたプロファイリング データ ファイルの関数ビューに表示される値について、次の表で説明します。  
  
|Column|説明|  
|------------|-----------------|  
|**排他ブロック時間**|この関数の関数本体でのコードの実行がブロックされていた時間。 この関数によって呼び出された関数のブロック時間は含まれません。|  
|**排他ブロック時間 %**|プロファイリング実行のすべてのブロック時間に対する、この関数の排他的なブロック時間の割合。|  
|**排他競合**|この関数の関数本体でのコードの実行がブロックされた回数。 この関数によって呼び出された関数の競合は含まれません。|  
|**排他競合 %**|プロファイリング実行のすべての競合に対する、この関数の排他的競合の割合。|  
|**関数アドレス**|関数のアドレス。|  
|**関数名**|関数の完全修飾名です。|  
|**包括ブロック時間**|この関数またはこの関数で呼び出された関数の実行がブロックされていた時間。|  
|**包括ブロック時間 %**|プロファイリング実行のすべてのブロック時間に対する、この関数またはモジュールの包括的なブロック時間の割合。|  
|**包括競合**|この関数またはこの関数で呼び出された関数の実行がブロックされた回数。|  
|**包括競合 %**|プロファイル実行のすべての競合に対する、この関数またはモジュールの包括競合の割合。|  
|**関数行番号**|ソース ファイルでのこの関数の開始行番号です。|  
|**モジュール名**|関数を含むモジュールの名前です。|  
|**モジュール パス**|関数を含むモジュールのパスです。|  
|**プロセス ID**|関数を実行したプロセスのプロセス ID (PID)。|  
|**プロセス名**|プロセスの名前です。|  
|**ソース ファイル**|この関数の定義を含むソース ファイルです。|  
  
## <a name="see-also"></a>関連項目  
 [方法: レポート ビューの列をカスタマイズする](../profiling/how-to-customize-report-view-columns.md)   
 [関数ビュー](../profiling/functions-view.md)   
 [関数ビュー - インストルメンテーション](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [関数ビュー - サンプリング](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [関数ビュー](../profiling/functions-view-instrumentation-data.md)   
 [関数 ビュー](../profiling/functions-view-sampling-data.md)



