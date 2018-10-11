---
title: Visual Studio2 でデータに WPF コントロールをバインドする |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e99f18122dc0be7e3a68871aa58a9109502da9c0
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880956"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio でのデータに WPF コントロールをバインドします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio 2017 ドキュメント](/visualstudio/)します。  
  
データ バインドを作成する[!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)]コントロールを使用して、**データソース**ウィンドウ。 最初に、データ ソースを追加、**データソース**ウィンドウ。 項目をドラッグし、**データ ソース**ウィンドウ、**WPF デザイナー**します。  
  
##  <a name="adding"></a> データ ソース ウィンドウにデータ ソースを追加します。  
 データ バインド コントロールを作成する前にまずをデータ ソースを追加する必要があります、**データソース**ウィンドウ。  
  
#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>[データ ソース] ウィンドウにデータ ソースを追加するには  
  
1.  **ビュー**メニューで、**その他の Windows**、 をクリックし、**データ ソース**します。  
  
2.  クリックして**新しいデータ ソースの追加**、完了して、**データ ソースの構成**ウィザード。  
  
3.  次のいずれかのタスクを実行して、データ バインド コントロールを作成します。  
  
    -   [データの 1 つのフィールドにバインドされるコントロールを作成する](#simple)します。  
  
    -   [データの複数のフィールドにバインドされるコントロールを作成する](#complex)します。  
  
    -   [データの複数のフィールドにバインドするコントロールのセットを作成する](#details)します。  
  
    -   [デザイナーで既存のコントロールへのデータ バインディング](#existing)します。  
  
##  <a name="simple"></a> 単一のデータ フィールドにバインドされているコントロールを作成します。  
 データ ソースを追加した後、**データソース**ウィンドウなど、データの 1 つのフィールドを表示する新しいデータ バインド コントロールを作成することができます、<xref:System.Windows.Controls.ComboBox>または<xref:System.Windows.Controls.TextBox>します。  
  
#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>単一のデータ フィールドにバインドされるコントロールを作成するには  
  
1.  **データソース**ウィンドウで、テーブルまたはオブジェクトを表す項目を展開します。 バインドする列またはプロパティを表す子項目を検索します。 ビジュアルの例では、次を参照してください。[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)します。  
  
2.  必要に応じて、作成するコントロールを選択します。 内の各項目、**データソース**ウィンドウがデザイナーに項目をドラッグするときに作成される既定のコントロール。 既定のコントロールは、項目の基になるデータ型によって異なります。  
  
     既定以外のコントロールを選択するには、項目の横にあるドロップダウン矢印をクリックし、コントロールを選択します。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。  
  
3.  デザイナーで有効なコンテナーに項目をドラッグします。 有効なコンテナーの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 新しいデータ バインド コントロールと適切なタイトルを作成します。<xref:System.Windows.Controls.Label>コンテナーにします。 また、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって、データにコントロールをバインドするための [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] とコードが生成されます。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
##  <a name="complex"></a> 複数のデータ フィールドにバインドされているコントロールを作成します。  
 データ ソースを追加した後、**データソース**ウィンドウなど、データの複数のフィールドを表示する新しいデータ バインド コントロールを作成することができます、<xref:System.Windows.Controls.DataGrid>または<xref:System.Windows.Controls.ListView>します。  
  
#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>複数のデータ フィールドにバインドされるコントロールを作成するには  
  
1.  **データソース**ウィンドウで、テーブルまたはオブジェクトを表す項目を選択します。 ビジュアルの例では、次を参照してください。[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)します。  
  
2.  必要に応じて、作成するコントロールを選択します。 既定では、各項目で、**データ ソース**を作成するデータ テーブルまたはオブジェクトを表す枠が設定されて、 <xref:System.Windows.Controls.DataGrid> (プロジェクトのターゲットが .NET Framework 4) の場合または<xref:System.Windows.Controls.ListView>(の .NET Framework の以前のバージョン)。  
  
     既定以外のコントロールを選択するには、項目の横にあるドロップダウン矢印をクリックし、コントロールを選択します。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。  
  
    > [!NOTE]
    >  特定の列またはプロパティを表示しないようにする場合は、項目を展開してその子を表示します。 列またはを表示したくないプロパティの横にあるドロップダウン矢印をクリックします。 **None**します。  
  
3.  デザイナーで、<xref:System.Windows.Controls.Grid> などの有効なコンテナーに項目をドラッグします。 有効なコンテナーの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって、新しいデータ バインド コントロールがコンテナー内に作成されます。 また、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって、データにコントロールをバインドするための [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] とコードが生成されます。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
##  <a name="details"></a> 複数のデータ フィールドにバインドされているコントロールのセットを作成します。  
 データ ソースを追加した後、**データソース**ウィンドウで、データ テーブルまたはオブジェクトは、一連のコントロールにバインドすることができます。 テーブルまたはオブジェクトの列やプロパティごとに、異なるコントロールが作成されます。  
  
#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>複数のデータ フィールドにバインドされるコントロール セットを作成するには  
  
1.  **データソース**ウィンドウで、テーブルまたはオブジェクトを表す項目を選択します。 ビジュアルの例では、次を参照してください。[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)します。  
  
2.  クリックし、項目の横にあるドロップダウン矢印をクリックします。**詳細**します。  
  
    > [!NOTE]
    >  特定の列またはプロパティを表示しないようにする場合は、項目を展開してその子を表示します。 列またはを表示したくないプロパティの横にあるドロップダウン矢印をクリックします。 **None**します。  
  
3.  デザイナーで、<xref:System.Windows.Controls.Grid> などの有効なコンテナーに項目をドラッグします。 有効なコンテナーの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって、新しいデータ バインド コントロールがコンテナー内に作成されます。 各コントロールは別々の列またはプロパティにバインドされ、適切なタイトルの <xref:System.Windows.Controls.Label> コントロールが追加されます。 また、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって、データにコントロールをバインドするための [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] とコードが生成されます。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
##  <a name="existing"></a> デザイナーで既存のコントロールに Binddata  
 データ ソースを追加した後、**データソース**ウィンドウで、データ デザイナーで既存のコントロールにバインディングを追加することができます。  
  
#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>デザイナー内の既存のコントロールにデータをバインドするには  
  
1.  **データソース**ウィンドウで、次の手順のいずれかを使用します。  
  
    -   <xref:System.Windows.Controls.DataGrid> や <xref:System.Windows.Controls.ListView> など、複数のデータ フィールドを表示する既存のコントロールにデータ バインディングを追加するには、コントロールにバインドするテーブルまたはオブジェクトを表す項目を選択します。  
  
    -   <xref:System.Windows.Controls.ComboBox> や <xref:System.Windows.Controls.TextBox> など、単一のデータ フィールドを表示する既存のコントロールにデータ バインディングを追加するには、データが格納されているテーブルまたはオブジェクトを表す項目を展開し、コントロールにバインドするデータを表す項目を選択します。  
  
2.  選択した項目をドラッグして、**データソース**デザイナーで既存のコントロールにウィンドウ。 コントロールは、有効なドロップ ターゲットである必要があります。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 生成[!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]と、データにコントロールをバインドするコードです。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
    > [!NOTE]
    >  コントロールが既にデータにバインドされている場合は、コントロールのデータ バインディングが、最後にコントロールにドラッグされた項目に再設定されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータに WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [WPF アプリケーションでルックアップ テーブルを作成します。](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [WPF アプリケーションで関連するデータを表示します。](../data-tools/display-related-data-in-wpf-applications.md)   
 [データセットへの WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [WCF データ サービスへの WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [チュートリアル: WPF アプリケーションでの関連データの表示](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)

