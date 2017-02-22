---
title: "プロファイリング ツールのサンプリング データ値について | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サンプリング プロファイル方法"
  - "プロファイリング ツール, サンプリング"
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# プロファイリング ツールのサンプリング データ値について
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイル ツールの*サンプリング* プロファイル方法は、コンピューター プロセッサを設定された間隔で中断し、関数の呼び出し履歴を収集します。  *呼び出し履歴*は、プロセッサ上で実行されている関数に関する情報を格納する動的な構造です。  
  
 **要件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 プロファイラー分析は、プロセッサが対象のプロセスでコードを実行しているかどうかを判断します。  プロセッサが対象のプロセスでコードを実行していない場合、サンプルは廃棄されます。  
  
 プロセッサが対象のコードを実行している場合、プロファイラーは呼び出し履歴の各関数のサンプル カウントをインクリメントします。  サンプルが取られる時点では、呼び出し履歴の 1 つの関数だけがコードを実行しています。  履歴の他の関数は関数呼び出し階層内の親で、子が戻るのを待っています。  
  
 サンプル イベントの場合、プロファイラーは現在命令を実行している関数の*排他*サンプル カウントをインクリメントします。  排他サンプルは、関数の総 \(*包括*\) サンプル数の一部でもあるため、現在アクティブな関数の包括サンプル カウントもインクリメントされます。  
  
 プロファイラーは、呼び出し履歴にある他のすべての関数の包括サンプル カウントをインクリメントします。  
  
## 包括サンプル  
 対象の関数の実行中に収集されるサンプルの総数。  
  
 これには、関数コードの直接実行中に収集されるサンプルと、対象の関数から呼び出される子関数の実行中に収集されるサンプルが含まれます。  
  
## 排他サンプル  
 対象の関数の命令の直接実行中に収集されるサンプルの数。  
  
 排他サンプルには、対象の関数から呼び出される関数の実行中に収集されるサンプルは含まれません。  
  
## 包括パーセント  
 プロファイリング実行の包括サンプルの総数に対する、関数またはデータ範囲の包括サンプルの割合。  
  
## 排他パーセント  
 プロファイリング実行の排他サンプルの総数に対する、関数またはデータ範囲の排他サンプルの割合。  
  
## 参照  
 [方法 : 収集方法を選択する](../profiling/how-to-choose-collection-methods.md)   
 [プロファイリング ツール データの分析](../profiling/analyzing-performance-tools-data.md)