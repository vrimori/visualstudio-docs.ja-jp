---
title: "チュートリアル: リボン デザイナーを使用してカスタム タブの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: cdbbd7ee286c97a986e89ccdb5bdcfdde4ef7578
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer"></a>チュートリアル : リボン デザイナーを使用したカスタム タブの作成
  リボン デザイナーでは、カスタム タブを作成し、その後、カスタム タブの中でコントロールを追加して配置することができます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   [操作ウィンドウの作成](#BKMK_CreateActionsPanes)です。  
  
-   [カスタム タブの作成](#BKMK_CreateCustomTab)です。  
  
-   [カスタム タブのボタンを使用して、操作ウィンドウの表示と非表示](#BKMK_HideShowActionsPane)です。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-an-excel-workbook-project"></a>Excel ブック プロジェクトの作成  
 すべての Office アプリケーションで、ほぼ同じ手順でリボン デザイナーを操作できます。 この例では、Excel ブックを使用します。  
  
#### <a name="to-create-an-excel-workbook-project"></a>Excel ブック プロジェクトを作成するには  
  
-   名前の Excel ブック プロジェクトを作成**MyExcelRibbon**です。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しいブックを開き、 **MyExcelRibbon**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
##  <a name="BKMK_CreateActionsPanes"></a>操作ウィンドウの作成  
 プロジェクトに 2 つのカスタム操作ウィンドウを追加します。 後の作業で、これらの操作ウィンドウの表示/非表示を切り替えるボタンをカスタム タブに追加します。  
  
#### <a name="to-create-actions-panes"></a>操作ウィンドウを作成するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、 **ActionsPaneControl**を選択し**追加**です。  
  
     **ActionsPaneControl1.cs**または**ActionsPaneControl1.vb**ファイルは、デザイナーで開きます。  
  
3.  **コモン コントロール**のタブ、**ツールボックス**、デザイナー画面にラベルを追加します。  
  
4.  **プロパティ**ウィンドウで、設定、**テキスト**プロパティに label1 の**Actions Pane 1**です。  
  
5.  手順 1. ～ 5. を繰り返して、2 つ目の操作ウィンドウとラベルを作成します。 設定、**テキスト**に 2 つ目のラベルのプロパティ**Actions Pane 2**です。  
  
##  <a name="BKMK_CreateCustomTab"></a>カスタム タブの作成  
 Office アプリケーションのデザイン ガイドラインの 1 つとして、ユーザーが常に Office アプリケーションの UI を操作できなければならないことがあります。 操作ウィンドウにこの機能を追加するには、リボンのカスタム タブから操作ウィンドウの表示/非表示を切り替えることができるボタンを追加します。 カスタム タブを作成するには追加、**リボン (ビジュアル デザイナー)**プロジェクト項目です。 デザイナーでは、コントロールの追加と配置、コントロールのプロパティの設定、およびコントロール イベントの処理を行うことができます。  
  
#### <a name="to-create-a-custom-tab"></a>カスタム タブを作成するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[リボン (ビジュアル デザイナー)]**をクリックします。  
  
3.  新しいリボンの名前を変更**MyRibbon**を選択して**追加**です。  
  
     リボン デザイナーで **MyRibbon.cs** ファイルまたは **MyRibbon.vb** ファイルが開き、既定のタブとグループが表示されます。  
  
4.  リボン デザイナーで、既定のタブをクリックします。  
  
5.  **プロパティ**ウィンドウで、展開、 **ControlId**プロパティ、および設定、 **[controlidtype]**プロパティを**カスタム**です。  
  
6.  設定、**ラベル**プロパティを**My Custom Tab**です。  
  
7.  リボン デザイナーで選択**group1**です。  
  
8.  **プロパティ**ウィンドウで、設定**ラベル**に**Actions Pane Manager**です。  
  
9. **Office リボン コントロール**のタブ、**ツールボックス**、上にボタンをドラッグして**group1**です。  
  
10. 選択**button1**です。  
  
11. **プロパティ**ウィンドウで、設定**ラベル**に**Show Actions Pane 1**です。  
  
12. 2 番目のボタンを追加して**group1**、設定と、**ラベル**プロパティを**Show Actions Pane 2**です。  
  
13. **Office リボン コントロール**のタブ、**ツールボックス**、ドラッグ、 **ToggleButton**コントロールを**group1**です。  
  
14. 設定、**ラベル**プロパティを**Hide Actions Pane**です。  
  
##  <a name="BKMK_HideShowActionsPane"></a>カスタム タブのボタンを使用して、操作ウィンドウの表示と非表示  
 最後の手順で、ユーザーに応答するコードを追加します。 2 つのボタンの <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> イベントと、トグル ボタンの <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> イベントのイベント ハンドラーを追加します。 操作ウィンドウの表示/非表示を有効にするために、イベント ハンドラーにコードを追加します。  
  
#### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>カスタム タブのボタンを使用して操作ウィンドウの表示/非表示を切り替えるには  
  
1.  **ソリューション エクスプ ローラー**MyRibbon.cs または MyRibbon.vb のショートカット メニューを開き、クリックして**コードの表示**です。  
  
2.  `MyRibbon` クラスの先頭に、次のコードを追加します。 このコードにより、操作ウィンドウ オブジェクトが 2 つ作成されます。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  `MyRibbon_Load` メソッドを次のコードに置き換えます。 このコードにより、<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> コレクションに操作ウィンドウ オブジェクトが追加され、オブジェクトが非表示になります。 さらに、この Visual C# コードは複数のリボン コントロール イベントにデリゲートをアタッチします。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  `MyRibbon` クラスに、次の 3 つのイベント ハンドラー メソッドを追加します。 これらのメソッドは、2 つのボタンの <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> イベントと、トグル ボタンの <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> イベントを処理します。 button1 と button2 のイベント ハンドラーにより、別の操作ウィンドウが表示されます。 toggleButton1 のイベント ハンドラーにより、アクティブな操作ウィンドウの表示/非表示が切り替えられます。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="testing-the-custom-tab"></a>カスタム タブのテスト  
 プロジェクト、Excel を起動を実行すると、 **My Custom Tab**リボンにタブが表示されます。 ボタンの  **My Custom Tab**表示し、操作ウィンドウを非表示にします。  
  
#### <a name="to-test-the-custom-tab"></a>カスタム タブをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  選択、 **My Custom Tab**タブです。  
  
3.  **Custom Actions Pane Manager**グループで、選択**Show Actions Pane 1**です。  
  
     [操作] ウィンドウが表示され、ラベルが表示されます**Actions Pane 1**です。  
  
4.  選択**Show Actions Pane 2**です。  
  
     [操作] ウィンドウが表示され、ラベルが表示されます**Actions Pane 2**です。  
  
5.  選択**Hide Actions Pane**です。  
  
     操作ウィンドウが表示されなくなります。  
  
## <a name="next-steps"></a>次の手順  
 Office UI をカスタマイズする方法の詳細については、次のトピックで説明します。  
  
-   ドキュメント レベルのカスタマイズにコンテキスト ベースの UI を追加する。 詳細については、「 [Actions Pane Overview](../vsto/actions-pane-overview.md)」を参照してください。  
  
-   標準またはカスタムの Microsoft Office Outlook フォームを拡張する。 詳細については、次を参照してください。[チュートリアル: Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)です。  
  
## <a name="see-also"></a>参照  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [Outlook のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法: リボンのタブの位置を変更](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: コントロール Backstage ビューを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)  
  
  