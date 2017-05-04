---
title: "リボン オブジェクト モデルの概要 | Microsoft Docs"
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
  - "リボン [Visual Studio での Office 開発], オブジェクト モデル"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# リボン オブジェクト モデルの概要
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] が公開する厳密に型指定されたオブジェクト モデルを使用して、実行時にリボン コントロールのプロパティを取得および設定できます。  たとえば、メニュー コントロールを動的に設定したり、コントロールの表示\/非表示をコンテキストに応じて切り替えたりすることができます。  Office アプリケーションがリボンを読み込む前であれば、タブ、グループ、およびコントロールをリボンに追加することもできます。  詳細については、「[読み取り専用になるプロパティの設定](#SettingReadOnlyProperties)」を参照してください。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 このリボン オブジェクト モデルの主要な要素は、[リボン クラス](#RibbonClass)、[リボン イベント](#RibbonEvents)、および[リボン コントロール クラス](#RibbonControlClasses)です。  
  
##  <a name="RibbonClass"></a> リボン クラス  
 プロジェクトに新しい **\[リボン \(ビジュアルなデザイナー\)\]** 項目を追加すると、Visual Studio によって、プロジェクトに **Ribbon** クラスが追加されます。  **Ribbon** クラスは、<xref:Microsoft.Office.Tools.Ribbon.RibbonBase> クラスを継承します。  
  
 このクラスは、リボン コード ファイルとリボン デザイナー コード ファイルを分割する部分クラスとして位置付けられます。  
  
##  <a name="RibbonEvents"></a> リボン イベント  
 **Ribbon** クラスには、次の 3 つのイベントが含まれています。  
  
|Event|説明|  
|-----------|--------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Office アプリケーションがリボンのカスタマイズを読み込んだときに発生します。  <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> イベント ハンドラーがリボン コード ファイルに自動的に追加されます。  このイベント ハンドラーを使用して、リボンが読み込まれるときにカスタム コードを実行します。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|リボンが読み込まれたときに、リボンのカスタマイズ内のイメージをキャッシュできます。  これにより、リボンのイメージをこのイベント ハンドラーにキャッシュするコードを作成する場合に、パフォーマンスを多少向上させることができます。  詳細については、「<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>」を参照してください。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|リボンのインスタンスを閉じたときに発生します。|  
  
##  <a name="RibbonControlClasses"></a> リボン コントロール  
 <xref:Microsoft.Office.Tools.Ribbon> 名前空間には、**\[ツールボックス\]** の **\[Office リボン コントロール\]** グループに表示される各コントロールの型が含まれています。  
  
 各 `Ribbon` コントロールの型を次の表に示します。  各コントロールの詳細については、「[リボンの概要](../vsto/ribbon-overview.md)」を参照してください。  
  
|コントロール名|クラス名|  
|-------------|----------|  
|**\[ボックス\]**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Gallery**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**グループ**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**ラベル**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon> 名前空間では、<xref:System.Windows.Forms> 名前空間に属するコントロール クラスとの名前の衝突を回避するために、型名にプレフィックス "Ribbon" が追加されています。  
  
 リボン デザイナーにコントロールを追加すると、そのコントロールのクラスがリボン デザイナー コード ファイルにフィールドとして宣言されます。  
  
### リボン コントロールのプロパティを使用する一般的なタスク  
 各 `Ribbon` コントロールには、コントロールへのラベルの割り当てやコントロールの表示\/非表示の切り替えなど、さまざまなタスクの実行に使用できるプロパティが含まれています。  
  
 リボンが読み込まれた後、またはコントロールが動的メニューに追加された後で、プロパティが読み取り専用になることがあります。  詳細については、「[読み取り専用になるプロパティの設定](#SettingReadOnlyProperties)」を参照してください。  
  
 `Ribbon` コントロールのプロパティを使用して実行できる一部のタスクについて、次の表で説明します。  
  
|タスク :|方法 :|  
|-----------|----------|  
|コントロールの表示\/非表示を切り替える。|Visible プロパティを使用します。|  
|コントロールを有効または無効にする。|Enabled プロパティを使用します。|  
|コントロールのサイズを設定する。|ControlSize プロパティを使用します。|  
|コントロールに表示するイメージを取得する。|Image プロパティを使用します。|  
|コントロールのラベルを変更する。|Label プロパティを使用します。|  
|ユーザー定義のデータをコントロールに追加する。|Tag プロパティを使用します。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>、<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>、<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>、<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> コントロール。|Items プロパティを使用します。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>、<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>、<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> のいずれかのコントロールに項目を追加する。|Items プロパティを使用します。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> にコントロールを追加する。|Items プロパティを使用します。<br /><br /> リボンが Office アプリケーションに読み込まれた後で <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> にコントロールを追加する場合は、リボンが Office アプリケーションに読み込まれる前に <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> プロパティを **true** に設定する必要があります。  詳細については、「[読み取り専用になるプロパティの設定](#SettingReadOnlyProperties)」を参照してください。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> 内の選択された項目を取得する。<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> または <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|SelectedItem プロパティを使用します。  <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> では、<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> プロパティを使用します。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab> 上のグループを取得する。|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> プロパティを使用します。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> に表示する行および列の数を指定する。|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> プロパティおよび <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> プロパティを使用します。|  
  
##  <a name="SettingReadOnlyProperties"></a> 読み取り専用になるプロパティの設定  
 リボンが読み込まれる前にのみ設定できるプロパティがあります。  それらのプロパティは次の 3 つの方法で設定できます。  
  
-   Visual Studio の **\[プロパティ\]** ウィンドウ  
  
-   **Ribbon** クラスのコンストラクター  
  
-   プロジェクトの `ThisAddin`、`ThisWorkbook`、または `ThisDocument` クラスの CreateRibbonExtensibilityObject メソッド  
  
 動的メニューにはいくつかの例外があります。  メニューを含むリボンが読み込まれた後であっても、新しいコントロールを作成してそれらのプロパティを設定し、それらのコントロールを実行時に動的メニューに追加できます。  
  
 動的メニューに追加するコントロールのプロパティは、いつでも設定できます。  
  
 詳細については、「[読み取り専用になるプロパティ](#ReadOnlyProperties)」を参照してください。  
  
### リボンのコンストラクターでのプロパティの設定  
 `Ribbon` コントロールのプロパティを **Ribbon** クラスのコンストラクターで設定できます。  このコードは、`InitializeComponent` メソッドの呼び出しの後に置く必要があります。  次のコード例は、現在の時刻が太平洋標準時間 \(UTC\-8\) の 17:00 以降である場合に、新しいボタンをグループに追加します。  
  
 次のコードを追加します。  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/Ribbon1.Designer.vb#1)]  
  
 Visual Studio 2008 からアップグレードした Visual C\# プロジェクトでは、リボン コード ファイルにコンストラクターがあります。  
  
 Visual Basic プロジェクト、または [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] で作成した Visual C\# プロジェクトでは、リボン デザイナー コード ファイルにコンストラクターがあります。  ファイル名は、*YourRibbonItem*.Designer.cs または *YourRibbonItem*.Designer.vb です。  Visual Basic プロジェクトでこのファイルを確認するには、まずソリューション エクスプローラーの **\[すべてのファイルの表示\]** をクリックする必要があります。  
  
### CreateRibbonExtensibilityObject メソッドでのプロパティの設定  
 プロジェクトの `ThisAddin`、`ThisWorkbook`、または `ThisDocument` のいずれかのクラスの CreateRibbonExtensibilityObject メソッドをオーバーライドするときに、`Ribbon` コントロールのプロパティを設定できます。  CreateRibbonExtensibilityObject メソッドの詳細については、[リボンの概要](../vsto/ribbon-overview.md) を参照してください。  
  
 次のコード例は、Excel ブック プロジェクトの `ThisWorkbook` クラスの CreateRibbonExtensibilityObject メソッドでリボンのプロパティを設定します。  
  
 次のコードを追加します。  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/ThisWorkbook.cs#2)]
 [!code-vb[Trin_Ribbon_ObjectModel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/ThisWorkbook.vb#2)]  
  
###  <a name="ReadOnlyProperties"></a> 読み取り専用になるプロパティ  
 リボンが読み込まれる前にのみ設定できるプロパティを次の表に示します。  
  
> [!NOTE]  
>  動的メニューのコントロールのプロパティは、いつでも設定できます。  この場合、次の表の内容は該当しません。  
  
|プロパティ|リボン コントロール クラス|  
|-----------|--------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**動的**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**グループ**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**名前**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**\[位置\]**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**\[タブ\]**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**タイトル**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### Outlook インスペクターに表示されるリボンのプロパティの設定  
 ユーザーがリボンを含むインスペクターを開くたびにリボンの新しいインスタンスが作成されます。  ただし、上の表に示すプロパティは、リボンの最初のインスタンスが作成される前にのみ設定できます。  最初のインスタンスが作成されると、そのインスタンスによって Outlook がリボンの読み込みに使用する XML ファイルを定義するため、これらのプロパティは読み取り専用になります。  
  
 リボンの他のインスタンスが作成されたときにこれらのプロパティを別の値に設定する条件ロジックがある場合、そのコードは何の効果ももたらしません。  
  
> [!NOTE]  
>  Outlook リボンに追加した各コントロールで **\[Name\]** プロパティが設定されるようにしてください。  実行時にコントロールを Outlook リボンに追加する場合は、このプロパティをコードで設定する必要があります。  デザイン時にコントロールを Outlook リボンに追加する場合は、Name プロパティが自動的に設定されます。  
  
## リボン コントロール イベント  
 各コントロール クラスに 1 つ以上のイベントが含まれています。  次の表は、それらのイベントについての説明です。  
  
|イベント|説明|  
|----------|--------|  
|Click|コントロールがクリックされたときに発生します。|  
|TextChanged|編集ボックスまたはコンボ ボックス内のテキストが変更されたときに発生します。|  
|ItemsLoading|コントロールの Items コレクションが Office から要求されたときに発生します。  Office は、コードがコントロールのプロパティを変更するか、<xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> メソッドが呼び出されるまで、Items コレクションをキャッシュします。|  
|ButtonClick|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> または <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 内のボタンがクリックされたときに発生します。|  
|SelectionChanged|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> または <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 内の選択項目が変更されたときに発生します。|  
|DialogLauncherClick|グループの右下にあるダイアログ ランチャー アイコンがクリックされたときに発生します。|  
  
 これらのイベントのイベント ハンドラーには、次の 2 つのパラメーターがあります。  
  
|パラメーター|説明|  
|------------|--------|  
|*sender*|イベントを発生させたコントロールを表す <xref:System.Object>。|  
|*e*|<xref:Microsoft.Office.Core.IRibbonControl> を格納している <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>。  このコントロールを使用すると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって提供されるリボン オブジェクト モデルには用意されていないプロパティにアクセスできます。|  
  
## 参照  
 [実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル : 実行時のリボン コントロールの更新](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Outlook のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法 : 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: Backstage ビューにコントロールを追加する](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [方法 : リボンをリボン デザイナーからリボン XML にエクスポートする](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [方法 : アドインのユーザー インターフェイス エラーを表示する](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  