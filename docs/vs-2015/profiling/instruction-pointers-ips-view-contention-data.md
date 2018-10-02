---
title: 命令ポインター (IP) ビュー - 競合データ | Microsoft Docs
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
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 080e71b12bd41d4649556541326480cf018a2b5b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547994"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>命令ポインター (IP) ビュー - 競合データ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[命令ポインター (Ip) ビュー - 競合データ](https://docs.microsoft.com/visualstudio/profiling/instruction-pointers-ips-view-contention-data)します。  
  
競合データの IP ビューには、プロファイル実行中に実行がブロックされていたアセンブリ命令のデータが一覧表示されます。  
  
 命令ポインター ビュー内の列の値について、次の表で説明します。  
  
|Column|説明|  
|------------|-----------------|  
|**排他ブロック時間**|この関数のブロック時間。|  
|**排他ブロック時間 %**|命令の実行中のブロック時間の割合。|  
|**排他競合**|命令の実行中に発生した競合の数。|  
|**排他競合 %**|プロファイリング実行のすべての競合に対する、命令の実行中に発生した競合の割合。|  
|**関数アドレス**|読み込まれたバイナリ内の関数の開始メモリ アドレス。|  
|**関数名**|命令を含む関数の名前。|  
|**命令ポインター アドレス**|読み込まれたバイナリ内の命令のメモリ アドレス。|  
|**関数行番号**|ソース ファイルでのこの関数の開始行番号です。|  
|**モジュール名**|命令を含むモジュールの名前。|  
|**モジュール パス**|命令を含むモジュールのパス。|  
|**プロセス ID**|プロファイリングされたプロセスのプロセス ID (PID)。|  
|**プロセス名**|プロセスの名前です。|  
|**ソース開始文字番号**|この命令の開始位置である、ソース ファイル行内の文字のオフセット。|  
|**ソース終了文字番号**|この命令の終了位置である、ソース ファイル行内の文字のオフセット。|  
|**ソース ファイル**|命令を含むソース ファイル。|  
|**ソース開始行**|この命令の開始位置である、ソース ファイル内の行番号。|  
|**ソース終了行**|この命令の終了位置である、ソース ファイル内の行番号。|  
  
## <a name="see-also"></a>関連項目  
 [方法: レポート ビューの列をカスタマイズする](../profiling/how-to-customize-report-view-columns.md)   
 [命令ポインター (IP) ビュー](../profiling/instruction-pointers-ips-view.md)   
 [命令ポインター (IP) ビュー - サンプリング](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [命令ポインター (IP) ビュー](../profiling/instruction-pointers-ips-view-sampling-data.md)



