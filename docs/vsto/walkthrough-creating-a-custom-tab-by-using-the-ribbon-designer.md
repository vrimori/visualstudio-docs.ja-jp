---
title: "チュートリアル : リボン デザイナーを使用したカスタム タブの作成"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "操作ウィンドウ [Visual Studio での Office 開発], 制御 (リボンによる)"
  - "カスタム リボン, タブ"
  - "カスタム タブ [Visual Studio での Office 開発]"
  - "カスタマイズ (リボンを), タブ"
  - "リボン [Visual Studio での Office 開発], カスタマイズ"
  - "リボン デザイナー [Visual Studio での Office 開発]"
ms.assetid: 312865e6-950f-46ab-88de-fe7eb8036bfe
caps.latest.revision: 68
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 67
---
# チュートリアル : リボン デザイナーを使用したカスタム タブの作成
  リボン デザイナーでは、カスタム タブを作成し、その後、カスタム タブの中でコントロールを追加して配置することができます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   [操作ウィンドウの作成](#BKMK_CreateActionsPanes).  
  
-   [カスタム タブの作成](#BKMK_CreateCustomTab).  
  
-   [カスタム タブのボタンによる操作ウィンドウの表示/非表示の切り替え](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Excel ブック プロジェクトの作成  
 すべての Office アプリケーションで、ほぼ同じ手順でリボン デザイナーを操作できます。  この例では、Excel ブックを使用します。  
  
#### Excel ブック プロジェクトを作成するには  
  
-   MyExcelRibbon という名前で Excel ブックのプロジェクトを作成します。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。  
  
     新しいワークブックがデザイナーで開き、**MyExcelRibbon** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
##  <a name="BKMK_CreateActionsPanes"></a> 操作ウィンドウの作成  
 プロジェクトに 2 つのカスタム操作ウィンドウを追加します。  後の作業で、これらの操作ウィンドウの表示\/非表示を切り替えるボタンをカスタム タブに追加します。  
  
#### 操作ウィンドウを作成するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[ActionsPaneControl\]** をクリックし、**\[追加\]** をクリックします。  
  
     デザイナーで **ActionsPaneControl1.cs** ファイルまたは **ActionsPaneControl1.vb** ファイルが開きます。  
  
3.  **ツールボックス**の **\[コモン コントロール\]** タブから、デザイナー画面にラベルを追加します。  
  
4.  **\[プロパティ\]** ウィンドウで、label1 の **\[Text\]** プロパティを Actions Pane 1 に設定します。  
  
5.  手順 1. ～ 5. を繰り返して、2 つ目の操作ウィンドウとラベルを作成します。  2 番目のラベルの **\[Text\]** プロパティは Actions Pane 2 に設定します。  
  
##  <a name="BKMK_CreateCustomTab"></a> カスタム タブの作成  
 Office アプリケーションのデザイン ガイドラインの 1 つとして、ユーザーが常に Office アプリケーションの UI を操作できなければならないことがあります。  操作ウィンドウにこの機能を追加するには、リボンのカスタム タブから操作ウィンドウの表示\/非表示を切り替えることができるボタンを追加します。  カスタム タブを作成するには、プロジェクトに**リボン \(ビジュアル デザイナー\)** 項目を追加します。  デザイナーでは、コントロールの追加と配置、コントロールのプロパティの設定、およびコントロール イベントの処理を行うことができます。  
  
#### カスタム タブを作成するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[リボン \(ビジュアル デザイナー\)\]** をクリックします。  
  
3.  新しいリボンの名前を「**MyRibbon**」に変更し、**\[追加\]** をクリックします。  
  
     リボン デザイナーで **MyRibbon.cs** ファイルまたは **MyRibbon.vb** ファイルが開き、既定のタブとグループが表示されます。  
  
4.  リボン デザイナーで、既定のタブをクリックします。  
  
5.  **\[プロパティ\]** ウィンドウで、**\[ControlId\]** プロパティを展開し、**\[ControlIdType\]** プロパティを **Custom** に設定します。  
  
6.  **\[Label\]** プロパティを「My Custom Tab」に設定します。  
  
7.  リボン デザイナーで **\[group1\]** をクリックします。  
  
8.  **\[プロパティ\]** ウィンドウで、**\[ラベル\]** を Actions Pane Manager に設定します。  
  
9. **ツールボックス**の **\[Office リボン コントロール\]** タブから、ボタンを **group1** にドラッグします。  
  
10. **\[button1\]** をクリックします。  
  
11. **\[プロパティ\]** ウィンドウで、**\[ラベル\]** を Show Actions Pane 1 に設定します。  
  
12. 2 番目のボタンを **group1** に追加し、**\[ラベル\]** プロパティを Show Actions Pane 2 に設定します。  
  
13. **ツールボックス**の **\[Office リボン コントロール\]** タブから、**ToggleButton** コントロールを **group1** にドラッグします。  
  
14. **\[ラベル\]** プロパティを Hide Actions Pane に設定します。  
  
##  <a name="BKMK_HideShowActionsPane"></a> カスタム タブのボタンによる操作ウィンドウの表示\/非表示の切り替え  
 最後の手順で、ユーザーに応答するコードを追加します。  2 つのボタンの <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> イベントと、トグル ボタンの <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> イベントのイベント ハンドラーを追加します。  操作ウィンドウの表示\/非表示を有効にするために、イベント ハンドラーにコードを追加します。  
  
#### カスタム タブのボタンを使用して操作ウィンドウの表示\/非表示を切り替えるには  
  
1.  **ソリューション エクスプローラー**で MyRibbon.cs または MyRibbon.vb のショートカット メニューを開き、**\[コードの表示\]** をクリックします。  
  
2.  `MyRibbon` クラスの先頭に、次のコードを追加します。  このコードにより、操作ウィンドウ オブジェクトが 2 つ作成されます。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#1)]  
  
3.  `MyRibbon_Load` メソッドを次のコードに置き換えます。  このコードにより、<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> コレクションに操作ウィンドウ オブジェクトが追加され、オブジェクトが非表示になります。  さらに、この Visual C\# コードは複数のリボン コントロール イベントにデリゲートをアタッチします。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#2)]  
  
4.  `MyRibbon` クラスに、次の 3 つのイベント ハンドラー メソッドを追加します。  これらのメソッドは、2 つのボタンの <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> イベントと、トグル ボタンの <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> イベントを処理します。  button1 と button2 のイベント ハンドラーにより、別の操作ウィンドウが表示されます。  toggleButton1 のイベント ハンドラーにより、アクティブな操作ウィンドウの表示\/非表示が切り替えられます。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#3)]  
  
## カスタム タブのテスト  
 プロジェクトを実行し、Excel を起動して、リボンに **\[My Custom Tab\]** タブを表示します。  **\[My Custom Tab\]** 内のボタンをクリックして、操作ウィンドウの表示\/非表示を切り替えます。  
  
#### カスタム タブをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  **\[My Custom Tab\]** タブをクリックします。  
  
3.  **\[Custom Actions Pane Manager\]** グループで、**\[Show Actions Pane 1\]** をクリックします。  
  
     操作ウィンドウが表示され、Actions Pane 1 というラベルが表示されます。  
  
4.  **\[Show Actions Pane 2\]** をクリックします。  
  
     操作ウィンドウが表示され、Actions Pane 2 というラベルが表示されます。  
  
5.  **\[Hide Actions Pane\]** をクリックします。  
  
     操作ウィンドウが表示されなくなります。  
  
## 次の手順  
 Office UI をカスタマイズする方法の詳細については、次のトピックで説明します。  
  
-   ドキュメント レベルのカスタマイズにコンテキスト ベースの UI を追加する。  詳細については、「[操作ウィンドウの概要](../vsto/actions-pane-overview.md)」をご覧ください。  
  
-   標準またはカスタムの Microsoft Office Outlook フォームを拡張する。  詳細については、「[チュートリアル : Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)」をご覧ください。  
  
## 参照  
 [実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [Outlook のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法: リボンのタブの位置を変更する](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法 : 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: Backstage ビューにコントロールを追加する](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)  
  
  