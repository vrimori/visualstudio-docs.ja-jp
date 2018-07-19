---
title: 'チュートリアル: リボン XML によるカスタム タブを作成します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 45e35b7cf97a6b9a1f310149817f8e79956a47aa
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808925"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>チュートリアル: リボン XML によるカスタム タブを作成します。
  このチュートリアルを使用してカスタム リボン タブを作成する方法について説明、**リボン (XML)** 項目。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   ボタンの追加、**アドイン**タブ。**アドイン**タブがリボン XML ファイルで定義されている既定のタブ。  
  
-   Microsoft Office Word を自動化するボタンを使用して、**アドイン**タブ。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word。  
  
## <a name="create-the-project"></a>プロジェクトの作成  
 まず、Word VSTO アドイン プロジェクトを作成します。 カスタマイズ後で、**アドイン**このドキュメントのタブ。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  作成、 **Word アドイン**という名前のプロジェクト**MyRibbonAddIn**します。  
  
     詳細については、次を参照してください。[方法: Visual Studio でプロジェクトを作成する Office](../vsto/how-to-create-office-projects-in-visual-studio.md)します。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 表示されます、 **ThisAddIn.cs**または**ThisAddIn.vb**コード ファイルのほか、 **MyRibbonAddIn**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="create-the-vsto-add-ins-tab"></a>VSTO [アドイン] タブを作成します。  
 作成する、**アドイン** タブで、追加、**リボン (XML)** 項目をプロジェクトにします。 このチュートリアルの後半で、このタブにボタンを追加します。  
  
### <a name="to-create-the-add-ins-tab"></a>[アドイン] タブを作成するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、**リボン (XML)** します。  
  
3.  新しいリボンの名前を " **MyRibbon**" に変更し、 **[追加]** をクリックします。  
  
     **MyRibbon.cs**または**MyRibbon.vb**ファイルは、デザイナーが開きます。 XML ファイルは、という**MyRibbon.xml**もプロジェクトに追加されます。  
  
4.  **ソリューション エクスプ ローラー**を右クリックして**ThisAddin.cs**または**ThisAddin.vb**、 をクリックし、**コードの表示**します。  
  
5.  次のコードを **ThisAddin** クラスに追加します。 このコードは、`CreateRibbonExtensibilityObject` メソッドをオーバーライドし、Office アプリケーションにリボン XML クラスを返します。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  **ソリューション エクスプ ローラー**を右クリックし、 **MyRibbonAddIn**プロジェクトをクリックして**ビルド**します。 プロジェクトのビルドでエラーが発生しないことを確認します。  
  
## <a name="add-buttons-to-the-add-ins-tab"></a>[アドイン] タブにボタンを追加します。  
 この VSTO アドインの目的は、定型句や特定の表を作業中のドキュメントに追加する手段をユーザーに提供することです。 ユーザー インターフェイスを提供する 2 つのボタンを追加、**アドイン** タブをリボン XML ファイルを変更します。 このチュートリアルの後半で、これらのボタンのコールバック メソッドを定義します。 リボン XML ファイルの詳細については、次を参照してください。[リボン XML](../vsto/ribbon-xml.md)します。  
  
### <a name="to-add-buttons-to-the-add-ins-tab"></a>[アドイン] タブにボタンを追加するには  
  
1.  **ソリューション エクスプ ローラー**、右クリックして**MyRibbon.xml**順にクリックします**オープン**します。  
  
2.  内容を置き換える、**タブ**を次の XML 要素。 この XML に既定のコントロール グループのラベルを変更する**コンテンツ**、というラベルが付いた 2 つの新しいボタンを追加および**Insert Text**と**Insert Table**します。  
  
    ```xml  
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
  
## <a name="automate-the-document-by-using-the-buttons"></a>ボタンを使用して、ドキュメントを自動化します。  
 追加する必要があります`onAction`のコールバック メソッド、 **Insert Text**と**Insert Table**にユーザーがクリックしたときにアクションを実行するボタン。 リボン コントロールのコールバック メソッドの詳細については、次を参照してください。[リボン XML](../vsto/ribbon-xml.md)します。  
  
### <a name="to-add-callback-methods-for-the-buttons"></a>ボタンのコールバック メソッドを追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**MyRibbon.cs**または**MyRibbon.vb**、 をクリックし、**オープン**します。  
  
2.  先頭に次のコードを追加、 **MyRibbon.cs**または**MyRibbon.vb**ファイル。 このコードによって、<xref:Microsoft.Office.Interop.Word> 名前空間のエイリアスが作成されます。  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  `MyRibbon` クラスに次のメソッドを追加します。 これは、コールバック メソッド、 **Insert Text**カーソルの現在の場所にアクティブなドキュメントに文字列を追加するボタン。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  `MyRibbon` クラスに次のメソッドを追加します。 これは、コールバック メソッド、 **Insert Table**カーソルの現在の場所にアクティブなドキュメントにテーブルを追加するボタン。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>VSTO アドインのテスト  
 実行中のプロジェクト、word およびという名前のタブ**アドイン**リボンが表示されます。 をクリックして、 **Insert Text**と**テーブルの挿入**ボタン、**アドイン**タブ コードをテストします。  
  
### <a name="to-test-your-vsto-add-in"></a>VSTO アドインをテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  いることを確認、**アドイン**タブは、リボンに表示されます。  
  
3.  **[アドイン]** タブをクリックします。  
  
4.  いることを確認、**コンテンツ**グループがリボンに表示されます。  
  
5.  をクリックして、 **Insert Text**ボタン、**コンテンツ**グループ。  
  
     ドキュメント内のカーソルの現在位置に文字列が追加されます。  
  
6.  をクリックして、 **Insert Table**ボタン、**コンテンツ**グループ。  
  
     ドキュメント内のカーソルの現在位置に表が追加されます。  
  
## <a name="next-steps"></a>次の手順  
 Office UI をカスタマイズする方法の詳細については、次のトピックで説明します。  
  
-   別の Office アプリケーションのリボンをカスタマイズします。 リボンのカスタマイズをサポートするアプリケーションの詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)します。  
  
-   Office アプリケーションのリボンをカスタマイズするには、リボン デザイナーを使用します。 詳細については、「 [Ribbon Designer](../vsto/ribbon-designer.md)」を参照してください。  
  
-   カスタム操作ウィンドウを作成する。 詳細については、次を参照してください。[操作ウィンドウの概要](../vsto/actions-pane-overview.md)します。  
  
-   Outlook フォーム領域を使用して Microsoft Office Outlook の UI をカスタマイズする。 詳細については、次を参照してください。[チュートリアル: Outlook フォーム領域をデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)します。  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  