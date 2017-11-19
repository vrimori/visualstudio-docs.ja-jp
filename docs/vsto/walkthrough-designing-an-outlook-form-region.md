---
title: "チュートリアル: Outlook フォーム領域のデザイン |Microsoft ドキュメント"
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
helpviewer_keywords: form regions [Office development in Visual Studio], creating
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f2d8e1f8ad116bd6db12eca288e567a652e502a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-designing-an-outlook-form-region"></a>チュートリアル : Outlook フォーム領域のデザイン
  カスタム フォーム領域は、標準またはカスタムの Microsoft Office Outlook フォームを拡張します。 このチュートリアルでは、連絡先アイテムのインスペクター ウィンドウに新しいページとして表示するカスタム フォーム領域をデザインします。 このフォーム領域では、アドレス情報を Windows Live Local Search の Web サイトに送信することによって、連絡先に設定された個々の住所の地図を表示します。 フォーム領域の詳細については、次を参照してください。 [Outlook フォーム領域を作成する](../vsto/creating-outlook-form-regions.md)です。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   新しい Outlook VSTO アドイン プロジェクトの作成。  
  
-   VSTO アドイン プロジェクトへのフォーム領域の追加。  
  
-   フォーム領域のレイアウトのデザイン。  
  
-   フォーム領域の動作のカスタマイズ。  
  
-   Outlook フォーム領域のテスト。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] または [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")、このトピックのビデオ版については、次を参照してください。[ビデオ デモ: Outlook フォーム領域のデザイン](http://go.microsoft.com/fwlink/?LinkID=140824)です。  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>新しい Outlook VSTO アドイン プロジェクトの作成  
 まず、基本的な VSTO アドイン プロジェクトを作成します。  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>新しい Outlook VSTO アドイン プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、名前の Outlook VSTO アドイン プロジェクトを作成**MapItAddIn**です。  
  
2.  **[新しいプロジェクト]** ダイアログ ボックスの **[ソリューションのディレクトリを作成]**チェック ボックスをオンにします。  
  
3.  プロジェクトを任意のディレクトリに保存します。  
  
     詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
## <a name="adding-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO アドイン プロジェクトへのフォーム領域の追加  
 Outlook VSTO アドイン ソリューションには、1 つ以上の Outlook フォーム領域アイテムを格納できます。 使用して、プロジェクトにフォーム領域アイテムを追加、**新しい Outlook フォーム領域**ウィザード。  
  
#### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO アドイン プロジェクトにフォーム領域を追加するには  
  
1.  **ソリューション エクスプ ローラー**、select、 **MapItAddIn**プロジェクト。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、 **Outlook フォーム領域**、ファイルの名前**MapIt**、クリックして**追加**です。  
  
     **NewOutlook フォーム領域**ウィザードが起動します。  
  
4.  **フォーム領域を作成する方法を選択** ページで、をクリックして**新しいフォーム領域をデザイン**、順にクリック**次**です。  
  
5.  **を作成するフォーム領域の種類を選択** ページで、をクリックして**個別**、クリックして**次へ**です。  
  
     A*個別*フォーム領域を Outlook フォームを新しいページに追加します。 フォーム領域の種類の詳細については、「 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)」参照してください。  
  
6.  **説明のテキストを指定し、表示設定を選択します。**  ページで、入力**Map It**で、**名前**ボックス。  
  
     この名前は、連絡先アイテムを開いたときにインスペクター ウィンドウのリボンに表示されます。  
  
7.  選択**作成モードのインスペクター内にある**と**読み取りモードのインスペクター**、順にクリック**[次へ]**です。  
  
