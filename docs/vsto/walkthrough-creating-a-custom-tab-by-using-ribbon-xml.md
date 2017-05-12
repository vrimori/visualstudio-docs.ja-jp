---
title: "チュートリアル : リボン XML によるカスタム タブの作成"
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
  - "カスタム タブ [Visual Studio での Office 開発]"
  - "カスタマイズ (リボンを), tabscustom リボン, タブ"
  - "リボン [Visual Studio での Office 開発], カスタマイズ"
  - "リボン [Visual Studio での Office 開発], タブ"
  - "リボン [Visual Studio での Office 開発], XML"
  - "XML [Visual Studio での Office 開発], リボン"
ms.assetid: f6391a01-df1a-4a0f-bfbb-a9526c73b2b3
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# チュートリアル : リボン XML によるカスタム タブの作成
  このチュートリアルでは、**リボン \(XML\)** 項目を使用してカスタム リボン タブを作成する方法について説明します。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   **\[アドイン\]** タブへのボタンの追加。  **\[アドイン\]** タブは、リボン XML ファイルで定義されている既定のタブです。  
  
-   **\[アドイン\]** タブ上のボタンを使用した Microsoft Office Word の自動化。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## プロジェクトの作成  
 まず、Word VSTO アドイン プロジェクトを作成します。   後の手順で、このドキュメントの **\[アドイン\]** タブをカスタマイズします。  
  
#### 新しいプロジェクトを作成するには  
  
1.  MyRibbonAddIn という名前の **Word アドイン** プロジェクトを作成します。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」をご覧ください。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、**ThisAddIn.cs** コード ファイルまたは **ThisAddIn.vb** コード ファイルが開き、**ソリューション エクスプローラー**に **MyRibbonAddIn** プロジェクトが追加されます。  
  
## VSTO \[アドイン\] タブの作成  
 **\[アドイン\]** タブを作成するには、**リボン \(XML\)** 項目をプロジェクトに追加します。  このチュートリアルの後半で、このタブにボタンを追加します。  
  
#### \[アドイン\] タブを作成するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[リボン \(XML\)\]** をクリックします。  
  
3.  新しいリボンの名前を "**MyRibbon**" に変更し、**\[追加\]** をクリックします。  
  
     デザイナーに **MyRibbon.cs** ファイルか **MyRibbon.vb** ファイルが開きます。  **MyRibbon.xml** という名前の XML ファイルもプロジェクトに追加されます。  
  
4.  **ソリューション エクスプ ローラー**で、**ThisAddin.cs** または **ThisAddin.vb** を右クリックし、**\[コードの表示\]** をクリックします。  
  
5.  次のコードを **ThisAddin** クラスに追加します。  このコードは、CreateRibbonExtensibilityObject メソッドをオーバーライドし、Office アプリケーションにリボン XML クラスを返します。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  **ソリューション エクスプローラー**で、**MyRibbonAddIn** プロジェクトを右クリックし、**\[ビルド\]** をクリックします。  プロジェクトのビルドでエラーが発生しないことを確認します。  
  
## \[アドイン\] タブへのボタンの追加  
 この VSTO アドインの目的は、定型句や特定の表を作業中のドキュメントに追加する手段をユーザーに提供することです。  このユーザー インターフェイスを提供するには、リボン XML ファイルを変更して、2 つのボタンを **\[アドイン\]** タブに追加します。  このチュートリアルの後半で、これらのボタンのコールバック メソッドを定義します。  リボン XML ファイルの詳細については、「[リボン XML](../vsto/ribbon-xml.md)」をご覧ください。  
  
#### \[アドイン\] タブにボタンを追加するには  
  
1.  **ソリューション エクスプローラー**で **MyRibbon.xml** を右クリックし、**\[開く\]** をクリックします。  
  
2.  **tab** 要素の内容を次の XML に置き換えます。  この XML は、既定のコントロール グループのラベルを **Content** に変更して、**Insert Text** および **Insert Table** というラベルが付いた 2 つのボタンを新しく追加します。  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## ボタンを使用したドキュメントの自動化  
 ユーザーが **\[Insert Text\]** ボタンや **\[Insert Table\]** ボタンをクリックしたときにアクションが実行されるようにするには、これらのボタンの `onAction` コールバック メソッドを追加する必要があります。  リボン コントロールのコールバック メソッドの詳細については、「[リボン XML](../vsto/ribbon-xml.md)」をご覧ください。  
  
#### ボタンのコールバック メソッドを追加するには  
  
1.  **ソリューション エクスプローラー**で **MyRibbon.cs** または **MyRibbon.vb** を右クリックし、**\[開く\]** をクリックします。  
  
2.  **MyRibbon.cs** ファイルまたは **MyRibbon.vb** ファイルの先頭に次のコードを追加します。   このコードによって、<xref:Microsoft.Office.Interop.Word> 名前空間のエイリアスが作成されます。  
  
     [!code-csharp[Trin_RibbonButtons#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonButtons/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonButtons/VB/MyRibbon.vb#1)]  
  
3.  `MyRibbon` クラスに次のメソッドを追加します。  これは **\[Insert Text\]** ボタンのコールバック メソッドで、作業中のドキュメント内のカーソルの現在位置に文字列を追加します。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#2)]  
  
4.  `MyRibbon` クラスに次のメソッドを追加します。  これは **\[Insert Table\]** ボタンのコールバック メソッドで、作業中のドキュメント内のカーソルの現在位置に表を追加します。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#3)]  
  
## VSTO アドインのテスト  
 プロジェクトを実行すると、Word が開き、**\[アドイン\]** タブがリボン上に表示されます。  **\[アドイン\]** タブの **\[Insert Text\]** ボタンと **\[Insert Table\]** ボタンをクリックして、コードをテストします。  
  
#### VSTO アドインをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  **\[アドイン\]** タブがリボンに表示されていることを確認します。  
  
3.  **\[アドイン\]** タブをクリックします。  
  
4.  **\[コンテンツ\]** グループがリボンに表示されていることを確認します。  
  
5.  **\[コンテンツ\]** グループの **\[Insert Text\]** ボタンをクリックします。  
  
     ドキュメント内のカーソルの現在位置に文字列が追加されます。  
  
6.  **\[コンテンツ\]** グループの **\[Insert Table\]** ボタンをクリックします。  
  
     ドキュメント内のカーソルの現在位置に表が追加されます。  
  
## 次の手順  
 Office UI をカスタマイズする方法の詳細については、次のトピックで説明します。  
  
-   別の Office アプリケーションのリボンをカスタマイズする。  リボンのカスタマイズをサポートするアプリケーションの詳細については、「[リボンの概要](../vsto/ribbon-overview.md)」をご覧ください。  
  
-   リボン デザイナーを使用して Office アプリケーションのリボンをカスタマイズする。  詳細については、「[リボン デザイナー](../vsto/ribbon-designer.md)」をご覧ください。  
  
-   カスタム操作ウィンドウを作成する。  詳細については、「[操作ウィンドウの概要](../vsto/actions-pane-overview.md)」をご覧ください。  
  
-   Outlook フォーム領域を使用して Microsoft Office Outlook の UI をカスタマイズする。  詳細については、「[チュートリアル : Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)」をご覧ください。  
  
## 参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  