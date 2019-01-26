---
title: '方法: コンテンツ コントロールを使用してドキュメントを保護する. します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9f12eb0e43b1868d93a155354756b10b9661e560
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875525"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>方法: コンテンツ コントロールを使用してドキュメントを保護する. します。
  ドキュメントの一部を保護することにより、ユーザーがドキュメントのその部分を変更したり削除したりできないようにします。 コンテンツ コントロールを使用して Microsoft Office Word ドキュメントの一部を保護する方法は、いくつかあります。  
  
- コンテンツ コントロールを保護することができます。  
  
- コンテンツ コントロールに含まれていないドキュメントの一部を保護することができます。  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> コンテンツ コントロールを保護します。  
 ユーザーを編集またはデザイン時または実行時にドキュメント レベルのプロジェクトで、コントロールのプロパティを設定してコンテンツ コントロールを削除を防ぐことができます。  
  
 VSTO アドイン プロジェクトを使用して、実行時にドキュメントに追加したコンテンツ コントロールを保護することもできます。 詳細については、「[方法 :Word 文書にコンテンツ コントロールを追加](../vsto/how-to-add-content-controls-to-word-documents.md)します。  
  
### <a name="to-protect-a-content-control-at-design-time"></a>デザイン時に、コンテンツ コントロールを保護するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされているドキュメントで、保護するコンテンツ コントロールを選択します。  
  
2.  **プロパティ**ウィンドウで、次のプロパティの一方または両方を設定します。  
  
    -   ユーザーがコントロールを編集できないようにする設定**LockContents**に**True**します。  
  
    -   ユーザーがコントロールを削除することを防ぐために次のように設定します。 **[lockcontentcontrol]** に**True**します。  
  
3.  **[OK]** をクリックします。  
  
### <a name="to-protect-a-content-control-at-runtime"></a>実行時にコンテンツ コントロールを保護するには  
  
1.  設定、`LockContents`するコンテンツ コントロールのプロパティ**true** 、コントロールを編集できないようにし、設定、`LockContentControl`プロパティを**true**をユーザーがコントロールを削除することを防ぐためにします。  
  
     次のコード例は、ドキュメント レベル プロジェクト内の 2 つの異なる <xref:Microsoft.Office.Tools.Word.RichTextContentControl> オブジェクトのプロパティ、<xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> と <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> の使用法を示しています。 このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、 `AddProtectedContentControls` イベント ハンドラーから `ThisDocument_Startup` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]  
  
     次のコード例は、VSTO アドイン プロジェクト内の 2 つの異なる <xref:Microsoft.Office.Tools.Word.RichTextContentControl> オブジェクトのプロパティ、<xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> と <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> の使用法を示しています。 このコードを実行するには、プロジェクトの `ThisAddIn` クラスにコードを追加し、 `AddProtectedContentControls` イベント ハンドラーから `ThisAddIn_Startup` メソッドを呼び出します。  
  
     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]  
  
## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>コンテンツ コントロールに含まれていないドキュメントの一部を保護します。  
 ドキュメントのある領域を <xref:Microsoft.Office.Tools.Word.GroupContentControl> に配置することにより、ユーザーがその領域を変更できないようにすることができます。 これは、次のシナリオで役立ちます。  
  
-   コンテンツ コントロールが含まれていない領域を保護する場合。  
  
-   既にコンテンツ コントロールが含まれている領域だが、保護対象のテキストまたはその他のアイテムが、コンテンツ コントロールに含まれていない場合。  
  
> [!NOTE]  
>  コンテンツ コントロールが埋め込まれた <xref:Microsoft.Office.Tools.Word.GroupContentControl> を作成した場合、埋め込まれたコンテンツ コントロールは自動的には保護されません。 ユーザーが埋め込みコンテンツ コントロールを編集できないようにするには、使用、 **LockContents**コントロールのプロパティ。  
  
### <a name="to-protect-an-area-of-a-document-at-design-time"></a>デザイン時にドキュメントのある領域を保護するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされているドキュメントで、保護する領域を選択します。  
  
2.  リボンの **[開発]** タブをクリックします。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
3.  **コントロール**グループで、、**グループ**ドロップダウン ボタン、およびクリック**グループ**します。  
  
     保護された領域を含む <xref:Microsoft.Office.Tools.Word.GroupContentControl> が、プロジェクト内の `ThisDocument` クラスに自動的に生成されます。 デザイン時に、グループ コントロールを表す枠線が表示されるが、実行時に表示される枠線はありません。  
  
### <a name="to-protect-an-area-of-a-document-at-runtime"></a>実行時にドキュメントの領域を保護するには  
  
1.  プログラムを使用して、保護する領域を選択し、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> メソッドを呼び出すことにより <xref:Microsoft.Office.Tools.Word.GroupContentControl> を作成します。  
  
     ドキュメント レベル プロジェクトの次のコード例は、ドキュメント内の最初の段落にテキストを追加し、最初の段落を選択して <xref:Microsoft.Office.Tools.Word.GroupContentControl> をインスタンス化します。 このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、 `ProtectFirstParagraph` イベント ハンドラーから `ThisDocument_Startup` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]  
  
     VSTO アドイン プロジェクトの次のコード例は、アクティブなドキュメント内の最初の段落にテキストを追加し、最初の段落を選択して <xref:Microsoft.Office.Tools.Word.GroupContentControl> をインスタンス化します。 このコードを実行するには、プロジェクトの `ThisAddIn` クラスにコードを追加し、 `ProtectFirstParagraph` イベント ハンドラーから `ThisAddIn_Startup` メソッドを呼び出します。  
  
     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]  
  
## <a name="see-also"></a>関連項目  
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [方法: コンテンツ コントロールを Word 文書に追加します。](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)  
