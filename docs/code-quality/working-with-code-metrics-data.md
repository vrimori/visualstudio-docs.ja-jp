---
title: コード メトリックス ウィンドウ
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31690ccc3c2f32b4abb2ff9fefcc268c83977595
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856320"
---
# <a name="use-the-code-metrics-results-window"></a>コード メトリックスの結果 ウィンドウを使用します。

**コード メトリックスの結果**ウィンドウには、コード メトリックスの分析によって生成されるデータが表示されます。 コード メトリックス データの値の詳細については、次を参照してください。[コード メトリックス値](../code-quality/code-metrics-values.md)します。

## <a name="display-code-metrics-results"></a>コード メトリックスの結果を表示します。

**コード メトリックスの結果**コード メトリックスの結果を生成するときに、ウィンドウが自動的に表示されます。 いつでも、ウィンドウを表示することもできます。

次の順序でメニューのいずれかを使用して、コード メトリックスの結果ウィンドウを表示できます。

- **分析**] メニューの [選択**Windows** > **コード メトリックスの結果**します。

- **ビュー** ] メニューの [選択**その他の Windows** > **コード メトリックスの結果**します。

**コード メトリックスの結果**結果が含まれていない場合でも、ウィンドウが開きます。

### <a name="to-view-code-metrics-details"></a>コード メトリックの詳細を表示するには

コード メトリックスの結果が生成された場合のツリーを展開、**階層**列。

## <a name="filter-code-metrics-results"></a>コード メトリックスの結果をフィルター処理します。

表示される結果をフィルター処理することができます、**コード メトリックスの結果**ウィンドウ上部にあるツールバーを使用します。 たとえば、65 以下の保守容易性指数のある結果のみを表示します。

**フィルター**ドロップダウン ボックスに結果列の名前が含まれています。 フィルターが定義されている場合、インデントと共に一覧の一番下に追加されます。 一覧には、定義された 10 個までのフィルターを含めることができます。

### <a name="to-filter-the-code-metrics-results"></a>コード メトリックスの結果をフィルター処理するには

1.  **フィルター**一覧で、列名を選択します。

2.  **Min**、表示される最小値を入力します。

3.  **最大**、表示される最大値を入力します。

4.  をクリックして、**フィルターの適用**ボタンをクリックします。

5.  結果の詳細を表示するには、階層ツリーを展開します。

## <a name="add-remove-and-rearrange-data-columns"></a>追加、削除、およびデータ列を並べ替える

追加したり削除からの列の結果、**コード メトリックスの結果**ウィンドウ。 さらに、希望する順序で表示されるので、結果の列を並べ替えることができます。

### <a name="add-or-remove-a-column"></a>追加または列を削除します。

1. をクリックして、**列の追加/削除**ボタンをクリックすると、または任意の列見出しを右クリックし、クリックして**列の追加/削除**します。

1. **列の追加/削除**の追加または削除、および選択する列のチェック ボックス ダイアログ ボックスをオンまたはオフ**OK**します。

### <a name="rearrange-columns"></a>列を並べ替える

1. をクリックして、**列の追加/削除**ボタンをクリックします。

1. **列の追加/削除** ダイアログ ボックスに移動し、上矢印または下矢印を選択する列を選択します。

1. 目的の場所列を配置すると、選択**OK**します。

## <a name="copy-data-to-the-clipboard-or-excel"></a>クリップボードまたは Excel にデータをコピーします。

選択し、各データ列の値と名前の 1 つの行を含むテキスト文字列として選択した行のコード メトリックス データをクリップボードにコピーできます。 クリックすることもできます**Microsoft Excel で開いて選択**すべてのコード メトリックスの結果を Excel のスプレッドシートにエクスポートします。

## <a name="create-a-work-item-based-on-code-metric-results"></a>コード メトリックの結果に基づいて作業項目を作成します。

作成することができます、 [Azure ボード](/azure/devops/boards/index?view=vsts)に基づいている作業項目の結果、**コード メトリックスの結果**ウィンドウ。 Visual Studio が自動的にタイトルを入力して、作業項目が作成されたときに、**タイトル**フィールドとコード メトリック データの下で、**履歴**タブ。

Azure のボードの詳細については、作業項目を参照してください[作業項目](/azure/devops/boards/work-items/index?view=vsts)します。

### <a name="to-create-a-work-item-based-on-a-result"></a>結果に基づく作業項目を作成するには

1.  結果を右クリックします。

2.  をポイント**作業項目の作成**、作成する作業項目の種類をクリックして (**バグ**、**タスク**などのように) します。

3.  すべての必須フィールドに入力して、作業項目フォームを完了します。

4.  **ファイル** メニューのをクリックして**すべて保存**作業項目を保存します。

### <a name="to-create-a-bug-based-on-a-result"></a>結果に基づくバグを作成するには

1.  選択結果をクリックします。

2.  をクリックして、**作業項目の作成**ボタンをクリックします。

3.  すべての必須フィールドに入力して、作業項目フォームを完了します。

4.  **ファイル** メニューのをクリックして**すべて保存**作業項目を保存します。

## <a name="see-also"></a>関連項目

- [コード メトリックス値](../code-quality/code-metrics-values.md)
- [方法: コード メトリックス データを生成します。](../code-quality/how-to-generate-code-metrics-data.md)