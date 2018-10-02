---
title: コール ツリー ビュー - インストルメンテーション データ | Microsoft Docs
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
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54360ded2c3e758658969484515e06e50b86b45e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539075"
---
# <a name="call-tree-view---instrumentation-data"></a>コール ツリー ビュー - インストルメンテーション データ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コール ツリー ビュー - インストルメンテーション データ](https://docs.microsoft.com/visualstudio/profiling/call-tree-view-instrumentation-data)します。  
  
コール ツリーの関数の値は、コール ツリーの親関数によって呼び出された関数インスタンスの時間を示します。 割合の値を計算するには、関数インスタンスの値と、プロファイル実行のすべての関数の包括経過時間の総計を比較します。  
  
## <a name="general"></a>全般  
 全般の各列は、ビューの行で関数を識別します。  
  
|Column|説明|  
|------------|-----------------|  
|**関数名**|関数の名前。|  
|**関数アドレス**|関数のアドレス。|  
|**関数行番号**|ソース ファイルでのこの関数の開始行番号です。|  
|**呼び出し数**|この関数に対して行われた呼び出しの総数です。|  
|**ソース ファイル**|この関数の定義を含むソース ファイルです。|  
|**モジュール名**|関数を含むモジュールの名前です。|  
|**モジュール パス**|関数を含むモジュールのパスです。|  
|**プロセス ID**|プロファイリング実行のプロセス ID (PID) です。|  
|**プロセス名**|プロセスに割り当てられた名前です。|  
|**プローブ オーバーヘッド時間 (関数のみ)**|インストルメンテーションによって発生したこの関数のオーバーヘッド時間。 プローブ オーバーヘッドはすべての排他時間から減算されています。|  
|**プローブ オーバーヘッド時間 (子を含む)**|インストルメンテーションによって発生したこの関数とその子関数のオーバーヘッド時間。 プローブ オーバーヘッドはすべての包括時間から減算されています。|  
|**レベル**|コール ツリーにおけるこの関数の深度。 [VSPerfReport](../profiling/vsperfreport.md) コマンド ライン レポートでのみ有効です。|  
  
## <a name="elapsed-inclusive-values"></a>包括経過値  
 包括経過値は、コール ツリーの親関数によって呼び出された関数のインスタンスの呼び出し履歴に存在していた時間を示します。 この時間には、関数によって呼び出された子関数で費やされた時間と、オペレーティング システムの呼び出し (コンテキストの切り替え、入出力操作など) で費やされた時間が含まれます。  
  
|Column|説明|  
|------------|-----------------|  
|**経過時間 (子を含む)**|このコンテキストのこの関数に対するすべての呼び出しの包括経過時間の合計。|  
|**経過時間 % (子を含む)**|プロファイル実行の包括経過時間の総計に対する、このコンテキストのこの関数に費やされた包括経過時間の総計の割合。|  
|**平均包括経過時間**|このコンテキストのこの関数の呼び出しの平均包括経過時間。|  
|**最大経過時間 (子を含む)**|このコンテキストのこの関数の呼び出しの最大包括経過時間。|  
|**最小経過時間 (子を含む)**|このコンテキストのこの関数の呼び出しの最小包括経過時間。|  
  
## <a name="elapsed-exclusive-values"></a>排他経過値  
 排他経過値は、コール ツリーの親関数によって呼び出された関数のインスタンスが関数本体でコードを実行していた時間、つまりその関数が呼び出し履歴の最上位に配置されていた時間を示します。 この時間には、オペレーティング システムの呼び出し (コンテキストの切り替え、入出力操作など) で費やされた時間が含まれます。 ただし、この関数によって呼び出された子関数で費やされた時間は含まれません。  
  
|Column|説明|  
|------------|-----------------|  
|**排他経過時間**|このコンテキストのこの関数に対するすべての呼び出しの排他経過時間の合計。|  
|**経過時間 % (関数のみ)**|プロファイル実行の排他経過時間の総計に対する、このコンテキストのこの関数に費やされた排他経過時間の総計の割合。|  
|**平均経過時間 (関数のみ)**|このコンテキストのこの関数の呼び出しの平均排他経過時間。|  
|**最大経過時間 (関数のみ)**|このコンテキストのこの関数の呼び出しの最大排他経過時間。|  
|**最小経過時間 (関数のみ)**|このコンテキストのこの関数の呼び出しの最小排他経過時間。|  
  
## <a name="application-inclusive-values"></a>アプリケーション包括値  
 アプリケーション包括値は、コール ツリーの親関数によって呼び出された関数のインスタンスが呼び出し履歴に存在していた時間を示します。 この時間には、オペレーティング システムの呼び出し (コンテキストの切り替え、入出力操作など) で費やされた時間は含まれませんが、関数によって呼び出された子関数で費やされた時間は含まれます。  
  
|Column|説明|  
|------------|-----------------|  
|**アプリケーション時間 (子を含む)**|このコンテキストのこの関数に対するすべての呼び出しのアプリケーション包括時間の合計。|  
|**アプリケーション時間 % (子を含む)**|プロファイル実行の包括経過時間の総計に対する、このコンテキストのこの関数に費やされたアプリケーション包括時間の総計の割合。|  
|**平均アプリケーション時間 (子を含む)**|このコンテキストのこの関数の呼び出しの平均アプリケーション包括時間。|  
|**最大アプリケーション時間 (子を含む)**|このコンテキストのこの関数の呼び出しの最大アプリケーション包括時間。|  
|**最小アプリケーション時間 (子を含む)**|このコンテキストのこの関数の呼び出しの最小アプリケーション包括時間。|  
  
## <a name="application-exclusive-values"></a>アプリケーション排他値  
 アプリケーション排他値は、コール ツリーの親関数によって呼び出された関数のインスタンスが関数本体でコードを直接実行していた時間、つまりその関数が呼び出し履歴の最上位に配置されていた時間を示します。 この時間には、オペレーティング システムの呼び出し (コンテキストの切り替え、入出力操作など) で費やされた時間は含まれません。 また、この関数によって呼び出された子関数で費やされた時間も含まれません。  
  
|Column|説明|  
|------------|-----------------|  
|**アプリケーション時間 (関数のみ)**|このコンテキストのこの関数に対するすべての呼び出しのアプリケーション排他時間の合計。|  
|**アプリケーション時間 % (関数のみ)**|プロファイル実行の排他経過時間の総計に対する、このコンテキストのこの関数に費やされたアプリケーション排他時間の総計の割合。|  
|**平均アプリケーション時間 (関数のみ)**|このコンテキストのこの関数の呼び出しの平均アプリケーション排他時間。|  
|**最大アプリケーション時間 (関数のみ)**|このコンテキストのこの関数の呼び出しの最大アプリケーション排他時間。|  
|**最小アプリケーション時間 (関数のみ)**|このコンテキストのこの関数の呼び出しの最小アプリケーション排他時間。|  
  
## <a name="see-also"></a>関連項目  
 [方法: レポート ビューの列をカスタマイズする](../profiling/how-to-customize-report-view-columns.md)   
 [コール ツリー ビュー](../profiling/call-tree-view-sampling-data.md)   
 [コール ツリー ビュー - インストルメンテーション](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [コール ツリー ビュー - サンプリング](../profiling/call-tree-view-dotnet-memory-sampling-data.md)


