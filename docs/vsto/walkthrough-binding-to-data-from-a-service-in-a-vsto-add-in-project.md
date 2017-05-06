---
title: "チュートリアル : VSTO アドイン プロジェクトでサービスのデータをバインドする"
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
  - "データベース [Visual Studio での Office 開発]、スクロール (レコードを)"
  - "レコード [Visual Studio での Office 開発]、スクロール"
  - "データ [Visual Studio での Office 開発]、スクロール (データベース レコードを)"
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# チュートリアル : VSTO アドイン プロジェクトでサービスのデータをバインドする
  VSTO アドイン プロジェクトでは、データをホスト コントロールにバインドできます。 このチュートリアルでは、実行時に Microsoft Office の Word ドキュメントにコントロールを追加し、それらのコントロールを MSDN コンテンツ サービスから取得されたデータにバインドして、イベントに応答する方法について説明します。  
  
 **対象:** このトピックの情報は、Word 2010 のアプリケーション レベルのプロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   実行時にドキュメントに <xref:Microsoft.Office.Tools.Word.RichTextContentControl> コントロールを追加する  
  
-   <xref:Microsoft.Office.Tools.Word.RichTextContentControl> コントロールを Web サービスのデータにバインドする  
  
-   <xref:Microsoft.Office.Tools.Word.RichTextContentControl> コントロールの <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> イベントに応答する  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 新規プロジェクトの作成  
 まず、Word VSTO アドイン プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  Visual Basic または C\# のいずれかを使用して、「**MTPS コンテンツ サービス**」という名前の Word VSTO アドイン プロジェクトを作成します。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     `ThisAddIn.vb` または `ThisAddIn.cs` ファイルが Visual Studio で開かれ、プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## Web サービスの追加  
 このチュートリアルでは、「MTPS コンテンツ サービス」という Web サービスを使用します。 この Web サービスは、指定された MSDN の記事を XML 文字列またはプレーンテキストの形式で返します。 返された情報をコンテンツ コントロールに表示する方法については、後の手順で説明します。  
  
#### MTPS コンテンツ サービスをプロジェクトを追加するには  
  
1.  **\[データ\]** メニューの **\[新しいデータ ソースの追加\]** をクリックします。  
  
2.  **データ ソース構成ウィザード**で、**\[サービス\]** をクリックし、**\[次へ\]** をクリックします。  
  
3.  **\[アドレス\]** フィールドに、次の URL を入力します。  
  
     **http:\/\/services.msdn.microsoft.com\/ContentServices\/ContentService.asmx**  
  
4.  **\[検索\]** をクリックします。  
  
5.  **\[名前空間\]** フィールドに「**ContentService**」と入力し、**\[OK\]** をクリックします。  
  
6.  **\[参照の追加ウィザード\]** ダイアログ ボックスで **\[完了\]** をクリックします。  
  
## 実行時のコンテンツ コントロールの追加とデータへのバインディング  
 VSTO アドイン プロジェクトでは、実行時にコントロールを追加してバインドします。 このチュートリアルでは、ユーザーがコントロールの内部をクリックしたときに Web サービスからデータを取得するようにコンテンツ コントロールを構成します。  
  
#### コンテンツ コントロールを追加してデータにバインドするには  
  
1.  `ThisAddIn` クラスで、MTPS コンテンツ サービス、コンテンツ コントロール、およびデータ バインディングのための変数を宣言します。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#2)]  
  
2.  `ThisAddIn` クラスに次のメソッドを追加します。 このメソッドは、アクティブ ドキュメントの先頭に、コンテンツ コントロールを作成します。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#4)]  
  
3.  `ThisAddIn` クラスに次のメソッドを追加します。 このメソッドは、要求を作成して Web サービスに送信するために必要なオブジェクトを初期化します。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#6)]  
  
4.  ユーザーがコンテンツ コントロールの内部をクリックしたときにコンテンツ コントロールに関する MSDN ライブラリ ドキュメントを取得し、そのデータをコンテンツ コントロールにバインドするイベント ハンドラーを作成します。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#5)]  
  
5.  `ThisAddIn_Startup` メソッドから `AddRichTextControlAtRange` および `InitializeServiceObjects` メソッドを呼び出します。 C\# プログラマの場合は、イベント ハンドラーを追加します。  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#3)]  
  
## アドインのテスト  
 Word を開くと、<xref:Microsoft.Office.Tools.Word.RichTextContentControl> コントロールが表示されます。 コントロールの内部をクリックすると、コントロールのテキストが変わります。  
  
#### VSTO アドインをテストするには  
  
1.  **F5** キーを押します。  
  
2.  コンテンツ コントロールの内部をクリックします。  
  
     MTPS コンテンツ サービスから情報がダウンロードされて、コンテンツ コントロール内部に表示されます。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  