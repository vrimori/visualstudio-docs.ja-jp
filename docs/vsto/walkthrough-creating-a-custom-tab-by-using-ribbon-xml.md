---
title: "チュートリアル: リボン XML によるカスタム タブの作成 |Microsoft ドキュメント"
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
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b736ace651854b3b6a527685e150f6f1ec7194c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-ribbon-xml"></a>チュートリアル : リボン XML によるカスタム タブの作成
  このチュートリアルを使用してカスタム リボン タブを作成する方法を示します、**リボン (XML)**項目。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   に対するボタンの追加、**アドイン**タブです。**アドイン**タブは、リボン XML ファイルで定義されている既定のタブです。  
  
-   上のボタンを使用して Microsoft Office Word の自動化、**アドイン**タブです。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 まず、Word VSTO アドイン プロジェクトを作成します。 後でカスタマイズする、**アドイン**このドキュメントのタブです。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  作成、 **Word アドイン**という名前のプロジェクト**MyRibbonAddIn**です。  
  
     詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]開く、 **ThisAddIn.cs**または**ThisAddIn.vb**コード ファイルと追加、 **MyRibbonAddIn**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="creating-the-vsto-add-ins-tab"></a>VSTO [アドイン] タブの作成  
 作成する、**アドイン** タブで、追加、**リボン (XML)**をプロジェクトに項目。 このチュートリアルの後半で、このタブにボタンを追加します。  
  
#### <a name="to-create-the-add-ins-tab"></a>[アドイン] タブを作成するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、**リボン (XML)**です。  
  
3.  新しいリボンの名前を " **MyRibbon**" に変更し、 **[追加]**をクリックします。  
  
     **MyRibbon.cs**または**MyRibbon.vb**ファイルは、デザイナーで開きます。 という XML ファイル**MyRibbon.xml**もプロジェクトに追加されます。  
  
4.  **ソリューション エクスプ ローラー**を右クリックして**ThisAddin.cs**または**ThisAddin.vb**、クリックして**コードの表示**です。  
  
5.  次のコードを **ThisAddin** クラスに追加します。 このコードは、CreateRibbonExtensibilityObject メソッドをオーバーライドし、Office アプリケーションにリボン XML クラスを返します。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  **ソリューション エクスプ ローラー**を右クリックし、 **MyRibbonAddIn**クリックしてプロジェクト**ビルド**です。 プロジェクトのビルドでエラーが発生しないことを確認します。  
  
## <a name="adding-buttons-to-the-add-ins-tab"></a>[アドイン] タブへのボタンの追加  
 この VSTO アドインの目的は、定型句や特定の表を作業中のドキュメントに追加する手段をユーザーに提供することです。 ユーザー インターフェイスを提供するには、2 つのボタンを追加、**アドイン** タブをリボン XML ファイルを変更します。 このチュートリアルの後半で、これらのボタンのコールバック メソッドを定義します。 リボン XML ファイルの詳細については、次を参照してください。[リボン XML](../vsto/ribbon-xml.md)です。  
  
#### <a name="to-add-buttons-to-the-add-ins-tab"></a>[アドイン] タブにボタンを追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**MyRibbon.xml**  をクリックし、**開く**です。  
  
2.  内容を置き換える、**タブ**を次の XML 要素です。 この XML に既定のコントロール グループのラベルを変更する**コンテンツ**、され、ラベルが付いた 2 つの新しいボタンが追加**Insert Text**と**表の挿入**です。  
  
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
  
## <a name="automating-the-document-by-using-the-buttons"></a>ボタンを使用したドキュメントの自動化  
 追加する必要があります`onAction`のコールバック メソッド、 **Insert Text**と**表の挿入**にユーザーがクリックしたときにアクションを実行するボタンです。 リボン コントロールのコールバック メソッドの詳細については、次を参照してください。[リボン XML](../vsto/ribbon-xml.md)です。  
  
#### <a name="to-add-callback-methods-for-the-buttons"></a>ボタンのコールバック メソッドを追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**MyRibbon.cs**または**MyRibbon.vb**、クリックして**開く**です。  
  
2.  先頭に次のコードを追加、 **MyRibbon.cs**または**MyRibbon.vb**ファイル。 このコードによって、<xref:Microsoft.Office.Interop.Word> 名前空間のエイリアスが作成されます。  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  `MyRibbon` クラスに次のメソッドを追加します。 これは、コールバック メソッドを**Insert Text**文字列をカーソルの現在の場所で作業中の文書に追加するボタンです。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  `MyRibbon` クラスに次のメソッドを追加します。 これは、コールバック メソッドを**表の挿入**アクティブなドキュメント内のカーソルの現在の場所に、テーブルを追加するボタンです。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>VSTO アドインのテスト  
 プロジェクト、word およびという名前のタブを実行すると**アドイン**リボンに表示されます。 をクリックして、 **Insert Text**と**表の挿入**ボタンを**アドイン**タブは、コードをテストします。  
  
#### <a name="to-test-your-vsto-add-in"></a>VSTO アドインをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  いることを確認、**アドイン** タブがリボンに表示します。  
  
3.  **[アドイン]** タブをクリックします。  
  
4.  いることを確認、**コンテンツ**グループは、リボンに表示します。  
  
5.  クリックして、 **Insert Text**ボタンをクリックして、**コンテンツ**グループ。  
  
     ドキュメント内のカーソルの現在位置に文字列が追加されます。  
  
6.  クリックして、**表の挿入**ボタンをクリックして、**コンテンツ**グループ。  
  
     ドキュメント内のカーソルの現在位置に表が追加されます。  
  
## <a name="next-steps"></a>次の手順  
 Office UI をカスタマイズする方法の詳細については、次のトピックで説明します。  
  
-   別の Office アプリケーションのリボンをカスタマイズする。 リボンのカスタマイズをサポートするアプリケーションの詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。  
  
-   リボン デザイナーを使用して Office アプリケーションのリボンをカスタマイズする。 詳細については、「 [Ribbon Designer](../vsto/ribbon-designer.md)」を参照してください。  
  
-   カスタム操作ウィンドウを作成する。 詳細については、「 [Actions Pane Overview](../vsto/actions-pane-overview.md)」を参照してください。  
  
-   Outlook フォーム領域を使用して Microsoft Office Outlook の UI をカスタマイズする。 詳細については、次を参照してください。[チュートリアル: Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)です。  
  
## <a name="see-also"></a>参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル: リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  