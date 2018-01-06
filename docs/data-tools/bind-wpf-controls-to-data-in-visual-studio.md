---
title: "Visual Studio の第 1 部でのデータに WPF コントロールをバインド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 77c56d70c6fc3dd3dac9a563c146d8bab2c6f699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio でのデータに WPF コントロールをバインドします。
データを [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] コントロールにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 これらのデータ バインド コントロールを作成するから項目をドラッグすることができます、**データソース** ウィンドウ、[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]で[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 このトピックでは、データ バインド [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] アプリケーションの作成に使用できる最も一般的なタスク、ツール、およびクラスについて説明します。  
  
 データ バインド コントロールを作成する方法についての一般的な[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を参照してください[Visual Studio でのデータにコントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)です。 詳細については[!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]データ バインディングを参照してください[データ バインディングの概要](/dotnet/framework/wpf/data/data-binding-overview)です。  
  
## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>データに WPF コントロールのバインドに関連するタスク  
 次の表の一覧から項目をドラッグして実行できるタスク、**データソース**ウィンドウ、[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]です。  
  
|タスク|詳細情報|  
|----------|----------------------|  
|データ バインド コントロールを作成する。<br /><br /> 既存のコントロールをデータにバインドする。|[データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)|  
|親子のリレーションシップを持つ関連データを表示するコントロールを作成する。あるコントロールの親データ レコードを選択すると、その選択レコードに関連する子データが別のコントロールに表示されるようにします。|[WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)|  
|作成、*ルックアップ テーブル*別のテーブルの外部キー フィールドの値に基づいて 1 つのテーブルからの情報を表示します。|[WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|コントロールをデータベース内のイメージにバインドする。|[データベースの画像にコントロールをバインドする](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## <a name="valid-drop-targets"></a>有効なドロップ ターゲット  
 項目をドラッグすることができます、**データソース**ウィンドウ内の有効なドロップ ターゲットにのみ、[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]です。 有効なドロップ ターゲットの種類は、主にコンテナーとコントロールの 2 つです。 コンテナーとは、通常はコントロールを含むユーザー インターフェイス要素です。 たとえば、グリッドやウィンドウはコンテナーです。  
  
## <a name="generated-xaml-and-code"></a>生成される XAML およびコード  
 項目をドラッグすると、**データ ソース**ウィンドウ、 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]を新しいデータ バインド コントロールを定義します (または既存のコントロールをデータ ソースにバインド)。 一部のデータ ソースでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] により、データ ソースにデータを読み込むためのコードも分離コード ファイルに生成されます。  
  
 次の表、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]とコードがあり[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]内のデータ ソースの種類ごとに生成されます、**データソース**ウィンドウです。  
  
|データ ソース|コントロールをデータ ソースにバインドする XAML の生成|データ ソースにデータを読み込むコードの生成|  
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|  
|データセット|[はい]|はい|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|はい|[はい]|  
|サービス|[はい]|×|  
|Object|[はい]|×|  
  
### <a name="datasets"></a>データセット  
 テーブルまたは列をドラッグすると、**データ ソース**をデザイナーにウィンドウ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]は次を実行します。  
  
-   項目をドラッグした先のコンテナーのリソースに、データセットと新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、データセットのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、XAML により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合は、XAML は、ドラッグした項目に対して選択されたコントロールを作成し、項目にコントロールをバインドします。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、分離コード ファイルに次の変更も加えます。  
  
-   コントロールを格納する <xref:System.Windows.FrameworkElement.Loaded> 要素の [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] イベント ハンドラーを作成する。 イベント ハンドラーは、テーブルにデータを読み込み、コンテナーのリソースから <xref:System.Windows.Data.CollectionViewSource> を取得して、最初のデータ項目を現在の項目にします。 場合、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーは既に存在する、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]既存のイベント ハンドラーに次のコードを追加します。  
  
### <a name="entity-data-models"></a>エンティティ データ モデル  
 エンティティまたはエンティティ プロパティからドラッグすると、**データ ソース**をデザイナーにウィンドウ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]は次を実行します。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、エンティティのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]コントロールが作成され、ドラッグした項目が選択されていると、項目にコントロールをバインドします。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
Visual Studio は、分離コード ファイルに次の変更も加えます。  
  
-   デザイナーにドラッグされたエンティティ (または、デザイナーにドラッグされたプロパティを含むエンティティ) のクエリを返す新しいメソッドを追加する。 新しいメソッドの名前は Get*EntityName*クエリ、場所*EntityName*エンティティの名前を指定します。  
  
-   コントロールを格納する <xref:System.Windows.FrameworkElement.Loaded> 要素の [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] イベント ハンドラーを作成する。 イベント ハンドラーが、Get を呼び出す*EntityName*エンティティにデータを格納、取得メソッドのクエリ、<xref:System.Windows.Data.CollectionViewSource>コンテナーのリソースからでは最初のデータが現在の項目を項目。 場合、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーは既に存在する、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]既存のイベント ハンドラーに次のコードを追加します。  
  
### <a name="services"></a>サービス  
 サービス オブジェクトまたはプロパティからドラッグすると、**データ ソース**をデザイナーにウィンドウ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]をデータ バインド コントロールを作成します (または、オブジェクトまたはプロパティに既存のコントロールをバインド)。 ただし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はプロキシ サービス オブジェクトにデータを読み込むコードを生成しません。 このコードは、ユーザーが手動で記述する必要があります。 これを行う方法を示す例を参照してください[WCF データ サービスにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)です。  
  
 Visual Studio は、次の処理を行う XAML を生成します。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、サービスから返されるオブジェクトのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]コントロールが作成され、ドラッグした項目が選択されていると、項目にコントロールをバインドします。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
### <a name="objects"></a>オブジェクト  
 オブジェクトまたはからプロパティをドラッグすると、**データ ソース**をデザイナーにウィンドウ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]をデータ バインド コントロールを作成します (または、オブジェクトまたはプロパティに既存のコントロールをバインド)。 ただし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はオブジェクトにデータを読み込むコードを生成しません。 このコードは、ユーザーが手動で記述する必要があります。  
  
> [!NOTE]
>  カスタム クラス パブリックであり、既定では、パラメーターなしのコンス トラクターを持ちます。 それらをそれぞれの構文で「ドット」を持つ入れ子になった can'tbe クラスです。 詳細については、次を参照してください。 [XAML と WPF のカスタム クラス](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf)です。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]は次を実行します。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、オブジェクトのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、XAML により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合は、XAML は、ドラッグした項目に対して選択されたコントロールを作成し、項目にコントロールをバインドします。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
## <a name="see-also"></a>関連項目
[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)
