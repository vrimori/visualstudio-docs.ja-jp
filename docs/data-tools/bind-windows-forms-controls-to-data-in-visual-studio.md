---
title: Windows フォーム コントロールをデータにバインドする
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c9acd074eb1d4ac73ca0f905376f22f6e2e11b08
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53897725"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Visual Studio でのデータへの Windows フォーム コントロールのバインド

データを Windows フォームにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 これらのデータ バインド コントロールを作成するから項目をドラッグ、**データソース**Visual Studio での Windows フォーム デザイナー ウィンドウ。

![データ ソースのドラッグ操作](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> 場合、**データソース**ウィンドウが表示されないを選択して開くことができます**ビュー** > **その他の Windows** > **データ ソース**、またはキーを押して**Shift**+**Alt**+**D**します。 表示する Visual Studio で開くプロジェクトがあります、**データソース**ウィンドウ。

項目をドラッグする前にバインドするコントロールの種類を設定できます。 自体、または個々 の列にテーブルを選択するかどうかに応じて異なる値が表示されます。  カスタム値を設定することもできます。 表については、**詳細**各列が個別のコントロールにバインドされていることを意味します。

![データ ソースを DataGridView にバインドします。](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource と BindingNavigator コントロール

<xref:System.Windows.Forms.BindingSource> コンポーネントは 2 つの目的で利用できます。 最初に、コントロールのデータをバインドするときに、抽象化レイヤーを提供します。 フォームのコントロールにバインドされます、<xref:System.Windows.Forms.BindingSource>データ ソースへの直接の代わりにコンポーネント。 また、オブジェクトのコレクションを管理できます。 <xref:System.Windows.Forms.BindingSource> に型を追加すると、その型の一覧が作成されます。

<xref:System.Windows.Forms.BindingSource> コンポーネントの詳細については、次のトピックを参照してください。

- [BindingSource コンポーネント](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource コンポーネントの概要](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource コンポーネント アーキテクチャ](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator コントロール](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)Windows アプリケーションで表示されるデータを移動するためのユーザー インターフェイスを提供します。

## <a name="bind-to-data-in-a-datagridview-control"></a>DataGridView コントロールでデータをバインドします。

[DataGridView コントロール](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)、テーブル全体がその 1 つのコントロールにバインドします。 ドラッグすると、 **DataGridView**レコードを移動するためのツール ストリップをフォームに (<xref:System.Windows.Forms.BindingNavigator>) も表示されます。 [DataSet](../data-tools/dataset-tools-in-visual-studio.md)、[TableAdapter](../data-tools/create-and-configure-tableadapters.md)、<xref:System.Windows.Forms.BindingSource>、<xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。 次の図に、 [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) Customers テーブルには、Orders テーブルにリレーションシップが含まれているためにも追加されます。 これらの変数が宣言されたすべての自動生成されたコード フォーム クラスのプライベート メンバーとして。 塗りつぶしの自動生成されたコード、 **DataGridView**にある、`Form_Load`イベント ハンドラー。 データベースを更新するデータを保存するためのコードにある、`Save`のイベント ハンドラー、 **BindingNavigator**します。 移動したり、必要に応じてこのコードを変更します。

![BindingNavigator を含む GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

動作をカスタマイズすることができます、 **DataGridView**と**BindingNavigator**ごとの右上隅のスマート タグをクリックしています。

![DataGridView コントロールとバインドのナビゲーターのスマート タグ](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

コントロール、アプリケーション ニーズがない場合内から利用できる、**データソース**ウィンドウ、コントロールを追加することができます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。

項目をドラッグすることも、**データ ソース**既にデータにコントロールをバインドするフォーム上のコントロールにウィンドウ。 データに既にバインドされているコントロールには、そのデータ バインドは、最も最近ドラッグされた項目にリセットがあります。 有効なドロップ ターゲットにするには、コントロールにから上にドラッグした項目の基になるデータ型を表示することは、**データソース**ウィンドウ。 などのデータ型を持つ項目のドラッグを有効ながない<xref:System.DateTime>上に、<xref:System.Windows.Forms.CheckBox>ため、<xref:System.Windows.Forms.CheckBox>日付を表示することはできません。

## <a name="bind-to-data-in-individual-controls"></a>個々 のコントロールでデータをバインドします。

データ ソースをバインドすると**詳細**データセット内の各列は個別のコントロールにバインドします。

![詳細へのデータ ソースをバインドします。](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> 前の図に、Orders テーブルからではなく、Customers テーブルの Orders プロパティからドラッグしてください。 バインドして、`Customer.Orders`で行われたプロパティのナビゲーション コマンド、 **DataGridView**詳細コントロールにすぐに反映されます。 Orders テーブルからドラッグした場合、コントロールは、データセットにもバインドが、それらはないと同期できません、 **DataGridView**します。

次の図は、既定の Customers テーブルに Orders プロパティにバインドした後、フォームに追加されるデータ バインド コントロール**詳細**で、**データソース**ウィンドウ。

![Orders テーブルな詳細にバインドされています。](../data-tools/media/raddata-orders-table-bound-to-details.png)

各コントロールがスマート タグを持つことにも注意してください。 このタグは、そのコントロールのみに適用されるカスタマイズを使用できます。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows フォーム (.NET Framework) におけるデータ バインディング](/dotnet/framework/winforms/windows-forms-data-binding)