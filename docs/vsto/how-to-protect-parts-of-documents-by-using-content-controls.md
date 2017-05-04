---
title: "方法 : コンテンツ コントロールを使用して文書を保護する | Microsoft Docs"
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
  - "コンテンツ コントロール [Visual Studio での Office 開発], 保護 (ドキュメントを)"
  - "ドキュメント保護 [Visual Studio での Office 開発]"
  - "GroupContentControl"
  - "部分的なドキュメント保護 [Visual Studio での Office 開発]"
  - "制限されたアクセス許可 [Visual Studio での Office 開発]"
  - "Word [Visual Studio での Office 開発], 部分的なドキュメント保護"
  - "Word [Visual Studio での Office 開発], 制限されたアクセス許可"
ms.assetid: 50d7286a-7746-446f-8eef-06ceeadc94d0
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 方法 : コンテンツ コントロールを使用して文書を保護する
  ドキュメントの一部を保護することにより、ユーザーがドキュメントのその部分を変更したり削除したりできないようにします。  コンテンツ コントロールを使用して Microsoft Office Word ドキュメントの一部を保護する方法は、いくつかあります。  
  
-   コンテンツ コントロールを保護することができます。  
  
-   コンテンツ コントロールに含まれていないドキュメントの一部を保護することができます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> コンテンツ コントロールの保護  
 デザイン時または実行時に文書レベルのプロジェクト内のコントロールのプロパティを設定することにより、ユーザーがコンテンツ コントロールを編集したり削除したりしないようにすることができます。  
  
 VSTO アドイン プロジェクトを使用して、実行時にドキュメントに追加したコンテンツ コントロールを保護することもできます。  詳細については、「[方法 : Word 文書にコンテンツ コントロールを追加する](../vsto/how-to-add-content-controls-to-word-documents.md)」を参照してください。  
  
#### デザイン時に、コンテンツ コントロールを保護するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされているドキュメントで、保護するコンテンツ コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、次のプロパティのいずれか、または両方を設定します。  
  
    -   ユーザーがコントロールを編集できないようにするには、**\[LockContents\]** を **True** に設定します。  
  
    -   ユーザーがコントロールを削除できないようにするには、**\[LockContentControl\]** を **True** に設定します。  
  
3.  **\[OK\]** をクリックします。  
  
#### 実行時に、コンテンツ コントロールを保護するには  
  
1.  ユーザーがコントロールを編集しないように、コンテンツ コントロールの `LockContents` プロパティを **true** に設定し、また、ユーザーがコントロールを削除しないように、`LockContentControl` プロパティを **true** に設定します。  
  
     次のコード例は、ドキュメント レベル プロジェクト内の 2 つの異なる <xref:Microsoft.Office.Tools.Word.RichTextContentControl> オブジェクトのプロパティ、<xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> と <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> の使用法を示しています。  このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、`ThisDocument_Startup` イベント ハンドラーから `AddProtectedContentControls` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#2)]  
  
     次のコード例は、VSTO アドイン プロジェクト内の 2 つの異なる <xref:Microsoft.Office.Tools.Word.RichTextContentControl> オブジェクトのプロパティ、<xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> と <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> の使用法を示しています。  このコードを実行するには、プロジェクトの `ThisAddIn` クラスにコードを追加し、`ThisAddIn_Startup` イベント ハンドラーから `AddProtectedContentControls` メソッドを呼び出します。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_WordAddInDynamicControls#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#14)]  
  
## コンテンツ コントロールに含まれていないドキュメントの一部の保護  
 ドキュメントのある領域を <xref:Microsoft.Office.Tools.Word.GroupContentControl> に配置することにより、ユーザーがその領域を変更できないようにすることができます。  これは、次のシナリオで役立ちます。  
  
-   コンテンツ コントロールが含まれていない領域を保護する場合。  
  
-   既にコンテンツ コントロールが含まれている領域だが、保護対象のテキストまたはその他のアイテムが、コンテンツ コントロールに含まれていない場合。  
  
> [!NOTE]  
>  埋め込みコンテンツ コントロールを含む <xref:Microsoft.Office.Tools.Word.GroupContentControl> を作成する場合、埋め込みコンテンツ コントロールは自動的には保護されません。  ユーザーが埋め込みコンテンツ コントロールを編集できないようにするには、コントロールの **LockContents** プロパティを使用します。  
  
#### デザイン時にドキュメントのある領域を保護するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされているドキュメントで、保護する領域を選択します。  
  
2.  リボンの **\[開発\]** タブをクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブが表示されていない場合は、最初にこれを表示する必要があります。  詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
3.  **コントロール** グループで、**\[グループ\]** ドロップダウン ボタンをクリックしてから、**\[グループ\]** をクリックします。  
  
     保護された領域を含む <xref:Microsoft.Office.Tools.Word.GroupContentControl> が、プロジェクト内の `ThisDocument` クラスに自動的に生成されます。  グループ コントロールを表す枠線は、デザイン時に表示されますが、実行時に表示される枠線はありません。  
  
#### 実行時にドキュメントの領域を保護するには  
  
1.  プログラムを使用して、保護する領域を選択し、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> メソッドを呼び出すことにより <xref:Microsoft.Office.Tools.Word.GroupContentControl> を作成します。  
  
     ドキュメント レベル プロジェクトの次のコード例は、ドキュメント内の最初の段落にテキストを追加し、最初の段落を選択して <xref:Microsoft.Office.Tools.Word.GroupContentControl> をインスタンス化します。  このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、`ThisDocument_Startup` イベント ハンドラーから `ProtectFirstParagraph` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#1)]  
  
     VSTO アドイン プロジェクトの次のコード例は、アクティブなドキュメント内の最初の段落にテキストを追加し、最初の段落を選択して <xref:Microsoft.Office.Tools.Word.GroupContentControl> をインスタンス化します。  このコードを実行するには、プロジェクトの `ThisAddIn` クラスにコードを追加し、`ThisAddIn_Startup` イベント ハンドラーから `ProtectFirstParagraph` メソッドを呼び出します。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_WordAddInDynamicControls#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#15)]  
  
## 参照  
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [方法 : Word 文書にコンテンツ コントロールを追加する](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  