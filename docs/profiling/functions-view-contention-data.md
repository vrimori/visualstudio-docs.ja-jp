---
title: "関数ビュー - プロファイラー競合データ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[関数] ビュー"
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 関数ビュー - プロファイラー競合データ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

競合データの関数レポート ビューには、プロファイリング実行中に実行がブロックされた関数が一覧表示されます。  
  
 次の表では、関数ビューに表示される、同時実行メソッドを使用して収集されたプロファイル データ ファイルの値について説明します。  
  
|列|説明|  
|-------|--------|  
|**\[排他ブロック時間\]**|関数の本体でのコード実行がブロックされていた時間。  この関数によって呼び出された関数のブロック時間は含まれません。|  
|**\[排他ブロック時間 %\]**|プロファイリング実行のすべてのブロック時間に対する、この関数の排他ブロック時間の割合。|  
|**\[排他競合\]**|この関数の本体でのコードの実行がブロックされた回数。  この関数によって呼び出された関数の競合は含まれません。|  
|**\[排他競合 %\]**|プロファイリング実行のすべての競合に対する、この関数の排他競合の割合。|  
|**\[関数アドレス\]**|関数のアドレス。|  
|**\[関数名\]**|関数の完全修飾名。|  
|**包括ブロック時間**|関数またはこの関数が呼び出した関数の実行がブロックされていた時間。|  
|**包括ブロック時間 %**|プロファイリング実行のすべてのブロック時間に対する、この関数またはモジュールの包括ブロック時間の割合。|  
|**包括競合**|関数またはこの関数が呼び出した関数の実行がブロックされた回数。|  
|**包括競合 %**|プロファイリング実行のすべての競合に対する、関数またはモジュールの包括競合の割合。|  
|**\[関数行番号\]**|ソース ファイルのこの関数の開始行番号。|  
|**\[モジュール名\]**|関数を含むモジュールの名前。|  
|**\[モジュール パス\]**|関数を含むモジュールのパス。|  
|**プロセス ID**|関数を実行したプロセスのプロセス ID \(PID\)。|  
|**プロセス名**|プロセスの名前。|  
|**\[ソース ファイル\]**|この関数の定義を含むソース ファイル。|  
  
## 参照  
 [方法: レポート ビューの列をカスタマイズする](../profiling/how-to-customize-report-view-columns.md)   
 [関数ビュー](../profiling/functions-view.md)   
 [関数ビュー \- インストルメンテーション](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [関数ビュー \- サンプリング](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [関数ビュー](../profiling/functions-view-instrumentation-data.md)   
 [関数ビュー](../profiling/functions-view-sampling-data.md)