---
title: WPF アプリケーションでルックアップ テーブルを作成します。
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 81edef642fd2d83f6bb65c01f9a1726812ba0fca
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF アプリケーションでルックアップ テーブルを作成します。
用語*ルックアップ テーブル*(とも呼ばれる、*検索バインド*) 別のテーブルの外部キー フィールドの値に基づいて 1 つのデータ テーブルからの情報を表示するコントロールについて説明します。 親テーブルの主ノードをドラッグして、ルックアップ テーブルを作成したり、オブジェクトに、**データソース**列または関連する子テーブルのプロパティに既にバインドされているコントロール ウィンドウ。

たとえば、販売データベースの `Orders` テーブルであれば、次のように使用されます。 内の各レコード、`Orders`テーブルが含まれています、`CustomerID`どの顧客が注文を発注することを示します。 `CustomerID`で顧客レコードを指す外部キー、`Customers`テーブル。 注文の一覧を表示した場合、`Orders`テーブル、可能性がありますを表示するのではなく実際の顧客名、`CustomerID`です。 顧客名がであるため、`Customers`テーブル、顧客名を表示するルックアップ テーブルを作成する必要があります。 ルックアップ テーブルの使用、`CustomerID`値で、`Orders`リレーションシップの移動を記録し、顧客名を取得します。

## <a name="to-create-a-lookup-table"></a>ルックアップ テーブルを作成するには

1.  関連データを持つデータ ソースの種類を次のいずれかをプロジェクトに追加します。

    -   データセットまたはエンティティ データ モデル。

    -   WCF データ サービス、WCF サービスまたは Web サービスです。 詳細については、次を参照してください。[する方法: データ サービスに接続する](../data-tools/how-to-connect-to-data-in-a-service.md)です。

    -   オブジェクト。 詳細については、次を参照してください。 [Visual Studio でのオブジェクトにバインド](bind-objects-in-visual-studio.md)です。

    > [!NOTE]
    >  ルックアップ テーブルを作成することができます、前に、2 つの関連するテーブルまたはオブジェクトがプロジェクトのデータ ソースとして存在する必要があります。

2.  開く、 **WPF デザイナー**、デザイナーには内の項目の有効なドロップ ターゲットのコンテナーが含まれているかどうかを確認し、**データ ソース**ウィンドウです。

     有効なドロップ ターゲットの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)です。

3.  **データ** メニューのをクリックして**データ ソースの表示**を開くには、**データソース**ウィンドウです。

4.  内のノードを展開し、**データソース**ウィンドウが表示されるまで、親テーブルまたはオブジェクトと関連する子テーブルまたはオブジェクト。

    > [!NOTE]
    >  関連する子テーブルまたはオブジェクトは、親テーブルまたはオブジェクトで拡張可能な子ノードとして表示されるノードです。

5.  子ノードのドロップダウン メニューをクリックし、選択**詳細**です。

6.  子ノードを展開します。

7.  子ノードの下の子と親のデータを関連する項目のドロップダウン メニューをクリックします。 (これは、前の例で、 **CustomerID**ノードです)。検索バインドをサポートするコントロールの種類を次のいずれかを選択します。

    -   **ComboBox**

    -   **ListBox**

    -   **ListView**

        > [!NOTE]
        >  場合、 **ListBox**または**ListView**コントロールがない一覧で、一覧にこれらのコントロールを追加することができます。 詳細については、次を参照してください。[データ ソース ウィンドウからドラッグしたときに作成するコントロールを設定](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)です。

    -   派生した任意のカスタム コントロール<xref:System.Windows.Controls.Primitives.Selector>です。

        > [!NOTE]
        >  カスタム コントロールを追加するコントロールのリストする方法に関する情報を選択するので項目の**データソース**ウィンドウを参照してください[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)です。

8.  子ノードをドラッグして、**データソース**ウィンドウから WPF デザイナーでのコンテナーにします。 (子ノードは、前の例で、 **Orders**ノードです)。

     Visual Studio では、ドラッグした項目ごとに新しいデータ バインド コントロールを作成する XAML を生成します。 XAML も新しく追加<xref:System.Windows.Data.CollectionViewSource>子テーブルまたはオブジェクトのドロップ ターゲットのリソースにします。 一部のデータ ソースでは、Visual Studio には、テーブルまたはオブジェクトにデータを読み込むコードも生成されます。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)です。

9. 親ノードをドラッグして、**データ ソース**ウィンドウから先ほど作成した検索バインド コントロールにします。 (前の例では、親ノードが、**顧客**ノード)。

     Visual Studio では、照合バインディングを構成するコントロールのいくつかのプロパティを設定します。 次の表は、Visual Studio によって変更されるプロパティを一覧表示します。 かどうか、必要に応じて変更できます、XAML またはこれらのプロパティ、**プロパティ**ウィンドウです。

    |プロパティ|設定の説明|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|このプロパティは、コレクションまたはコントロールに表示されるデータの取得に使用されるバインディングを指定します。 Visual Studio では、このプロパティを設定、<xref:System.Windows.Data.CollectionViewSource>親データをコントロールにドラッグします。|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|このプロパティは、コントロールに表示されるデータ項目のパスを指定します。 Visual Studio では、主キーの後、文字列データ型を持つ最初の列または親データ内のプロパティをこのプロパティを設定します。<br /><br /> 親データ内の別の列またはプロパティを表示する場合は、別のプロパティのパスにこのプロパティを変更します。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio では、このプロパティを列または子データをデザイナーにドラッグした先のプロパティにバインドします。 これは、親データへの外部キーです。|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio では、列のパス、または、親データへの外部キーは、子のデータのプロパティをこのプロパティを設定します。|

## <a name="see-also"></a>関連項目

- [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)
- [チュートリアル: WPF アプリケーションでの関連データの表示](../data-tools/display-related-data-in-wpf-applications.md)