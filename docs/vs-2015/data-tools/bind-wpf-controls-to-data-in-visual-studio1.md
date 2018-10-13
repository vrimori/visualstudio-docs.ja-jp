---
title: Visual Studio1 でデータに WPF コントロールをバインドする |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c71181a939ae91986ed31e2518456002f5bb417c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237017"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio でのデータに WPF コントロールをバインドします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
データを [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] コントロールにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。 これらのデータ バインド コントロールを作成するから項目をドラッグすることができます、**データソース**ウィンドウ、[!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]で[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 このトピックでは、データ バインド [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] アプリケーションの作成に使用できる最も一般的なタスク、ツール、およびクラスについて説明します。  
  
 データ バインド コントロールを作成する方法についての一般的な[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]を参照してください[Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。 詳細については[!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]データ バインディングを参照してください[データ バインディングの概要](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)します。  
  
## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>データに WPF コントロールのバインドに関連するタスク  
 次の表から項目をドラッグして実行できるタスク、**データソース**ウィンドウ、 [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]。  
  
|タスク|詳細情報|  
|----------|----------------------|  
|データ バインド コントロールを作成する。<br /><br /> 既存のコントロールをデータにバインドする。|[Visual Studio でのデータに WPF コントロールをバインド](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)[データセットにコントロールを WPF のバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)|  
|親子のリレーションシップを持つ関連データを表示するコントロールを作成する。あるコントロールの親データ レコードを選択すると、その選択レコードに関連する子データが別のコントロールに表示されるようにします。|[WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)|  
|作成、*ルックアップ テーブル*別のテーブルの外部キー フィールドの値に基づいて 1 つのテーブルからの情報を表示します。|[WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|コントロールをデータベース内のイメージにバインドする。|[データベースの画像にコントロールをバインドする](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## <a name="valid-drop-targets"></a>有効なドロップ ターゲット  
 項目をドラッグすることができます、**データソース**ウィンドウ内の有効なドロップ ターゲットにのみ、[!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]します。 有効なドロップ ターゲットの種類は、主にコンテナーとコントロールの 2 つです。 コンテナーとは、通常はコントロールを含むユーザー インターフェイス要素です。 たとえば、グリッドやウィンドウはコンテナーです。  
  
## <a name="generated-xaml-and-code"></a>XAML とコードの生成  
 項目をドラッグすると、**データ ソース**ウィンドウ、 [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]を新しいデータ バインド コントロールを定義します (または既存のコントロールをデータ ソースにバインドします)。 一部のデータ ソースでは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] により、データ ソースにデータを読み込むためのコードも分離コード ファイルに生成されます。  
  
 次の表、[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]とコードがあり[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]内のデータ ソースの種類ごとに生成、**データソース**ウィンドウ。  
  
|データ ソース|コントロールをデータ ソースにバインドする XAML の生成|データ ソースにデータを読み込むコードの生成|  
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|  
|データセット|はい|[はい]|  
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|[はい]|はい|  
|サービス|はい|いいえ|  
|Object|はい|いいえ|  
  
### <a name="datasets"></a>データセット  
 テーブルまたは列をドラッグすると、**データ ソース**、デザイナーにウィンドウ[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]次を行うこと。  
  
-   項目をドラッグした先のコンテナーのリソースに、データセットと新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、データセットのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、XAML により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合は、XAML がドラッグした項目に対して選択されたコントロールを作成し、項目にバインドするコントロール。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] は、分離コード ファイルに次の変更も加えます。  
  
-   コントロールを格納する <xref:System.Windows.FrameworkElement.Loaded> 要素の [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] イベント ハンドラーを作成する。 イベント ハンドラーは、テーブルにデータを読み込み、コンテナーのリソースから <xref:System.Windows.Data.CollectionViewSource> を取得して、最初のデータ項目を現在の項目にします。 場合、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーが既に存在する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]既存のイベント ハンドラーに次のコードを追加します。  
  
### <a name="entity-data-models"></a>エンティティ データ モデル  
 エンティティまたはエンティティ プロパティからドラッグすると、**データ ソース**、デザイナーにウィンドウ[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]次を行うこと。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、エンティティのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合、[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]コントロールを作成します。 ドラッグした項目の選択されていたとコントロールの項目にバインドします。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
 Visual Studio は、分離コード ファイルに次の変更も加えます。  
  
-   デザイナーにドラッグされたエンティティ (または、デザイナーにドラッグされたプロパティを含むエンティティ) のクエリを返す新しいメソッドを追加する。 新しいメソッドの名前は Get*EntityName*、クエリ、 *EntityName*エンティティの名前を指定します。  
  
-   コントロールを格納する <xref:System.Windows.FrameworkElement.Loaded> 要素の [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] イベント ハンドラーを作成する。 イベント ハンドラーは、Get を呼び出して*EntityName*Query メソッドを取得、データ エンティティを読み込み、<xref:System.Windows.Data.CollectionViewSource>からコンテナーのリソース、し、最初のデータ項目の現在の項目。 場合、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラーが既に存在する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]既存のイベント ハンドラーに次のコードを追加します。  
  
### <a name="services"></a>Services  
 サービス オブジェクトまたはプロパティからドラッグすると、**データ ソース**、デザイナーにウィンドウ[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]をデータ バインド コントロールを作成します (または、オブジェクトまたはプロパティに既存のコントロールをバインドします)。 ただし、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] はプロキシ サービス オブジェクトにデータを読み込むコードを生成しません。 このコードは、ユーザーが手動で記述する必要があります。 これを行う方法については、例では、次を参照してください。 [WCF data service にコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)します。  
  
 Visual Studio は、次の処理を行う XAML を生成します。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、サービスから返されるオブジェクトのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合、[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]コントロールを作成します。 ドラッグした項目の選択されていたとコントロールの項目にバインドします。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
### <a name="objects"></a>オブジェクト  
 オブジェクトまたはからプロパティをドラッグすると、**データ ソース**、デザイナーにウィンドウ[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]生成[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]をデータ バインド コントロールを作成します (または、オブジェクトまたはプロパティに既存のコントロールをバインドします)。 ただし、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] はオブジェクトにデータを読み込むコードを生成しません。 このコードは、ユーザーが手動で記述する必要があります。  
  
> [!NOTE]
>  カスタム クラス パブリックであり、既定では、パラメーターなしのコンス トラクターを持ちます。 それらをそれぞれの構文で「ドット」を持つ入れ子になった can'tbe クラス。 詳細については、次を参照してください。 [XAML とカスタム クラスの WPF](http://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a)します。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 生成[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]は次を実行します。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。 <xref:System.Windows.Data.CollectionViewSource> は、オブジェクトのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。 デザイナーの既存のコントロールに項目をドラッグすると、XAML により、その項目にコントロールがバインドされます。 コンテナーに項目をドラッグする場合は、XAML がドラッグした項目に対して選択されたコントロールを作成し、項目にバインドするコントロール。 コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)

