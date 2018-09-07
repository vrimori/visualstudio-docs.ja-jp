---
title: 'チュートリアル: コンテンツ コントロールを使用してテンプレートを作成します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0f49e2e9e23f19a4346080b0e59435128e33849d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672862"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>チュートリアル: コンテンツ コントロールを使用してテンプレートを作成します。
  このチュートリアルでは、コンテンツ コントロールを使用して、Microsoft Office Word テンプレートで構造化された再利用可能なコンテンツを作成するための、ドキュメント レベルのカスタマイズを作成する方法について説明します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word では、再利用可能な文書パーツ、という名前のコレクションを作成することができます*ビルド ブロック*します。 このチュートリアルでは、文書パーツとして 2 つの表を作成する方法を説明します。 各表には、プレーン テキストや日付などさまざまな種類のコンテンツを保持できる、複数のコンテンツ コントロールが含まれます。 表の 1 つには従業員に関する情報が含まれ、もう一方の表には顧客からのフィードバックが含まれています。  
  
 テンプレートからドキュメントを作成した後に、複数の <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> オブジェクトを使用して、いずれかの表をドキュメントに追加できます。これらのオブジェクトには、テンプレート内で使用できる文書パーツが表示されます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   デザイン時に Word テンプレートで、コンテンツ コントロールが含まれる表を作成する。  
  
-   プログラムを使用して、コンボ ボックス コンテンツ コントロールおよびドロップダウン リスト コンテンツ コントロールのデータを読み込む。  
  
-   特定の表を保護してユーザーが編集できないようにする。  
  
-   表をテンプレートの文書パーツ コレクションに追加する。  
  
-   テンプレートで使用可能な文書パーツを表示するコンテンツ コントロールを作成する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word。  
  
## <a name="create-a-new-word-template-project"></a>新しい Word テンプレート プロジェクトを作成します。  
 ユーザーが独自のコピーを簡単に作成できるように、Word テンプレートを作成します。  
  
### <a name="to-create-a-new-word-template-project"></a>新しい Word テンプレート プロジェクトを作成するには  
  
1.  名前の Word テンプレート プロジェクトを作成**MyBuildingBlockTemplate**します。 ウィザードで、ソリューション内に新しいドキュメントを作成します。 詳細については、次の[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)を参照してください。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーで新しい Word テンプレートを開き、追加、 **MyBuildingBlockTemplate**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="create-the-employee-table"></a>Employee テーブルを作成します。  
 ユーザーが従業員に関する情報を入力できる 4 種類のコンテンツ コントロールが含まれる表を作成します。  
  
### <a name="to-create-the-employee-table"></a>従業員表を作成するには  
  
1.  ホストされている Word テンプレートで、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デザイナーのリボンで、をクリックして、**挿入**タブ。  
  
2.  **テーブル**グループで、**テーブル**、2 つの列と 4 つの行を含むテーブルを挿入します。  
  
3.  最初の列に次のようにテキストを入力します。  
  
    ||  
    |-|  
    |**従業員の名前**|  
    |**採用日**|  
    |**タイトル**|  
    |**画像**|  
  
4.  2 番目の列の最初のセルをクリックします (横に**Employee Name**)。  
  
