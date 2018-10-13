---
title: パフォーマンス ツール データの保存とエクスポート | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2eec24927f7e5b8897df988a51fb87f469088e0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236042"
---
# <a name="saving-and-exporting-performance-tools-data"></a>パフォーマンス ツール データの保存とエクスポート
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックでは、パフォーマンス データ ファイルを保存およびエクスポートする方法について説明します。  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> 方法: 分析されたレポート ファイルとしてパフォーマンス データ ファイルを保存する  
 プロファイル データ (.vsp) ファイルのフィルター処理済みビューまたはフィルター処理なしビューは、分析されたレポート (.vsps) ファイルとして保存することができます。 分析されたレポート ファイルは、[レポート ビュー] ウィンドウで表示することができ、ファイルのサイズは、元の .vsp ファイルよりもかなり小さくなります。 ただし、.vsps ファイルのデータにフィルターを適用することはできません。 統合開発環境 (IDE) でファイルを開かなくても、パフォーマンス エクスプ ローラーで、分析されたレポート ファイルを作成することができます。あるいは、.vsp ファイルを開き、フィルター処理してから、その結果を保存することもできます。  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>分析されたパフォーマンス レポートをパフォーマンス エクスプ ローラーで保存するには  
  
1.  **[レポート]** で、分析するプロファイル データ ファイルを右クリックして、**[分析されたものを保存]** をクリックします。  
  
2.  **[分析されたデータの保存]** ダイアログ ボックスで、ディレクトリを指定し、ファイル名を入力します。  
  
3.  **[保存]** をクリックします。  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>[レポート ビュー] ウィンドウで、パフォーマンス レポートを保存して分析するには  
  
1.  [レポート ビュー] ウィンドウで、プロファイル データ (.vsp) ファイルを開きます。  
  
2.  (省略可能) データにフィルターを適用します。 詳しくは、「[パフォーマンス レポート ビュー フィルター](../profiling/performance-report-view-filter.md)」をご覧ください。  
  
3.  [レポート ビュー] ウィンドウのツールバーで、**[分析されたものを保存]** をクリックします。  
  
4.  **[分析されたデータの保存]** ダイアログ ボックスで、ディレクトリを指定し、ファイル名を入力します。  
  
5.  **[保存]** をクリックします。  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>方法: プロファイリング ツールのレポートを .Xml または .Csv ファイルにエクスポートする  
 1 つまたは複数のレポート ビューを、.vsp ファイルまたは .vsps プロファイル データ ファイルから、コンマ区切りファイルまたは XML ファイルとしてエクスポートすることができます。 [レポート ビュー] ウィンドウでエクスポートする前にデータをフィルター処理することも、**[パフォーマンス エクスプ ローラー]** ウィンドウからデータ ファイル全体のレポート ビューをエクスポートすることもできます。  
  
> [!NOTE]
>  さらに、[レポート ビュー] ウィンドウで選択した行をタブ区切り値としてコピーして貼り付けることもできます。  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>[パフォーマンス エクスプ ローラー] ウィンドウから、パフォーマンス レポートをエクスポートするには  
  
1.  **[パフォーマンス エクスプローラー]** で、レポートを選択し、右クリックして **[エクスポート]** を選択します。  
  
     **[レポートのエクスポート]** ダイアログ ボックスが表示されます。  
  
2.  エクスポートするレポート ビューを選択します。  
  
3.  **[レポートに付けるプレフィックス]** で、レポート名に追加するプレフィックスを指定します。  
  
4.  **[エクスポートされたレポートの場所]** で、ディレクトリを指定します。  
  
5.  **エクスポートされたレポート形式**を選択します (コンマ区切り) (*.csv) または XML データ (\*.xml)。  
  
6.  **[エクスポート]** をクリックします。  
  
     各レポート ビューは、\<プレフィックス>_\<レポート ビュー名>.\<csv&#124;xml> という名前の別のファイルに保存されます  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>[レポート ビュー] ウィンドウからパフォーマンス レポートをエクスポートするには  
  
1.  [レポート ビュー] ウィンドウで .vsp ファイルを開きます。  
  
2.  (省略可能) データにフィルターを適用します。 詳しくは、「[パフォーマンス レポート ビュー フィルター](../profiling/performance-report-view-filter.md)」をご覧ください。  
  
3.  [レポート ビュー] ウィンドウのツールバーで **[レポートのエクスポート]** をクリックします。  
  
4.  エクスポートするレポート ビューを選択します。  
  
5.  **[レポートに付けるプレフィックス]** で、レポート名に追加するプレフィックスを指定します。  
  
6.  **[エクスポートされたレポートの場所]** で、ディレクトリを指定します。  
  
7.  **エクスポートされたレポート形式**を選択します (コンマ区切り) (*.csv) または XML データ (\*.xml)。  
  
8.  **[エクスポート]** をクリックします。  
  
     各レポート ビューは、\<プレフィックス>_\<レポート ビュー名>.\<csv&#124;xml> という名前の別のファイルに保存されます  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス エクスプ ローラー](../profiling/performance-explorer.md)   
 [パフォーマンス ツール データの分析](../profiling/analyzing-performance-tools-data.md)   
 [パフォーマンス データ ファイルの比較](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



