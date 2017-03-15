---
title: "Visual Studio でのデータへの WPF コントロールのバインド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [WPF], 表示"
  - "データ バインド, WPF"
  - "表示 (データを), WPF"
  - "WPF [WPF], データ"
  - "WPF データ バインド [Visual Studio]"
  - "WPF デザイナー, データ バインド"
  - "WPF, データ バインド (Visual Studio での)"
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual Studio でのデータへの WPF コントロールのバインド
データを [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] コントロールにバインドすることで、アプリケーションのユーザーに対してデータを表示できます。  これらのデータ バインド コントロールを作成するには、**\[データ ソース\]** ウィンドウから [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]に項目をドラッグします。  このトピックでは、データ バインド [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] アプリケーションの作成に使用できる最も一般的なタスク、ツール、およびクラスについて説明します。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でのデータ バインド コントロールの作成方法に関する一般的な情報については、「[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)」を参照してください。 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] データ バインドの詳細については、「[データ バインドの概要](../Topic/Data%20Binding%20Overview.md)」を参照してください。  
  
## データへの WPF コントロールのバインドに関連するタスク  
 次の表に、**\[データ ソース\]** ウィンドウから [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]に項目をドラッグすることで実行できるタスクを示します。  
  
|タスク|詳細情報|  
|---------|----------|  
|データ バインド コントロールを作成する。<br /><br /> 既存のコントロールをデータにバインドする。|[方法: Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)|  
|親子のリレーションシップを持つ関連データを表示するコントロールを作成する。あるコントロールの親データ レコードを選択すると、その選択レコードに関連する子データが別のコントロールに表示されるようにします。|[方法: WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)|  
|あるテーブルの外部キー フィールドの値に基づいて、別のテーブルの情報を表示する*ルックアップ テーブル*を作成する。|[方法: WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|コントロールをデータベース内のイメージにバインドする。|[方法: データベースの画像にコントロールをバインドする](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## 有効なドロップ ターゲット  
 **\[データ ソース\]** ウィンドウ内の項目は、[!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]の有効なドロップ ターゲットにのみドラッグできます。  有効なドロップ ターゲットの種類は、主にコンテナーとコントロールの 2 つです。  コンテナーとは、通常はコントロールを含むユーザー インターフェイス要素です。  たとえば、グリッドやウィンドウはコンテナーです。  
  
## 生成される XAML およびコード  
 **\[データ ソース\]** ウィンドウから [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]に項目をドラッグすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、新しいデータ バインド コントロールを定義する \(または、既存のコントロールをデータ ソースにバインドする\) [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] を生成します。  一部のデータ ソースでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] により、データ ソースにデータを読み込むためのコードも分離コード ファイルに生成されます。  
  
 次の表に、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] で [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\[データ ソース\] ウィンドウの各データ ソースに対して生成される  **とコードを示します。**  
  
|データ ソース|コントロールをデータ ソースにバインドする XAML の生成|データ ソースにデータを読み込むコードの生成|  
|-------------|------------------------------------|----------------------------|  
|データセット|はい|はい|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|はい|はい|  
|サービス|はい|いいえ|  
|オブジェクト|はい|いいえ|  
  
### データセット  
 **\[データ ソース\]** ウィンドウからデザイナーにテーブルまたは列をドラッグすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、次の処理を行う [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] を生成します。  
  
-   項目をドラッグした先のコンテナーのリソースに、データセットと新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。  <xref:System.Windows.Data.CollectionViewSource> は、データセットのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。  デザイナーの既存のコントロールに項目をドラッグすると、XAML により、その項目にコントロールがバインドされます。  コンテナーに項目をドラッグすると、XAML により、ドラッグした項目に対して選択されたコントロールが作成され、そのコントロールが項目にバインドされます。  コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、分離コード ファイルに次の変更も加えます。  
  
-   コントロールを格納する <xref:System.Windows.FrameworkElement.Loaded> 要素の [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] イベント ハンドラーを作成する。  イベント ハンドラーは、テーブルにデータを読み込み、コンテナーのリソースから <xref:System.Windows.Data.CollectionViewSource> を取得して、最初のデータ項目を現在の項目にします。  <xref:System.Windows.FrameworkElement.Loaded> イベント ハンドラーが既に存在する場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はこのコードを既存のイベント ハンドラーに追加します。  
  
### Entity Data Model  
 **\[データ ソース\]** ウィンドウからデザイナーにエンティティまたはエンティティ プロパティをドラッグすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、次の処理を行う [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] を生成します。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。  <xref:System.Windows.Data.CollectionViewSource> は、エンティティのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。  デザイナーの既存のコントロールに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] により、その項目にコントロールがバインドされます。  コンテナーに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] により、ドラッグした項目に対して選択されたコントロールが作成され、そのコントロールが項目にバインドされます。  コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
 Visual Studio は、分離コード ファイルに次の変更も加えます。  
  
