---
title: "コード メトリックスの結果を Visual Studio で |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/12/2017
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c259a1d303c741d4e36af46250073b0378a65f8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-code-metrics-data"></a>コード メトリックス データの操作

**コード メトリックスの結果**ウィンドウには、コード メトリックス分析によって生成されるデータが表示されます。 コード メトリックス データ値の詳細については、次を参照してください。[コード メトリックス値](../code-quality/code-metrics-values.md)です。

## <a name="displaying-code-metrics-results"></a>コード メトリックスの結果を表示します。

**コード メトリックスの結果**コード メトリックスの結果を生成するときに、ウィンドウが自動的に表示されます。 いつでも、ウィンドウを表示することもできます。

### <a name="to-display-the-code-metrics-results-window"></a>コード メトリックスの結果ウィンドウを表示するには

- **分析**] メニューの [選択**Windows** > **コード メトリックスの結果**です。

   \- または

- **ビュー** ] メニューの [選択**その他のウィンドウ** > **コード メトリックスの結果**です。

   **コード メトリックスの結果**結果が含まれていない場合でも、ウィンドウが表示されます。

### <a name="to-view-code-metrics-details"></a>コード メトリックの詳細を表示するには

コード メトリックスの結果が生成された場合のツリーを展開、**階層**列です。

## <a name="filtering-code-metrics-results"></a>コード メトリックスの結果をフィルター処理

表示される結果をフィルター処理することができます、**コード メトリックスの結果**ウィンドウ上部のツールバーを使用します。 たとえば、65 以下の保守容易性指数のある結果のみを表示することができます。

**フィルター**  ボックスの一覧には、結果の列の名前が含まれています。 フィルターが定義されている場合、インデントと共に一覧の一番下に追加されます。 一覧には、定義された最後の 10 個のフィルターを含めることができます。

### <a name="to-filter-the-code-metrics-results"></a>コード メトリックスの結果をフィルター処理するには

1.  **フィルター**一覧で、列名を選択します。

2.  **Min**、表示される最小値を入力します。

3.  **Max**、表示される最大値を入力します。

4.  クリックして、**フィルターの適用**ボタンをクリックします。

5.  結果の詳細を表示するには、階層ツリーを展開します。

## <a name="adding-removing-and-rearranging-data-columns"></a>追加、削除、およびデータ列を再配置

追加するか、削除の結果の列を**コード メトリックスの結果**ウィンドウです。 さらに、目的の順序で表示されるようにする、結果の列を並べ替えることができます。

### <a name="to-remove-a-column"></a>列を削除するには

1. クリックして、**列の追加/削除**ボタンをクリックします。

     \-任意の列見出しを右クリックし、をクリックしてまたは -**列の追加/削除**です。

1. **列の追加/削除**ダイアログ ボックスで、チェック ボックスをオフ列を削除し、をクリックする**OK**です。

### <a name="to-add-a-previously-removed-column"></a>以前に削除した列を追加するには

1. クリックして、**列の追加/削除**ボタンをクリックします。

     \- または

     任意の列見出しを右クリックし、をクリックして**列の追加/削除**です。

1. **列の追加/削除** ダイアログ ボックスで、追加し、をクリックする列のチェック ボックスを選択**OK**です。

### <a name="to-rearrange-columns"></a>列を並べ替える

1. クリックして、**列の追加/削除**ボタンをクリックします。

     \- または

     任意の列見出しを右クリックし、をクリックして**列の追加/削除**です。

1. **列の追加/削除** ダイアログ ボックスに移動し、上向き矢印または下向きの矢印をクリックする列を選択します。

1. 希望する場所、列を配置すると、をクリックして**OK**です。

## <a name="copying-data-to-the-clipboard-or-excel"></a>クリップボードまたは Excel にデータをコピー

選択し、各データ列の値と名前の 1 つの行を含むテキスト文字列として、コード メトリックス データの選択した行をクリップボードにコピーできます。 クリックすることも**Microsoft Excel で開いている選択**すべてのコード メトリックスの結果を Excel スプレッドシートにエクスポートします。

## <a name="creating-a-work-item-based-on-code-metric-results"></a>コード メトリックの結果に基づく作業項目を作成します。

作成することができます、 [Visual Studio Team Services (VSTS)](/vsts/index)に基づいている作業項目になります、**コード メトリックスの結果**ウィンドウです。 Visual Studio が自動的にタイトルを入力して、作業項目の作成時に、**タイトル**下にあるフィールドとコードのメトリック データ、**履歴**タブです。

VSTS の詳細については、作業項目を参照してください[作業項目 (VSTS)](/vsts/work/work-items/index)です。

### <a name="to-create-a-work-item-based-on-a-result"></a>結果に基づく作業項目を作成するには

1.  結果を右クリックします。

2.  をポイント**作業項目の作成**、しを作成する作業項目の種類をクリック (**バグ**、**タスク**などのように) します。

3.  すべての必須フィールドに情報を入力して、作業項目フォームを完了します。

4.  **ファイル** メニューのをクリックして**すべて保存**作業項目を保存します。

### <a name="to-create-a-bug-based-on-a-result"></a>結果に基づくバグを作成するには

1.  選択結果をクリックします。

2.  クリックして、**作業項目の作成**ボタンをクリックします。

3.  すべての必須フィールドに情報を入力して、作業項目フォームを完了します。

4.  **ファイル** メニューのをクリックして**すべて保存**作業項目を保存します。

## <a name="see-also"></a>関連項目

[コード メトリックス値](../code-quality/code-metrics-values.md)  
[方法 : コード メトリックス データを生成する](../code-quality/how-to-generate-code-metrics-data.md)