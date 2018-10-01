---
title: サンプリング データ値について | Microsoft Docs
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
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60087d2788cd4b46b77d670cf430bf0e0198b6f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539364"
---
# <a name="understanding-sampling-data-values"></a>サンプリング データ値について
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[サンプリング データ値について](https://docs.microsoft.com/visualstudio/profiling/understanding-sampling-data-values)します。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイリング ツールの*サンプリング* プロファイル方式では、設定された間隔でコンピューター プロセッサに割り込み、関数の呼び出し履歴を収集します。 *呼び出し履歴*は、プロセッサ上で実行されている関数に関する情報を格納する動的な構造です。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 プロファイラー分析は、プロセッサがターゲット プロセス内のコードを実行しているかどうかを判別します。 プロセッサがターゲット プロセス内のコードを実行していない場合、サンプルは破棄されます。  
  
 プロセッサがターゲット コードを実行している場合、プロファイラーは、呼び出し履歴の各関数のサンプル カウントをインクリメントします。 サンプルの取得時には、呼び出し履歴上の 1 つの関数のみがコードを実行中です。 スタック上の他の関数は、関数呼び出し階層内の親であり、子の復帰を待機しています。  
  
 プロファイラーは、サンプル イベントに対して、現在命令を実行している関数の*排他*サンプル数をインクリメントします。 排他サンプルは、関数の合計 (*包括*) サンプル数にも含まれるため、現在アクティブな関数の包括サンプル数もインクリメントされます。  
  
 プロファイラーは、呼び出し履歴上のすべての関数の包括サンプル数をインクリメントします。  
  
## <a name="inclusive-samples"></a>包括サンプル  
 対象の関数の実行中に収集されるサンプルの合計数。  
  
 これには、関数コードを直接実行しているときに収集されたサンプルと、対象の関数によって呼び出された子関数の実行中に収集されたサンプルが含まれます。  
  
## <a name="exclusive-samples"></a>排他サンプル  
 対象の関数の命令を直接実行中しているときに収集されたサンプルの数。  
  
 排他サンプルには、対象の関数によって呼び出された関数の実行中に収集されたサンプルは含まれません。  
  
## <a name="inclusive-percent"></a>包括 (%)  
 関数またはデータ範囲の包括サンプル数である、プロファイリング実行での包括サンプル合計数の割合。  
  
## <a name="exclusive-percent"></a>排他 (%)  
 関数またはデータ範囲の排他サンプル数である、プロファイリング実行での排他サンプル合計数の割合。  
  
## <a name="see-also"></a>関連項目  
 [方法: 収集方法を選択する](../profiling/how-to-choose-collection-methods.md)   
 [パフォーマンス ツール データの分析](../profiling/analyzing-performance-tools-data.md)