-   デザイナーにドラッグされたエンティティ \(または、デザイナーにドラッグされたプロパティを含むエンティティ\) のクエリを返す新しいメソッドを追加する。  新しいメソッドの名前は Get*EntityName*Query です。ここで、*EntityName* はエンティティの名前です。  
  
-   コントロールを格納する <xref:System.Windows.FrameworkElement.Loaded> 要素の [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] イベント ハンドラーを作成する。  イベント ハンドラーは、Get*EntityName*Query メソッドを呼び出してデータをエンティティに読み込み、コンテナーのリソースから <xref:System.Windows.Data.CollectionViewSource> を取得し、最初のデータ項目を現在の項目にします。  <xref:System.Windows.FrameworkElement.Loaded> イベント ハンドラーが既に存在する場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はこのコードを既存のイベント ハンドラーに追加します。  
  
### サービス  
 **\[データ ソース\]** ウィンドウからデザイナーにサービス オブジェクトまたはプロパティをドラッグすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、データ バインド コントロールを作成する \(オブジェクトまたはプロパティに既存のコントロールをバインドする\) [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] を生成します。  ただし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はプロキシ サービス オブジェクトにデータを読み込むコードを生成しません。  このコードは、ユーザーが手動で記述する必要があります。  この方法を示す例については、「[チュートリアル: WCF Data Service への WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)」を参照してください。  
  
 Visual Studio は、次の処理を行う XAML を生成します。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。  <xref:System.Windows.Data.CollectionViewSource> は、サービスから返されるオブジェクトのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。  デザイナーの既存のコントロールに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] により、その項目にコントロールがバインドされます。  コンテナーに項目をドラッグすると、[!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] により、ドラッグした項目に対して選択されたコントロールが作成され、そのコントロールが項目にバインドされます。  コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
### オブジェクト  
 **\[データ ソース\]** ウィンドウからデザイナーにオブジェクトまたはプロパティをドラッグすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、データ バインド コントロールを作成する \(オブジェクトまたはプロパティに既存のコントロールをバインドする\) [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] を生成します。  ただし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はオブジェクトにデータを読み込むコードを生成しません。  このコードは、ユーザーが手動で記述する必要があります。  
  
> [!NOTE]
>  カスタム クラスはパブリックで、既定のパラメーターなしのコンストラクターを備えている必要があります。  構文に "ドット" が含まれる入れ子になったクラスにすることはできません。  詳細については、「[WPF における XAML とカスタム クラス](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md)」を参照してください。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は、次の処理を行う [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] を生成します。  
  
-   項目をドラッグした先のコンテナーのリソースに、新しい <xref:System.Windows.Data.CollectionViewSource> を追加する。  <xref:System.Windows.Data.CollectionViewSource> は、オブジェクトのデータの移動と表示に使用できるオブジェクトです。  
  
-   コントロールのデータ バインディングを作成する。  デザイナーの既存のコントロールに項目をドラッグすると、XAML により、その項目にコントロールがバインドされます。  コンテナーに項目をドラッグすると、XAML により、ドラッグした項目に対して選択されたコントロールが作成され、そのコントロールが項目にバインドされます。  コントロールは、新しい <xref:System.Windows.Controls.Grid> 内に作成されます。  
  
## 参照  
 [方法: Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [方法: WPF アプリケーションでルックアップ テーブルを作成する](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [方法: WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)   
 [エンティティ データ モデルへの WPF コントロールのバインドに関するページ](http://msdn.microsoft.com/data/jj574514.aspx)   
 [チュートリアル: データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [チュートリアル: WCF Data Service への WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [チュートリアル: WPF アプリケーションでの関連データの表示](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)   
 [ウィンドウ](../Topic/Data%20Sources%20Window.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)