---
title: "命令ポインター (IP) ビュー - .NET メモリ サンプリング データ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c37cc7b63a8f93c3b63cdda0bb9ce460a01d195a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>命令ポインター (IP) ビュー - .NET メモリ サンプリング データ
サンプリング メソッドを使用して収集された .NET メモリの割り当てプロファイル データの IP ビューには、プロファイル実行中にメモリを割り当てたアセンブリ命令が一覧表示されます。 ビューの列には、割り当てのサイズと数も一覧表示されます。  
  
 排他的な値のみが一覧表示されます。  
  
|Column|説明|  
|------------|-----------------|  
|**プロセス ID**|プロファイリング実行のプロセス ID (PID) です。|  
|**プロセス名**|プロセスの名前です。|  
|**モジュール名**|命令を含むモジュールの名前。|  
|**モジュール パス**|命令を含むモジュールのパスです。|  
|**ソース ファイル**|命令を含むソース ファイルです。|  
|**関数名**|関数の名前。|  
|**関数行番号**|ソース ファイルでのこの関数の開始行番号です。|  
|**関数アドレス**|関数の開始アドレスです。|  
|**ソース開始行**|割り当てが行われたソース ファイル内の開始行番号です。|  
|**ソース終了行**|割り当てが行われたソース ファイル内の終了行番号です。|  
|**ソース開始文字番号**|割り当てが行われたソース ファイル行内の開始文字のオフセットです。|  
|**ソース終了文字番号**|割り当てが行われたソース ファイル行内の終了文字のオフセットです。|  
|**命令ポインター アドレス**|命令のアドレス。|  
|**割り当て数 (関数のみ)**|命令によって作成されたオブジェクトの総数。|  
|**割り当て % (関数のみ)**|プロファイル実行中に作成されたすべてのオブジェクトのうち、命令によって割り当てられたオブジェクトの割合。|  
|**割り当てバイト数 (関数のみ)**|プロファイル実行中に割り当てられ、命令によって割り当てられたメモリのバイト数。|  
|**割り当てバイト数 % (関数のみ)**|プロファイル実行中に割り当てられたメモリの総バイト数のうち、命令によって割り当てられたバイト数の割合。|  
  
## <a name="see-also"></a>関連項目  
 [命令ポインター (IP) ビュー](../profiling/instruction-pointers-ips-view-sampling-data.md)