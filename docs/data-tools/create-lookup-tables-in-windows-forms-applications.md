---
title: Windows フォーム アプリケーションでルックアップ テーブルを作成します。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7b154b970d2a738e80efa5cbf669d29bd7bae589
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756767"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows フォーム アプリケーションでルックアップ テーブルを作成します。
用語*ルックアップ テーブル*2 つの関連するデータ テーブルにバインドされているコントロールについて説明します。 この検索コントロールは、2 番目のテーブルで選択されている値に基づいて最初のテーブルからデータを表示します。

 親テーブルの主ノードをドラッグして、ルックアップ テーブルを作成することができます (から、[データ ソース ウィンドウ](add-new-data-sources.md)) に関連する子テーブル内の列に既にバインドされているフォーム上のコントロール。

 たとえば、販売データベースの `Orders` テーブルであれば、次のように使用されます。 内の各レコード、`Orders`テーブルが含まれています、 `CustomerID`、どの顧客が注文を表します。 `CustomerID` は、`Customers` テーブルの顧客レコードを指す外部キーです。 このシナリオで展開する、`Orders`テーブルに、**データ ソース**ウィンドウに、メイン ノードを設定し、**詳細**します。 次に、設定、`CustomerID`列を使用して、 <xref:System.Windows.Forms.ComboBox> (または検索バインドをサポートするその他のコントロール) をドラッグし、`Orders`フォーム上にノード。 最後に、ドラッグ、 `Customers` 、関連する列にバインドされているコントロールの上に、この場合、<xref:System.Windows.Forms.ComboBox>にバインドされている、`CustomerID`列。

## <a name="to-databind-a-lookup-control"></a>検索コントロールをデータバインドするには

1.  開く、**データソース**ウィンドウ。

    > [!NOTE]
    >  ルックアップ テーブルでは、2 つの関連するテーブルまたはオブジェクトがで使用できることが必要です、**データソース**ウィンドウ。 詳細については、次を参照してください。[データセットのリレーションシップ](relationships-in-datasets.md)します。

2.  内のノードを展開し、**データソース**ウィンドウが表示されるまで、親テーブルとすべての列、および関連する子テーブルとそのすべての列。

    > [!NOTE]
    >  子テーブルのノードは、展開可能な子ノードとして親テーブルに表示されます。

3.  子テーブルのドロップ タイプを変更する**詳細**を選択して**詳細**子テーブルのノード上のコントロール リストから。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

4.  2 つのテーブルの関連ノードを見つけます (、`CustomerID`前の例でのノード)。 ドロップ型を変更、<xref:System.Windows.Forms.ComboBox>を選択して**ComboBox**コントロール リストから。

5.  主要な子テーブル ノードをドラッグして、**データソース**ウィンドウから、フォームにします。

     説明のラベルが付いたデータ バインド コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A[データセット](../data-tools/dataset-tools-in-visual-studio.md)、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

6.  ここからメインの親テーブル ノードをドラッグ、**データ ソース**ルックアップ コントロールに直接ウィンドウ (、 <xref:System.Windows.Forms.ComboBox>)。

     これで検索バインドが確立されます。 コントロールに設定された特定のプロパティを次の表を参照してください。

    |プロパティ|設定の説明|
    |--------------|----------------------------|
    |**DataSource**|Visual Studio では、このプロパティを設定、 <xref:System.Windows.Forms.BindingSource>、コントロールにドラッグしたテーブルの作成 (ではなく、<xref:System.Windows.Forms.BindingSource>コントロールが作成されたときに作成) します。<br /><br /> 調整する必要がある場合に設定、<xref:System.Windows.Forms.BindingSource>を表示する列を含むテーブルの。|
    |**DisplayMember**|Visual Studio は、このプロパティをコントロールにドラッグするテーブルの主キーの後で、文字列データ型を含む最初の列に設定します。<br /><br /> 調整する必要がある場合は、表示する列名にこれを設定します。|
    |**ValueMember**|Visual Studio は、このプロパティを主キーに参加している最初の列、またはキーが定義されていない場合は、テーブルの最初の列に設定します。<br /><br /> 調整する必要がある場合は、表示する列を含むテーブルの主キーにこれを設定します。|
    |**SelectedValue**|Visual Studio では、このプロパティを設定から削除される元の列に、**データソース**ウィンドウ。<br /><br /> 調整する必要がある場合、関連テーブルの外部キー列に設定します。|

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)