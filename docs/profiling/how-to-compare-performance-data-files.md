---
title: "方法: パフォーマンス データ ファイルを比較する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 09e16202fb1b35a48925297e35840a60b65f0488
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-compare-performance-data-files"></a>方法: パフォーマンス データ ファイルを比較する
比較 ("Diff") のレポートまたはビューを作成することで、2 つの異なるプロファイラー データ ファイル (.vsp または .vsps) の結果を比較することができます。 この比較では、相違点、パフォーマンスの低下、および、1 つのプロファイリング セッションから他のプロファイリング セッションのあいだに起きた改善点を示します。  
  
 Diff レポートは、データのテーブル ビューを表示します。 テーブルは、差分、またはベースラインからの変化を表示します。 これは、古い値、ベースライン値と、新しい分析による結果の値との違いを調べることによって計算されます。  
  
 プロファイラーのデータの比較は、コード内の関数、アプリケーション内のモジュール、行、命令ポインター (IP)、および種類に基づいて作成できます。  
  
 しきい値を設定して、ノイズを減らし、指定した量によって変更のない行のテーブル ビュー内のデータをフィルター処理することができます。  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>パフォーマンス エクスプローラーで、プロジェクトの比較ファイル ビューを作成するには  
  
1.  **パフォーマンス エクスプローラー**の **[レポート]** で、比較の初期値として使用する .vsp または .vsps レポート ファイルを選択します。  
  
2.  比較する .vsp または .vsps レポート ファイルを選択します。  
  
3.  選択したファイルのいずれかを右クリックし、**[レポートの比較]** をクリックします。  
  
### <a name="to-compare-values"></a>値を比較するには  
  
1.  [レポート ビュー] ウィンドウで **[比較レポート]** タブを選択します。  
  
2.  **[テーブル]** ドロップダウン リストで、比較する関数またはモジュールのいずれかを選択します。  
  
3.  **[列]** ドロップダウン リストで、比較する値を選択します。  
  
4.  (省略可能) **[しきい値]** の値を入力します。  
  
5.  **[適用]** をクリックします。  
  
### <a name="to-compare-report-files"></a>レポート ファイルを比較するには  
  
1.  **[分析]** メニューで **[パフォーマンス レポートの比較]** を選択します。  
  
2.  **[比較のための分析ファイルの選択]** ウィンドウで、**[ベースライン ファイル]** 分析ファイル (.vsp または .vsps) と **[比較ファイル]** (.vsp or .vsps) を探して選択します。  
  
3.  **[OK]**をクリックします。