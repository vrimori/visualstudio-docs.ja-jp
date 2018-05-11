---
title: Visual Studio でのデータを Windows フォーム コントロールをバインドします。
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e89a919f6f93dc70f9417a23430c960f03cf92bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Visual Studio でのデータを Windows フォーム コントロールをバインドします。
データを Windows フォームにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 これらのデータ バインド コントロールを作成するから項目をドラッグすることができます、**データソース**ウィンドウから Visual Studio での Windows フォーム デザイナーにします。

![データ ソースはドラッグ操作](../data-tools/media/raddata-data-source-drag-operation.png "raddata データ ソースはドラッグ操作")

項目をドラッグすると、前にバインドするコントロールの種類を設定することができます。 自体、または個々 の列にテーブルを選択するかどうかに応じて異なる値が表示されます。  カスタム値を設定することもできます。 表については、"Details"は各列が個別のコントロールにバインドされていることを意味します。

![データ ソースをバインドする DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "DataGridView を raddata バインド データ ソース")

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource と BindingNavigator コントロール
<xref:System.Windows.Forms.BindingSource> コンポーネントは 2 つの目的で利用できます。 最初に、コントロールをデータにバインドするときに、抽象化レイヤーを提供します。 フォーム上のコントロールにバインドされます、<xref:System.Windows.Forms.BindingSource>コンポーネントの代わりに、データ ソースを直接です。 また、オブジェクトのコレクションを管理できます。 <xref:System.Windows.Forms.BindingSource> に型を追加すると、その型の一覧が作成されます。

<xref:System.Windows.Forms.BindingSource> コンポーネントの詳細については、次のトピックを参照してください。

-   [BindingSource コンポーネント](/dotnet/framework/winforms/controls/bindingsource-component)

-   [BindingSource コンポーネントの概要](/dotnet/framework/winforms/controls/bindingsource-component-overview)

-   [BindingSource コンポーネント アーキテクチャ](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator コントロール](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)Windows アプリケーションによって表示されるデータを移動するためのユーザー インターフェイスを提供します。

## <a name="bind-to-data-in-a-datagridview-control"></a>DataGridView コントロール内のデータにバインドします。
[DataGridView コントロール](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)、テーブル全体がその 1 つのコントロールにバインドされています。 レコードを移動するためのツールがストリップ DataGridView をフォームにドラッグすると、(<xref:System.Windows.Forms.BindingNavigator>) も表示されます。 A[データセット](../data-tools/dataset-tools-in-visual-studio.md)、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。 次の図では、Customers テーブルには、Orders テーブルにリレーションシップが含まれているために場合にも、TableAdapterManager が追加されます。 これらの変数は、すべての自動生成されたコードとして宣言フォーム クラスのプライベート メンバー。 DataGridView を塗りつぶすときの自動生成されたコードは、form_load イベント ハンドラーに格納されます。 データベースを更新するデータを保存するためのコードは、BindingNavigator の保存のイベント ハンドラーに格納されます。 移動したり、必要に応じてこのコードを変更することができます。

![BindingNavigator GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata BindingNavigator GridView")

それぞれの右上隅のスマート タグをクリックして、DataGridView コントロールと BindingNavigator の動作をカスタマイズできます。

![DataGridView コントロールとバインドのナビゲーターのスマート タグ](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView とバインドのナビゲーターのスマート タグ")

コントロール、アプリケーションが必要がない場合内から使用可能、**データ ソース**ウィンドウ、コントロールを追加することができます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)です。

項目をドラッグすることも、**データ ソース**ウィンドウからコントロールをデータにバインドするためのフォームにコントロールにします。 データに既にバインドされているコントロールには、そのデータを最も最近ドラッグされた項目にバインドがリセットがあります。 有効なドロップ ターゲットにするのには、コントロールを基になるのデータ型からの上にドラッグした項目を表示することにする必要があります、**データソース**ウィンドウです。 たとえば、これが無効のデータ型を持つ項目をドラッグし<xref:System.DateTime>上に、<xref:System.Windows.Forms.CheckBox>であるため、<xref:System.Windows.Forms.CheckBox>日付を表示することはできません。

## <a name="bind-to-data-in-individual-controls"></a>個々 のコントロールにデータにバインドします。
「詳細」をデータ ソースをバインドすると、データセット内の各列は個別のコントロールにバインドされます。

![詳細をデータ ソースをバインド](../data-tools/media/raddata-bind-data-source-to-details.png "raddata バインド データ ソースの詳細")

> [!IMPORTANT]
> 前の図に、Orders テーブルからではなく、Customers テーブルの注文プロパティからドラッグしてください。 Customer.Orders プロパティへのバインド、によって、DataGridView に加えられたナビゲーション コマンドに直ちに反映されます詳細コントロール。 Orders テーブルからドラッグした場合、データセットに、コントロールをバインドする、まだけれども、これらがないと同期できません DataGridView

次の図はで、既定値に、Customers テーブルに注文プロパティを「詳細」をバインドした後に、フォームに追加のデータ バインド コントロールを示します、**データソース**ウィンドウです。

![Orders テーブルの詳細にバインドされて](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders テーブルの詳細にバインド")

各コントロールがスマート タグを持つことにも注意してください。 このタグは、そのコントロールのみに適用されるカスタマイズを使用できます。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows フォーム (.NET Framework) におけるデータ バインディング](/dotnet/framework/winforms/windows-forms-data-binding)