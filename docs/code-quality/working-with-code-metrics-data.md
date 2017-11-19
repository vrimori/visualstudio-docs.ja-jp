---
title: "コード メトリックス データの操作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d45f5d43819dc418b6378d34a19e6af1d8ee12
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-code-metrics-data"></a>コード メトリックス データの操作
**コード メトリックスの結果**ウィンドウには、コード メトリックス分析によって生成されるデータが表示されます。 コード メトリックス データ値の詳細については、次を参照してください。[コード メトリックス値](../code-quality/code-metrics-values.md)です。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [コード メトリックスの結果を表示します。](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [コード メトリックスの結果をフィルター処理](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [追加、削除、およびデータ列を再配置](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [クリップボードまたは Excel にデータをコピー](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [コード メトリックの結果に基づく作業項目を作成します。](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 **コード メトリックスの結果**ウィンドウは、ツールバーの上部と計算の結果を表示する列にします。  
  
|列|説明|  
|------------|-----------------|  
|**階層**|**階層**列には展開したり折りたたんだりする詳細のレベルを表示するコードの階層のツリー ビューが含まれています。 その他の列は、計算の結果を表示します。 非表示にしたり、必要に応じて、結果の列を配置できます。|  
|**保守容易性**|**保守容易性**列には、数値結果の他のアイコンが含まれています。 緑のアイコンには、保守容易性が比較的高いことを示します。 黄色のアイコンでは、中程度の保守容易性を示します。 赤のアイコンは、低の保守容易性と潜在的な問題がスポットを示します。 これらの色のインジケーターは FxCop 規則 AvoidUnmaintainableCode によって使用されている重要度のカテゴリに対応します。 このルールは、保守容易性指数が 10 では、インデックスが 20 を超える場合に、10、20、およびエラーも警告間インデックスがある場合、警告を下回る場合、エラーを発生させます。 保守容易性指数が 3 つのメトリックの合成: サイクロマティック複雑度、行のコード、および計算の複雑度。 ユニットでは、その値は表されません。|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a>コード メトリックスの結果を表示します。  
 コード メトリックスの結果を生成するときに、コード メトリックスの結果 ウィンドウが自動的に表示されます。 いつでも、ウィンドウを表示することもできます。  
  
#### <a name="to-display-the-code-metrics-results-window"></a>コード メトリックスの結果ウィンドウを表示するには  
  
-   **分析** メニューのをクリックして**Windows**  をクリックし、**コード メトリックスの結果**です。  
  
     \- または  
  
-   **ビュー**  メニューのをポイント**その他のウィンドウ** をクリックし、**コード メトリックスの結果**です。  
  
     結果が含まれていない場合でも、コード メトリックスの結果 ウィンドウが表示されます。  
  
#### <a name="to-view-code-metrics-details"></a>コード メトリックの詳細を表示するには  
  
-   コード メトリックスの結果が生成された場合のツリーを展開、**階層**列です。  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a>コード メトリックスの結果をフィルター処理  
 表示される結果をフィルター処理することができます、**コード メトリックスの結果**ウィンドウ上部のツールバーを使用します。 たとえば、65 以下の保守容易性指数のある結果のみを表示することができます。  
  
 **フィルター**  ボックスの一覧には、結果の列の名前が含まれています。 フィルターが定義されている場合、インデントと共に一覧の一番下に追加されます。 一覧には、定義された最後の 10 個のフィルターを含めることができます。  
  
#### <a name="to-filter-the-code-metrics-results"></a>コード メトリックスの結果をフィルター処理するには  
  
1.  **フィルター**一覧で、列名を選択します。  
  
2.  **Min**、表示される最小値を入力します。  
  
3.  **Max**、表示される最大値を入力します。  
  
4.  クリックして、**フィルターの適用**ボタンをクリックします。  
  
5.  結果の詳細を表示するには、階層ツリーを展開します。  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>追加、削除、およびデータ列を再配置  
 追加するか、削除の結果の列を**コード メトリックスの結果**ウィンドウです。 さらに、目的の順序で表示されるようにする、結果の列を並べ替えることができます。  
  
#### <a name="to-remove-a-column"></a>列を削除するには  
  
1.  クリックして、**列の追加/削除**ボタンをクリックします。  
  
     \- または  
  
     任意の列見出しを右クリックし、をクリックして**列の追加/削除**です。  
  
2.  **列の追加/削除**ダイアログ ボックスで、チェック ボックスをオフ列を削除し、をクリックする**OK**です。  
  
#### <a name="to-add-a-previously-removed-column"></a>以前に削除した列を追加するには  
  
1.  クリックして、**列の追加/削除**ボタンをクリックします。  
  
     \- または  
  
     任意の列見出しを右クリックし、をクリックして**列の追加/削除**です。  
  
2.  **列の追加/削除** ダイアログ ボックスで、追加し、をクリックする列のチェック ボックスを選択**OK**です。  
  
#### <a name="to-rearrange-columns"></a>列を並べ替える  
  
1.  クリックして、**列の追加/削除**ボタンをクリックします。  
  
     \- または  
  
     任意の列見出しを右クリックし、をクリックして**列の追加/削除**です。  
  
2.  **列の追加/削除** ダイアログ ボックスに移動し、上向き矢印または下向きの矢印をクリックする列を選択します。  
  
3.  希望する場所、列を配置すると、をクリックして**OK**です。  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>クリップボードまたは Excel にデータをコピー  
 選択し、各データ列の値と名前の 1 つの行を含むテキスト文字列として、コード メトリックス データの選択した行をクリップボードにコピーできます。 クリックすることも**Microsoft Excel でリストを開く**すべてのコード メトリックスの結果を Excel スプレッドシートにエクスポートするには  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>コード メトリックの結果に基づく作業項目を作成します。  
 作成することができます、[!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]に基づいている作業項目になります、**コード メトリックスの結果**ウィンドウです。 作業項目の作成時に[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]にタイトルを自動的に入力、**タイトル**下にあるフィールドとコードのメトリック データ、**履歴**タブです。  
  
 作業項目を作成する方法の詳細については、次を参照してください。[作成、作業項目 &#91; リダイレクト &#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b)です。  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>結果に基づく作業項目を作成するには  
  
1.  結果を右クリックします。  
  
2.  をポイント**作業項目の作成**、しを作成する作業項目の種類をクリック (**バグ**、**タスク**などのように) します。  
  
3.  すべての必須フィールドに情報を入力して、作業項目フォームを完了します。  
  
4.  **ファイル** メニューのをクリックして**すべて保存**作業項目を保存します。  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>結果に基づくバグを作成するには  
  
1.  選択結果をクリックします。  
  
2.  クリックして、**作業項目の作成**ボタンをクリックします。  
  
3.  すべての必須フィールドに情報を入力して、作業項目フォームを完了します。  
  
4.  **ファイル** メニューのをクリックして**すべて保存**作業項目を保存します。  
  
## <a name="see-also"></a>関連項目  
 [複雑さとマネージ コードの保守容易性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [方法 : コード メトリックス データを生成する](../code-quality/how-to-generate-code-metrics-data.md)