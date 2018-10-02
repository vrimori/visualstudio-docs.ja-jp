---
title: コード メトリックス データの操作 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: 954b81dfe738ebd0de1f8aa38cb4975a05333feb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544307"
---
# <a name="working-with-code-metrics-data"></a>コード メトリックス データの操作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コード メトリックス データを扱う](https://docs.microsoft.com/visualstudio/code-quality/working-with-code-metrics-data)します。  
  
**コード メトリックスの結果**ウィンドウには、コード メトリックスの分析によって生成されるデータが表示されます。 コード メトリックス データの値の詳細については、次を参照してください。[コード メトリックス値](../code-quality/code-metrics-values.md)します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [コード メトリックスの結果を表示します。](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [コード メトリックスの結果をフィルター処理](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [追加、削除、およびデータ列の並べ替え](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [クリップボードまたは Excel へのデータのコピー](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [コード メトリックの結果に基づいて作業項目を作成します。](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 **コード メトリックスの結果**ウィンドウの一番上と計算の結果を表示する列のツールバーにします。  
  
|Column|説明|  
|------------|-----------------|  
|**階層**|**階層**列には展開したり折りたたんだりする詳細のレベルを表示するコードの階層構造のツリー ビューが含まれています。 その他の列は、計算結果を表示します。 非表示にしたり、必要に応じて、結果の列を配置できます。|  
|**保守容易性**|**保守容易性**列にはだけでなく、数値の結果アイコンが含まれています。 緑色のアイコンには、保守容易性が比較的高いことを示します。 黄色のアイコンでは、中程度の保守容易性を示します。 赤のアイコンは、低の保守容易性と潜在的な問題がスポットを示します。 これらのカラー インジケーターは、FxCop ルール AvoidUnmaintainableCode によって使用される重要度カテゴリに対応します。 このルールでは、保守容易性指数が 10、インデックスがインデックスが 20 より大きい場合に 10、20 とどちらも、エラー、警告の場合、警告を下回る場合、エラーが発生します。 保守容易性指数は、3 つのメトリックの合成: サイクロマティック複雑度、コード、および計算の複雑さの行。 ユニットでは、その値は表されません。|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a> コード メトリックスの結果を表示します。  
 コード メトリックスの結果を生成するときに、コード メトリックスの結果ウィンドウが自動的に表示されます。 いつでも、ウィンドウを表示することもできます。  
  
#### <a name="to-display-the-code-metrics-results-window"></a>コード メトリックスの結果ウィンドウを表示するには  
  
-   **分析** メニューのをクリックして**Windows**  をクリックし、**コード メトリックスの結果**します。  
  
     \- または -  
  
-   **ビュー**メニューで、**その他の Windows**  をクリックし、**コード メトリックスの結果**します。  
  
     結果が含まれていない場合でも、コード メトリックスの結果ウィンドウが表示されます。  
  
#### <a name="to-view-code-metrics-details"></a>コード メトリックの詳細を表示するには  
  
-   コード メトリックスの結果が生成された場合のツリーを展開、**階層**列。  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a> コード メトリックスの結果をフィルター処理  
 表示される結果をフィルター処理することができます、**コード メトリックスの結果**ウィンドウ上部にあるツールバーを使用します。 たとえば、65 以下の保守容易性指数のある結果のみを表示します。  
  
 **フィルター**ドロップダウン ボックスに結果列の名前が含まれています。 フィルターが定義されている場合、インデントと共に一覧の一番下に追加されます。 一覧には、定義された最後の 10 個のフィルターを含めることができます。  
  
#### <a name="to-filter-the-code-metrics-results"></a>コード メトリックスの結果をフィルター処理するには  
  
1.  **フィルター**一覧で、列名を選択します。  
  
2.  **Min**、表示される最小値を入力します。  
  
3.  **最大**、表示される最大値を入力します。  
  
4.  をクリックして、**フィルターの適用**ボタンをクリックします。  
  
5.  結果の詳細を表示するには、階層ツリーを展開します。  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> 追加、削除、およびデータ列の並べ替え  
 追加したり削除からの列の結果、**コード メトリックスの結果**ウィンドウ。 さらに、希望する順序で表示されるので、結果の列を並べ替えることができます。  
  
#### <a name="to-remove-a-column"></a>列を削除するには  
  
1.  をクリックして、**列の追加/削除**ボタンをクリックします。  
  
     \- または -  
  
     任意の列見出しを右クリックし、をクリックし、**列の追加/削除**します。  
  
2.  **列の追加/削除**ダイアログ ボックスで、チェック ボックスをオフ列の削除 をクリックする**OK**します。  
  
#### <a name="to-add-a-previously-removed-column"></a>以前に削除した列を追加するには  
  
1.  をクリックして、**列の追加/削除**ボタンをクリックします。  
  
     \- または -  
  
     任意の列見出しを右クリックし、をクリックし、**列の追加/削除**します。  
  
2.  **列の追加/削除** ダイアログ ボックスをクリックして追加する列のチェック ボックスをオン**OK**します。  
  
#### <a name="to-rearrange-columns"></a>列を並べ替える  
  
1.  をクリックして、**列の追加/削除**ボタンをクリックします。  
  
     \- または -  
  
     任意の列見出しを右クリックし、をクリックし、**列の追加/削除**します。  
  
2.  **列の追加/削除** ダイアログ ボックスに移動し、上矢印または下矢印をクリックする列を選択します。  
  
3.  目的の場所列を配置すると、クリックして**OK**します。  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> クリップボードまたは Excel へのデータのコピー  
 選択し、各データ列の値と名前の 1 つの行を含むテキスト文字列として選択した行のコード メトリックス データをクリップボードにコピーできます。 クリックすることもできます**Microsoft Excel でリストを開く**すべてのコード メトリックスの結果を Excel のスプレッドシートにエクスポートするには  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> コード メトリックの結果に基づいて作業項目を作成します。  
 作成することができます、[!INCLUDE[esprfound](../includes/esprfound-md.md)]に基づいている作業項目の結果、**コード メトリックスの結果**ウィンドウ。 作業項目が作成されると、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]にタイトルを自動的に入力、**タイトル**フィールドとコード メトリック データの下で、**履歴** タブ。  
  
 作業項目を作成する方法の詳細については、次を参照してください。[作業項目を作成&#91;リダイレクト&#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b)します。  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>結果に基づく作業項目を作成するには  
  
1.  結果を右クリックします。  
  
2.  をポイント**作業項目の作成**、作成する作業項目の種類をクリックして (**バグ**、**タスク**などのように) します。  
  
3.  すべての必須フィールドに入力して、作業項目フォームを完了します。  
  
4.  **ファイル** メニューのをクリックして**すべて保存**作業項目を保存します。  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>結果に基づくバグを作成するには  
  
1.  選択結果をクリックします。  
  
2.  をクリックして、**作業項目の作成**ボタンをクリックします。  
  
3.  すべての必須フィールドに入力して、作業項目フォームを完了します。  
  
4.  **ファイル** メニューのをクリックして**すべて保存**作業項目を保存します。  
  
## <a name="see-also"></a>関連項目  
 [複雑さとマネージ コードの保守性を測定します。](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [方法 : コード メトリックス データを生成する](../code-quality/how-to-generate-code-metrics-data.md)



