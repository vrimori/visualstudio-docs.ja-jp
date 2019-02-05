---
title: 第 1 部のデータに WPF コントロールをバインドします。
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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b1359371cc7a10ceb3056660a7b445f47e950247
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918271"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio でデータに WPF コントロールをバインドする

データを [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] コントロールにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 これらのデータ バインド コントロールを作成するから項目をドラッグすることができます、**データソース**ウィンドウ、 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] Visual Studio でします。 このトピックでは、データ バインド [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] アプリケーションの作成に使用できる最も一般的なタスク、ツール、およびクラスについて説明します。

Visual Studio でのデータ バインド コントロールを作成する方法については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] データ バインディングの詳細については、「[データ バインディングの概要](/dotnet/framework/wpf/data/data-binding-overview)」を参照してください。

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>データへの WPF コントロールのバインドに関連するタスク

次の表に、**[データ ソース]** ウィンドウから [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] に項目をドラッグすることで実行できるタスクを示します。

|タスク|詳細情報|
|----------| - |
|データ バインド コントロールを作成する。<br /><br /> 既存のコントロールをデータにバインドする。|[データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|親子のリレーションシップを持つ関連データを表示するコントロールを作成する。あるコントロールの親データ レコードを選択すると、その選択レコードに関連する子データが別のコントロールに表示されるようにします。|[WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)|
|あるテーブルの外部キー フィールドの値に基づいて、別のテーブルの情報を表示する*ルックアップ テーブル*を作成する。|[WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|コントロールをデータベース内のイメージにバインドする。|[データベースの画像にコントロールをバインドする](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>有効なドロップ ターゲット

**[データ ソース]** ウィンドウ内の項目は、[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] の有効なドロップ ターゲットにのみドラッグできます。 有効なドロップ ターゲットの種類は、主にコンテナーとコントロールの 2 つです。 コンテナーとは、通常はコントロールを含むユーザー インターフェイス要素です。 たとえば、グリッドやウィンドウはコンテナーです。

## <a name="generated-xaml-and-code"></a>生成される XAML およびコード

項目をドラッグすると、**データソース**ウィンドウ、 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]、Visual Studio によって生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]を新しいデータ バインド コントロールを定義します (または既存のコントロールをデータ ソースにバインドします)。 一部のデータ ソースの Visual Studio もデータをデータ ソースに設定する分離コード ファイルでコードを生成します。

次の表、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]と各種のデータ ソースの Visual Studio によって生成されるコード、**データソース**ウィンドウ。

| データ ソース | コントロールをデータ ソースにバインドする XAML の生成 | データ ソースにデータを読み込むコードの生成 |
| - | - | - |
| データセット | はい | はい |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | はい | はい |
| サービス | はい | × |
| Object | はい | × |

### <a name="datasets"></a>データセット

テーブルまたは列をドラッグすると、**データ ソース**デザイナー、Visual Studio ウィンドウの生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]は次を実行します。

-   項目をドラッグした先のコンテナーのリソースに、データセットと新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、データセットのデータの移動と表示に使用できるオブジェクトです。

-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、XAML により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合は、XAML がドラッグした項目に対して選択されたコントロールを作成し、項目にバインドするコントロール。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。

Visual Studio は、分離コード ファイルに次の変更も加えます。

- コントロールを格納する <xref:System.Windows.FrameworkElement.Loaded> 要素の [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] イベント ハンドラーを作成する。 イベント ハンドラーは、テーブルにデータを読み込み、コンテナーのリソースから <xref:System.Windows.Data.CollectionViewSource> を取得して、最初のデータ項目を現在の項目にします。 場合、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーが既に存在する、Visual Studio は、既存のイベント ハンドラーに次のコードを追加します。

### <a name="entity-data-models"></a>エンティティ データ モデル

エンティティまたはエンティティ プロパティからドラッグすると、**データ ソース**デザイナー、Visual Studio ウィンドウの生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]は次を実行します。

- 項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、エンティティのデータの移動と表示に使用できるオブジェクトです。

- コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]コントロールを作成します。 ドラッグした項目の選択されていたとコントロールの項目にバインドします。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。

Visual Studio は、分離コード ファイルに次の変更も加えます。

- デザイナーにドラッグされたエンティティ (または、デザイナーにドラッグされたプロパティを含むエンティティ) のクエリを返す新しいメソッドを追加する。 新しいメソッドの名前は`Get<EntityName>Query`ここで、`\<EntityName>`エンティティの名前を指定します。

- コントロールを格納する <xref:System.Windows.FrameworkElement.Loaded> 要素の [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] イベント ハンドラーを作成する。 イベント ハンドラーの呼び出し、`Get<EntityName>Query`エンティティをデータを格納するメソッドを取得、<xref:System.Windows.Data.CollectionViewSource>からコンテナーのリソース、し、最初のデータ項目の現在の項目。 場合、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーが既に存在する、Visual Studio は、既存のイベント ハンドラーに次のコードを追加します。

### <a name="services"></a>Services

サービス オブジェクトまたはプロパティからドラッグすると、**データソース**デザイナー、Visual Studio ウィンドウの生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]をデータ バインド コントロールを作成します (または、オブジェクトまたはプロパティに既存のコントロールをバインドします)。 ただし、Visual Studio では、データをプロキシ サービス オブジェクトに設定するコードは生成しません。 このコードは、ユーザーが手動で記述する必要があります。 これを行う方法については、例では、次を参照してください。 [WCF data service にコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)します。

Visual Studio は、次の処理を行う XAML を生成します。

- 項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、サービスから返されるオブジェクトのデータの移動と表示に使用できるオブジェクトです。

- コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]コントロールを作成します。 ドラッグした項目の選択されていたとコントロールの項目にバインドします。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。

### <a name="objects"></a>オブジェクト

オブジェクトまたはからプロパティをドラッグすると、**データソース**デザイナー、Visual Studio のウィンドウが生成されます[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]をデータ バインド コントロールを作成します (または、オブジェクトまたはプロパティに既存のコントロールをバインドします)。 ただし、Visual Studio では、オブジェクトのデータに設定するコードを生成しません。 このコードは、ユーザーが手動で記述する必要があります。

> [!NOTE]
> カスタム クラス パブリックであり、既定では、パラメーターなしのコンス トラクターを持ちます。 入れ子になったクラスをそれぞれの構文で「ドット」を持つことができません。 詳細については、次を参照してください。 [XAML とカスタム クラスの WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf)します。

Visual Studio によって生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]は次を実行します。

-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、オブジェクトのデータの移動と表示に使用できるオブジェクトです。

-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、XAML により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合は、XAML がドラッグした項目に対して選択されたコントロールを作成し、項目にバインドするコントロール。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)
