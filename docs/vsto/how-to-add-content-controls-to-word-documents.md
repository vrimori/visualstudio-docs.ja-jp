---
title: '方法: コンテンツの追加を Word 文書にコントロール'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8a7f99768236c8945fe82645c70c586361edcdde
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648047"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>方法: コンテンツの追加を Word 文書にコントロール
  ドキュメント レベルの Word プロジェクト デザイン時または実行時に、プロジェクト内の文書にコンテンツ コントロールを追加できます。 Word の VSTO アドイン プロジェクトでは、実行時に開いている文書にコンテンツ コントロールを追加できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 このトピックでは、次のタスクについて説明します。  
  
- [デザイン時にコンテンツ コントロールを追加します。](#designtime)  
  
- [ドキュメント レベルのプロジェクトの実行時にコンテンツ コントロールを追加します。](#runtimedoclevel)  
  
- [VSTO アドイン プロジェクトでの実行時にコンテンツ コントロールを追加します。](#runtimeaddin)  
  
  コンテンツ コントロールについて詳しくは、次を参照してください。[コンテンツ コントロール](../vsto/content-controls.md)します。  
  
##  <a name="designtime"></a> コンテンツを追加するデザイン時コントロール  
 デザイン時にドキュメント レベルのプロジェクトの文書にコンテンツ コントロールを追加する方法はいくつかあります。  
  
- **[ツールボックス]** の **[Word コントロール]** タブからコンテンツ コントロールを追加する。  
  
- Word でネイティブなコンテンツ コントロールを追加するのと同様に、ドキュメントにコンテンツ コントロールを追加します。  
  
- **[データ ソース]** ウィンドウからコンテンツ コントロールを文書にドラッグする。 これは、コントロールの作成時にデータにコントロールをバインドする場合に役立ちます。 詳細については、「[方法 :オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)と[方法。データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)します。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>[ツールボックス] を使用して文書にコンテンツ コントロールを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされているドキュメントで、コンテンツ コントロールを追加する場所にカーソルを置くか、または、テキストを置換するコンテンツ コントロールを選択します。  
  
2.  **[ツールボックス]** を開き、 **[Word コントロール]** タブをクリックします。  
  
3.  次のいずれかの方法でコントロールを追加します。  
  
    -   **[ツールボックス]** のコンテンツ コントロールをダブルクリックします。  
  
         または  
  
    -   コンテンツ コントロールをクリックして、**ツールボックス**を押し、 **」と入力**キー。  
  
         または  
  
    -   **[ツールボックス]** からコンテンツ コントロールを文書にドラッグします。 コンテンツ コントロールが、マウス ポインターの場所ではなく、ドキュメント内の現在の選択の場所で追加されます。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.GroupContentControl> [ツールボックス] **を使用して**を追加することはできません。 のみを追加することができます、 <xref:Microsoft.Office.Tools.Word.GroupContentControl> Word で、または実行時にします。  
  
> [!NOTE]  
>  Visual Studio では、チェック ボックス コンテンツ コントロールがツールボックスで提供されていません。 文書にチェック ボックス コンテンツ コントロールを追加するには、プログラムを使用して <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成する必要があります。 詳細については、次を参照してください。[コンテンツ コントロール](../vsto/content-controls.md)します。  
  
#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Word で文書にコンテンツ コントロールを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされているドキュメントで、コンテンツ コントロールを追加する場所にカーソルを置くか、または、テキストを置換するコンテンツ コントロールを選択します。  
  
2.  リボンの **[開発]** タブをクリックします。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
3.  **[コントロール]** グループで、追加するコンテンツ コントロールのアイコンをクリックします。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベルのプロジェクトの実行時にコンテンツ コントロールを追加します。  
 コンテンツ コントロールのメソッドを使用して実行時にドキュメントをプログラムで追加できます、<xref:Microsoft.Office.Tools.Word.Document.Controls%2A>のプロパティ、`ThisDocument`プロジェクト内のクラス。 各メソッドには 3 つのオーバーロードがあります。それらを使用することにより、次のようにコンテンツ コントロールを追加できます。  
  
- 現在の選択項目でコントロールを追加します。  
  
- 指定された範囲にコントロールを追加します。  
  
- 文書内のネイティブなコンテンツ コントロールに基づいたコントロールを追加します。  
  
  動的に作成されたコンテンツ コントロールは、文書を閉じる際に文書に残りません。 ただし、ネイティブなコンテンツ コントロールは、文書内に残ります。 文書を次回開くときに、ネイティブのコンテンツ コントロールに基づくコンテンツ コントロールを再作成できます。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
> [!NOTE]  
>  Word 2010 プロジェクトで文書にチェック ボックス コンテンツ コントロールを追加するには、 <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成する必要があります。 詳細については、次を参照してください。[コンテンツ コントロール](../vsto/content-controls.md)します。  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>現在の選択項目でコンテンツ コントロールを追加するには  
  
1.  使用して、<xref:Microsoft.Office.Tools.Word.ControlCollection>メソッドの名前を持つ`Add` \<*コントロール クラス*> (場所*コントロール クラス*など、追加するコンテンツコントロールのクラス名は、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>)、新しいコントロールの名前の単一のパラメーターを持つとします。  
  
     次のコード例では、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用して文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加しています。 このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、 `AddRichTextControlAtSelection` イベント ハンドラーから `ThisDocument_Startup` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>指定された範囲にコンテンツ コントロールを追加するには  
  
1.  使用して、<xref:Microsoft.Office.Tools.Word.ControlCollection>メソッドの名前を持つ`Add` \<*コントロール クラス*> (場所*コントロール クラス*など、追加するコンテンツコントロールクラスの名前を指定します<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>) を持つ、<xref:Microsoft.Office.Interop.Word.Range>パラメーター。  
  
     次のコード例では、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用して文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加しています。 このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、 `AddRichTextControlAtRange` イベント ハンドラーから `ThisDocument_Startup` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]  
  
### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>ネイティブなコンテンツ コントロールに基づいたコンテンツ コントロールを追加するには  
  
1.  使用して、<xref:Microsoft.Office.Tools.Word.ControlCollection>メソッドの名前を持つ`Add` \<*コントロール クラス*> (場所*コントロール クラス*など、追加するコンテンツコントロールクラスの名前を指定します<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>) を持つ、`Microsoft.Office.Interop.Word.ContentControl`パラメーター。  
  
     次のコード例では、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用して、ドキュメント内にあるすべてのネイティブなリッチ テキスト コントロールについて新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を作成しています。 このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、 `CreateRichTextControlsFromNativeControls` イベント ハンドラーから `ThisDocument_Startup` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクトでの実行時にコンテンツ コントロールを追加します。  
 VSTO アドインを使用して実行時に開いている文書をプログラムでコンテンツ コントロールを追加できます。 そのためには、開いている文書に基づいた <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を生成し、このホスト項目の <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> プロパティのメソッドを使用します。 各メソッドには 3 つのオーバーロードがあります。それらを使用することにより、次のようにコンテンツ コントロールを追加できます。  
  
- 現在の選択項目でコントロールを追加します。  
  
- 指定された範囲にコントロールを追加します。  
  
- 文書内のネイティブなコンテンツ コントロールに基づいたコントロールを追加します。  
  
  動的に作成されたコンテンツ コントロールは、文書を閉じる際に文書に残りません。 ただし、ネイティブなコンテンツ コントロールは、文書内に残ります。 文書を次回開くときに、ネイティブのコンテンツ コントロールに基づくコンテンツ コントロールを再作成できます。 詳細については、次を参照してください。 [Office ドキュメントでのダイナミック コントロールを永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)します。  
  
  VSTO アドイン プロジェクトでホスト項目の生成の詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  
  
> [!NOTE]  
>  文書にチェック ボックス コンテンツ コントロールを追加するには、 <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成する必要があります。 詳細については、次を参照してください。[コンテンツ コントロール](../vsto/content-controls.md)します。  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>現在の選択項目でコンテンツ コントロールを追加するには  
  
1.  使用して、<xref:Microsoft.Office.Tools.Word.ControlCollection>メソッドの名前を持つ`Add` \<*コントロール クラス*> (場所*コントロール クラス*など、追加するコンテンツコントロールのクラス名は、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>)、新しいコントロールの名前の単一のパラメーターを持つとします。  
  
     次のコード例では、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用してアクティブな文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加しています。 このコードを実行するには、プロジェクトの `ThisAddIn` クラスにコードを追加し、 `AddRichTextControlAtSelection` イベント ハンドラーから `ThisAddIn_Startup` メソッドを呼び出します。  
  
     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>指定された範囲にコンテンツ コントロールを追加するには  
  
1.  使用して、<xref:Microsoft.Office.Tools.Word.ControlCollection>メソッドの名前を持つ`Add` \<*コントロール クラス*> (場所*コントロール クラス*など、追加するコンテンツコントロールクラスの名前を指定します<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>) を持つ、<xref:Microsoft.Office.Interop.Word.Range>パラメーター。  
  
     次のコード例では、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用してアクティブな文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加しています。 このコードを実行するには、プロジェクトの `ThisAddIn` クラスにコードを追加し、 `AddRichTextControlAtRange` イベント ハンドラーから `ThisAddIn_Startup` メソッドを呼び出します。  
  
     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>ネイティブなコンテンツ コントロールに基づいたコンテンツ コントロールを追加するには  
  
1.  使用して、<xref:Microsoft.Office.Tools.Word.ControlCollection>メソッドの名前を持つ`Add` \<*コントロール クラス*> (場所*コントロール クラス*など、追加するコンテンツコントロールクラスの名前を指定します<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>) を持つ、`Microsoft.Office.Interop.Word.ContentControl`パラメーター。  
  
     次のコード例では、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用して、文書を開いた後に文書内にあるすべてのネイティブなリッチ テキスト コントロールについて、新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を作成しています。 このコードを実行するには、プロジェクトの `ThisAddIn` クラスに次のコードを追加します。  
  
     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]  
  
     C# の場合、 `Application_DocumentOpen` イベント ハンドラーを <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> イベントに接続する必要もあります。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>関連項目  
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [プログラムのドキュメント レベルのカスタマイズ](../vsto/programming-document-level-customizations.md)  
  