---
title: WPF アプリケーションでルックアップ テーブルを作成する
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ed448c44b46098a6ccaa7ac1194acd76bd64c089
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988910"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF アプリケーションでルックアップ テーブルを作成する

用語*ルックアップ テーブル*(とも呼ばれる、*ルックアップ バインディング*) 別のテーブルの外部キー フィールドの値に基づいて 1 つのデータ テーブルからの情報を表示するコントロールについて説明します。 親テーブルの主ノードをドラッグして、ルックアップ テーブルを作成したり、オブジェクト、**データソース**列または関連する子テーブルのプロパティに既にバインドされているコントロールにウィンドウ。

たとえば、販売データベースの `Orders` テーブルであれば、次のように使用されます。 内の各レコード、`Orders`テーブルが含まれています、`CustomerID`どの顧客が注文を示します。 `CustomerID`で顧客レコードを参照する外部キー、`Customers`テーブル。 注文の一覧を表示すると、`Orders`テーブルの代わりに実際の顧客名を表示する可能性があります、`CustomerID`します。 顧客名いるため、`Customers`テーブル、顧客の名前を表示するルックアップ テーブルを作成する必要があります。 参照テーブルの使用、`CustomerID`値、`Orders`リレーションシップの移動を記録し、顧客名を返します。

## <a name="to-create-a-lookup-table"></a>ルックアップ テーブルを作成するには

1.  プロジェクトに関連するデータを使用してデータ ソースの種類は、次のいずれかを追加します。

    -   データセットまたはエンティティ データ モデル。

    -   WCF データ サービス、WCF サービスまたは web サービス。 詳細については、「[方法 :サービスのデータに接続する](../data-tools/how-to-connect-to-data-in-a-service.md)

    -   オブジェクト。 詳細については、次を参照してください。 [Visual Studio でのオブジェクトにバインド](bind-objects-in-visual-studio.md)します。

    > [!NOTE]
    > ルックアップ テーブルを作成するには、2 つの関連するテーブルまたはオブジェクトがプロジェクトのデータ ソースとして存在する必要があります。

2.  開く、 **WPF デザイナー**、デザイナーには内の項目の有効なドロップ先であるコンテナーが含まれているかどうかを確認して、**データソース**ウィンドウ。

     有効なドロップ ターゲットの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)します。

3.  **[データ]** メニューの **[データ ソースの表示]** をクリックして **[データ ソース]** ウィンドウを開きます。

4.  内のノードを展開し、**データソース**ウィンドウで、親テーブルまたはオブジェクトと関連する子テーブルまたはオブジェクトが見つかるまで。

    > [!NOTE]
    > 関連する子テーブルまたはオブジェクトは、親テーブルまたはオブジェクトで拡張可能な子ノードとして表示されるノードです。

5.  子ノードは、ドロップダウン メニューをクリックし、**詳細**します。

6.  子ノードを展開します。

7.  子ノードの下の子と親のデータを関連する項目のドロップダウン メニューをクリックします。 (前の例では、 **CustomerID**ノードです)。次の種類の参照のバインディングをサポートするコントロールのいずれかを選択します。

    -   **ComboBox**

    -   **ListBox**

    -   **ListView**

        > [!NOTE]
        > 場合、 **ListBox**または**ListView**コントロールは表示されません一覧で、一覧にこれらのコントロールを追加することができます。 詳しくは、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

    -   派生した任意のカスタム コントロール<xref:System.Windows.Controls.Primitives.Selector>します。

        > [!NOTE]
        > 内の項目のカスタム コントロールをコントロールのリストを追加する方法についての情報を選択できます、**データソース**ウィンドウを参照してください[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。

8.  子ノードをドラッグして、**データソース**ウィンドウから WPF デザイナーでのコンテナーにします。 (前の例では、子ノードは、**注文**ノードです)。

     Visual Studio には、ドラッグした項目ごとに新しいデータ バインド コントロールを作成する XAML が生成されます。 XAML も新しく追加<xref:System.Windows.Data.CollectionViewSource>子テーブルまたはドロップ先のリソースへのオブジェクト。 Visual Studio には、一部のデータ ソースのテーブルまたはオブジェクトにデータを読み込むコードも生成されます。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)します。

9. 親ノードをドラッグして、**データ ソース**先ほど作成した検索バインド コントロールにウィンドウ。 (前の例では、親ノードが、**顧客**ノード)。

     Visual Studio では、検索バインドを構成するコントロールのいくつかのプロパティを設定します。 次の表は、Visual Studio を変更するプロパティを一覧表示します。 かどうか、必要に応じて変更できます、XAML またはこれらのプロパティ、**プロパティ**ウィンドウ。

    |プロパティ|設定の説明|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|このプロパティは、コレクションまたはコントロールに表示されるデータを取得するために使用するバインディングを指定します。 Visual Studio では、このプロパティを設定、<xref:System.Windows.Data.CollectionViewSource>親データをコントロールにドラッグします。|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|このプロパティは、コントロールに表示されるデータ項目のパスを指定します。 Visual Studio は、文字列データ型を持つ、主キーの後、最初の列または親のデータのプロパティにこのプロパティを設定します。<br /><br /> 親データで別々 の列またはプロパティを表示する場合は、別のプロパティのパスにこのプロパティを変更します。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio は、このプロパティを列または子データをデザイナーにドラッグした先のプロパティにバインドします。 これは、親データへの外部キーです。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio では、列のパス、または親データへの外部キーは、子のデータのプロパティをこのプロパティを設定します。|

## <a name="see-also"></a>関連項目

- [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)
- [チュートリアル: WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)