8.  **このフォーム領域を表示するメッセージ クラスを識別します**] ページでクリア**メール メッセージ**[**にお問い合わせください**、順にクリック**[完了]**.  
  
     MapIt.cs または MapIt.vb ファイルがプロジェクトに追加されます。  
  
## <a name="designing-the-layout-of-the-form-region"></a>フォーム領域のレイアウトのデザイン  
 使用して、フォーム領域を視覚的な開発、*フォーム領域デザイナー*です。 フォーム領域デザイナーの画面にマネージ コントロールをドラッグできます。 デザイナーを使用して、**プロパティ**コントロールのレイアウトと外観を調整するウィンドウです。  
  
#### <a name="to-design-the-layout-of-the-form-region"></a>フォーム領域のレイアウトをデザインするには  
  
1.  **ソリューション エクスプ ローラー**、展開、 **MapItAddIn**プロジェクト、およびフォーム領域デザイナーを開くには、MapIt.cs または MapIt.vb をダブルクリックします。  
  
2.  デザイナーを右クリックし、をクリックして**プロパティ**です。  
  
3.  **プロパティ**ウィンドウで、設定**サイズ**に**664, 469**です。  
  
     これにより、フォーム領域が地図を表示するのに十分な大きさになります。  
  
4.  **[表示]** メニューの **[ツールボックス]**をクリックします。  
  
5.  **コモン コントロール**のタブ、**ツールボックス**、追加、 **WebBrowser**フォーム領域にします。  
  
     **WebBrowser**連絡先に表示されている各住所の地図を表示します。  
  
## <a name="customizing-the-behavior-of-the-form-region"></a>フォーム領域の動作のカスタマイズ  
 フォーム領域の実行時の動作をカスタマイズするには、フォーム領域のイベント ハンドラーにコードを追加します。 このフォーム領域に対して、コードは Outlook アイテムのプロパティを調べ、Map It フォーム領域を表示するかどうかを決定します。 フォーム領域を表示する場合、コードは Windows Live Local Search に接続し、Outlook 連絡先アイテムに設定された各住所の地図を読み込みます。  
  
#### <a name="to-customize-the-behavior-of-the-form-region"></a>フォーム領域の動作をカスタマイズするには  
  
1.  **ソリューション エクスプ ローラー**MapIt.cs または MapIt.vb を右クリックしてをクリックして**コードの表示**です。  
  
     MapIt.cs または MapIt.vb がコード エディターで開きます。  
  
2.  展開して、**フォーム領域ファクトリ**コード領域です。  
  
     `MapItFactory` という名前のフォーム領域ファクトリ クラスが公開されます。  
  
3.  `MapItFactory_FormRegionInitializing` イベント ハンドラーに次のコードを追加します。 このイベント ハンドラーは、ユーザーが連絡先アイテムを開いたときに呼び出されます。 次のコードは、連絡先アイテムに住所が含まれているかどうかを判定します。 このコードを設定、連絡先アイテムに住所が含まれていない場合、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>のプロパティ、<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>クラスを**true**とフォーム領域は表示されません。 それ以外の場合は、VSTO アドインで <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> イベントが発生し、フォーム領域が表示されます。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4.  <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> イベント ハンドラーに次のコードを追加します。 このコードは次のタスクを実行します。  
  
    -   連絡先アイテムの各住所を連結し、URL 文字列を作成します。  
  
    -   <xref:System.Windows.Forms.WebBrowser> オブジェクトの <xref:System.Windows.Forms.WebBrowser.Navigate%2A> メソッドを呼び出し、パラメーターとして URL 文字列を渡します。  
  
     Map It フォーム領域に Local Search の Web サイトが表示され、スクラッチ パッドに各住所が表示されます。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="testing-the-outlook-form-region"></a>Outlook フォーム領域のテスト  
 プロジェクトを実行すると、Visual Studio によって Outlook が開かれます。 連絡先アイテムを開くと、Map It フォーム領域が表示されます。 Map It フォーム領域は、住所が含まれる連絡先アイテムのフォームのページとして表示されます。  
  
#### <a name="to-test-the-map-it-form-region"></a>Map It フォーム領域をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
     Outlook が開きます。  
  
2.  Outlook では、上、**ホーム** タブで、をクリックして**新しい項目**、順にクリック**連絡先**です。  
  
3.  連絡先のフォームでは、次のように入力します。 **Ann Beebe**連絡先としてこの名前を指定すると、し、次の 3 つのアドレスを指定します。  
  
    |住所の種類|アドレス|  
    |------------------|-------------|  
    |**ビジネス**|**4567 Main st. ツーソン, アリゾナ州**|  
    |**ホーム**|**1234 北 st. ツーソン, アリゾナ州**|  
    |**その他**|**3456 Main st. シアトル、ワシントン州**|  
  
4.  連絡先アイテムを保存して閉じます。  
  
5.  開き直す、 **Ann Beebe**連絡先アイテムです。  
  
6.  **表示**アイテムのリボンのグループをクリックして**Map It**を開くには、Map It フォーム領域。  
  
     Map It フォーム領域が開き、Local Search の Web サイトが表示されます。 **ビジネス**、**ホーム**、および**他**アドレス スクラッチ パッドに表示されます。 スクラッチ パッドで、地図を表示する住所を選択します。  
  
## <a name="next-steps"></a>次の手順  
 Outlook アプリケーションの UI をカスタマイズする方法の詳細については、次のトピックを参照してください。  
  
-   Outlook アイテムのリボンをカスタマイズする方法の詳細については、「 [Customizing a Ribbon for Outlook](../vsto/customizing-a-ribbon-for-outlook.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [実行時にフォーム領域へのアクセス](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [Outlook フォーム領域の作成に関するガイドライン](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [チュートリアル: Outlook でデザインしたフォーム領域のインポート](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [方法: フォーム領域を Outlook アドイン プロジェクトに追加します。](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Outlook メッセージ クラスとフォーム領域の関連付け](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Outlook フォーム領域のカスタム動作](../vsto/custom-actions-in-outlook-form-regions.md)   
 [方法: Outlook にフォーム領域が表示されないようにする](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  