5.  リボンの **[開発]** タブをクリックします。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、次を参照してください。[方法: リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
6.  **コントロール**グループで、、**テキスト**ボタン![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") を追加する<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>最初のセルにします。  
  
7.  2 番目の列では、2 番目のセルをクリックします (横に**Hire Date**)。  
  
8.  **コントロール**グループで、、**日付選択カレンダー**ボタン![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") を追加するには<xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 2 番目のセルにします。  
  
9. 2 番目の列の 3 番目のセルをクリックします (横に**タイトル**)。  
  
10. **コントロール**グループで、、**コンボ ボックス**ボタン![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") を追加する<xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>3 番目のセルにします。  
  
11. 2 番目の列の最後のセルをクリックします (横に**画像**)。  
  
12. **コントロール**グループで、、**画像コンテンツ コントロール**ボタン![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl")を追加する、<xref:Microsoft.Office.Tools.Word.PictureContentControl>最後のセルにします。  
  
## <a name="create-the-customer-feedback-table"></a>顧客フィードバック表を作成します。  
 ユーザーが顧客のフィードバック情報を入力できる 3 種類のコンテンツ コントロールが含まれる表を作成します。  
  
### <a name="to-create-the-customer-feedback-table"></a>顧客フィードバック表を作成するには  
  
1.  Word テンプレートで、先ほど追加した従業員表の後の行をクリックし、キーを押します**Enter**新しい段落を追加します。  
  
2.  リボンのクリックして、**挿入**タブ。  
  
3.  **テーブル**グループで、**テーブル**、2 つの列と 3 つの行を含むテーブルを挿入します。  
  
4.  最初の列に次のようにテキストを入力します。  
  
    ||  
    |-|  
    |**顧客名**|  
    |**満足度評価**|  
    |**コメント**|  
  
5.  2 番目の列の最初のセルをクリックして (横に**顧客名**)。  
  
6.  リボンの **[開発]** タブをクリックします。  
  
7.  **コントロール**グループで、、**テキスト**ボタン![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") を追加する<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>最初のセルにします。  
  
8.  2 番目の列の 2 つ目のセルをクリックして (横に**満足度評価**)。  
  
9. **コントロール**グループで、、**ドロップ ダウン リスト**ボタン![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl")を追加する、<xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 2 番目のセルにします。  
  
10. 2 番目の列の最後のセルをクリックします (横に**コメント**)。  
  
11. **コントロール**グループで、、**リッチ テキスト**ボタン![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") を追加する<xref:Microsoft.Office.Tools.Word.RichTextContentControl>最後のセルにします。  
  
## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>コンボ ボックスとドロップダウン リストをプログラムで設定します。  
 使用して、デザイン時にコンテンツ コントロールを初期化することができます、**プロパティ**ウィンドウ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 初期状態を動的に設定できるように、実行時にも初期化できます。 このチュートリアルでは、コードを使用して、エントリを作成、<xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>と<xref:Microsoft.Office.Tools.Word.DropDownListContentControl>実行時に表示されるため、これらのオブジェクトの動作します。  
  
### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>コンテンツ コントロールの UI をプログラムで変更するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**ThisDocument.cs**または**ThisDocument.vb**、 をクリックし、**コードの表示**します。  
  
2.  `ThisDocument` クラスに次のコードを追加します。 このコードは、このチュートリアルの後半で使用するいくつかのオブジェクトを宣言します。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  `ThisDocument_Startup` クラスの `ThisDocument` メソッドに次のコード行を追加します。 このコードは表の <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> と <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> にエントリを追加し、ユーザーがコンテンツ コントロールを編集する前に、各コントロールに表示されるプレースホルダー テキストを設定します。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="prevent-users-from-editing-the-employee-table"></a>ユーザーが employee テーブルを編集することを妨げる  
 先ほど宣言した <xref:Microsoft.Office.Tools.Word.GroupContentControl> オブジェクトを使用して、従業員表を保護します。 表を保護した後でも、ユーザーは表内のコンテンツ コントロールを編集できます。 ただし、最初の列のテキストを編集したり、他の方法で表を変更すること (行や列を追加/削除するなど) はできません。 使用する方法についての詳細、<xref:Microsoft.Office.Tools.Word.GroupContentControl>ドキュメントの一部を保護するには、次を参照してください。[コンテンツ コントロール](../vsto/content-controls.md)します。  
  
### <a name="to-prevent-users-from-editing-the-employee-table"></a>従業員表を保護してユーザーが編集できないようにするには  
  
1.  `ThisDocument` クラスの `ThisDocument_Startup` メソッドに (前の手順で追加したコードの後ろに) 次のコードを追加します。 このコードにより、先ほど宣言した <xref:Microsoft.Office.Tools.Word.GroupContentControl> オブジェクト内に表を配置することで、ユーザーが従業員表を編集できないようにします。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="add-the-tables-to-the-building-block-collection"></a>文書パーツ コレクションにテーブルを追加します。  
 作成した表をユーザーがドキュメントに挿入できるように、テンプレート内の文書パーツ コレクションに表を追加します。 文書パーツの詳細については、次を参照してください。[コンテンツ コントロール](../vsto/content-controls.md)します。  
  
### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>テンプレートの文書パーツに表を追加するには  
  
1.  `ThisDocument` クラスの `ThisDocument_Startup` メソッドに (前の手順で追加したコードの後ろに) 次のコードを追加します。 このコードは、テンプレートで再利用可能なすべての構成要素を含む Microsoft.Office.Interop.Word.BuildingBlockEntries コレクションにテーブルを含む新しい文書パーツを追加します。 という名前の新しいカテゴリで、新しい構成要素が定義されている**Employee and Customer Information**ビルディング ブロックの型が割り当てられていると`Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`します。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  `ThisDocument` クラスの `ThisDocument_Startup` メソッドに (前の手順で追加したコードの後ろに) 次のコードを追加します。 このコードは、テンプレートから、表を削除します。 表は、テンプレートの再利用可能な文書パーツのギャラリーに追加されたため、もう必要ありません。 コードは最初にドキュメントをデザイン モードにして、保護されている従業員表を削除できるようにします。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="create-a-content-control-that-displays-the-building-blocks"></a>文書パーツを表示するコンテンツ コントロールを作成します。  
 先ほど作成した文書パーツ (表) へのアクセスを提供するコンテンツ コントロールを作成します。 ユーザーはこのコントロールをクリックして、ドキュメントに表を追加できます。  
  
### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>文書パーツを表示するコンテンツ コントロールを作成するには  
  
1.  `ThisDocument` クラスの `ThisDocument_Startup` メソッドに (前の手順で追加したコードの後ろに) 次のコードを追加します。 このコードは先ほど宣言した <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> オブジェクトを初期化します。 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>カテゴリで定義されているすべての構成要素を表示します。 **Employee and Customer Information**のビルディング ブロックの種類があると`Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`します。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="test-the-project"></a>プロジェクトをテストします。  
 ユーザーはドキュメント内の文書パーツ ギャラリー コントロールをクリックして、従業員表や顧客フィードバック表を挿入できます。 ユーザーは、両方の表内のコンテンツ コントロールで、応答を入力または選択できます。 ユーザーは顧客フィードバック表の他の部分を変更できますが、従業員表の他の部分を変更できてはなりません。  
  
### <a name="to-test-the-employee-table"></a>従業員表をテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  クリックして**最初の文書パーツを選択**最初の文書パーツ ギャラリー コンテンツ コントロールを表示します。  
  
3.  ドロップダウン矢印をクリックして、**カスタム ギャラリー 1**コントロールでは、見出しと選択**Employee テーブル**します。  
  
4.  右にセルをクリックして、 **Employee Name**セルし、名前を入力します。  
  
     このセルにテキストのみを追加できることを確認します。 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> により、ユーザーはテキストのみを追加でき、アートや表など他の種類のコンテンツは追加できません。  
  
5.  右にセルをクリックして、 **Hire Date**セルし、日付の選択で日付を選択します。  
  
6.  右にセルをクリックして、**タイトル**セルし、コンボ ボックスで役職名のいずれかを選択します。  
  
     必要に応じて、リストに含まれていない役職名を入力します。 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ではユーザーがエントリの一覧から選択することも、独自のエントリを入力することもできるため、このようなケースが生じることがあります。  
  
7.  右側にあるセルでアイコンをクリックして、**画像**セルし、それを表示する画像を参照します。  
  
8.  表に行や列を追加できるか、また、表から行や列を削除できるか、試してみます。 表を変更できないことを確認します。 <xref:Microsoft.Office.Tools.Word.GroupContentControl> により、表は変更できないようになっています。  
  
### <a name="to-test-the-customer-feedback-table"></a>顧客フィードバック表をテストするには  
  
1.  をクリックして **、2 つ目の構成要素を選択**を 2 番目の文書パーツ ギャラリー コンテンツ コントロールを表示します。  
  
2.  ドロップダウン矢印をクリックして、**カスタム ギャラリー 1**コントロールでは、見出しと選択**Customer テーブル**します。  
  
3.  右にセルをクリックして、**顧客名**セルし、名前を入力します。  
  
4.  右にセルをクリックして、**満足度評価**セルし、使用可能なオプションのいずれかを選択します。  
  
     独自のエントリを入力できないことを確認します。 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> では、ユーザーはエントリの一覧から選択することのみが可能です。  
  
5.  右にセルをクリックして、**コメント**セルし、いくつかのコメントを入力します。  
  
     必要に応じて、アートや、埋め込み表など、テキスト以外のコンテンツを追加します。 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ではユーザーがテキスト以外のコンテンツを追加できるため、このようなケースが生じることがあります。  
  
6.  表に行や列を追加できること、また、表から行や列を削除できることを確認します。 表を <xref:Microsoft.Office.Tools.Word.GroupContentControl> に配置して保護していないため、表への変更が可能です。  
  
7.  テンプレートを閉じます。  
  
## <a name="next-steps"></a>次の手順  
 コンテンツ コントロールの使用方法の詳細については、次の各トピックを参照してください。  
  
-   コンテンツ コントロールを、文書に埋め込まれている XML の一部 (「カスタム XML 部分」とも呼ばれます) にバインドします。 詳細については、次を参照してください。[チュートリアル: カスタム XML 部分にコンテンツ コントロールをバインド](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)します。  
  
## <a name="see-also"></a>関連項目  
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [方法: Word 文書にコンテンツ コントロールを追加](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [方法: コンテンツ コントロールを使用してドキュメントを保護する.](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  