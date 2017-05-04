---
title: "実行時におけるフォーム領域へのアクセス | Microsoft Docs"
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
  - "インスペクター [Visual Studio での Office 開発]"
  - "エクスプローラー [Visual Studio での Office 開発]"
  - "フォーム領域 [Visual Studio での Office 開発]、アクセス (実行時の)"
ms.assetid: 58eaa9e0-acba-4a13-a6dd-b7e37a38156e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 実行時におけるフォーム領域へのアクセス
  
  
|対象|  
|--------|  
|このトピックの情報は、次の種類のプロジェクトおよび Microsoft Office のバージョンにのみ適用されます。 詳細については、「[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。<br /><br /> **プロジェクトの種類**<br /><br /> -   VSTO アドイン プロジェクト<br /><br /> **Microsoft Office のバージョン**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  
  
 `Globals` クラスを使用すると、Outlook プロジェクトの任意の場所からフォーム領域にアクセスできます。`Globals` クラスの詳細については、「[Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)」を参照してください。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 特定の Outlook インスペクター ウィンドウに表示されるフォーム領域へのアクセス  
 特定の Outlook インスペクターに表示されるすべてのフォーム領域にアクセスするには、`Globals` クラスの `FormRegions` プロパティを呼び出し、インスペクターを表す <xref:Microsoft.Office.Interop.Outlook.Inspector> オブジェクトを渡します。  
  
 次の例では、現在フォーカスが設定されているインスペクターに表示されるフォーム領域のコレクションを取得します。 この例では、次に、`formRegion1` というコレクション内のフォーム領域にアクセスし、テキスト ボックス内のテキストを `Hello World` に設定します。  
  
 [!code-csharp[Trin_Outlook_FR_Access#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_Outlook_FR_Access#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#2)]  
  
## 特定の Outlook エクスプローラー ウィンドウに表示されるフォーム領域へのアクセス  
 特定の Outlook エクスプローラーに表示されるすべてのフォーム領域にアクセスするには、`Globals` クラスの `FormRegions` プロパティを呼び出し、エクスプローラーを表す <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトを渡します。  
  
 次の例では、現在フォーカスが設定されているエクスプローラーに表示されるフォーム領域のコレクションを取得します。 この例では、次に、`formRegion1` というコレクション内のフォーム領域にアクセスし、テキスト ボックス内のテキストを `Hello World` に設定します。  
  
 [!code-csharp[Trin_Outlook_FR_Access#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#3)]
 [!code-vb[Trin_Outlook_FR_Access#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#3)]  
  
## すべてのフォーム領域へのアクセス  
 すべてのエクスプローラーおよびすべてのインスペクターに表示されるすべてのフォーム領域にアクセスするには、`Globals` クラスの `FormRegions` プロパティを呼び出します。  
  
 次の例では、すべてのエクスプローラーおよびすべてのインスペクターに表示されるフォーム領域のコレクションを取得します。 この例では、次に、`formRegion1` というフォーム領域にアクセスし、テキスト ボックス内のテキストを `Hello World` に設定します。  
  
 [!code-csharp[Trin_Outlook_FR_Access#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_Outlook_FR_Access#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#1)]  
  
## フォーム領域のコントロールへのアクセス  
 `Globals` クラスを使用してフォーム領域のコントロールにアクセスするには、それらのコントロールを、フォーム領域コード ファイルの外部にあるコードからアクセスできるようにする必要があります。  
  
### フォーム領域デザイナーでデザインされたフォーム領域  
 C\# の場合は、アクセス対象にする各コントロールの修飾子を変更します。 この操作を行うには、フォーム領域デザイナーで各コントロールを選択し、**\[プロパティ\]** ウィンドウで **Modifiers** プロパティを **Internal** または **public** に変更します。 たとえば、`textBox1` の **Modifier** プロパティを **Internal** に変更すると、`Globals.FormRegions.FormRegion1.textBox1` と入力して `textBox1` にアクセスできます。  
  
 Visual Basic の場合は、修飾子を変更する必要はありません。  
  
### インポートされたフォーム領域  
 Outlook でデザインされたフォーム領域をインポートすると、フォーム領域上の各コントロールのアクセス修飾子はプライベートになります。 インポートされたフォーム領域をフォーム領域デザイナーで変更することはできないため、**\[プロパティ\]** ウィンドウでコントロールの修飾子を変更する方法はありません。  
  
 フォーム領域コード ファイルの外部からコードにアクセスできるようにするには、フォーム領域コード ファイルに、そのコントロールを返すプロパティを作成します。  
  
 C\# でプロパティを作成する方法の詳細については、「[方法: 読み取り&#47;書き込みのプロパティの宣言と使用 &#40;C&#35; プログラミング ガイド&#41;](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20(C%23%20Programming%20Guide).md)」を参照してください。  
  
 Visual Basic でプロパティを作成する方法の詳細については、[「方法: フィールドおよびプロパティをクラスに追加する」](http://msdn.microsoft.com/ja-jp/ae53f61b-3abc-413e-8931-703c5f5e8fc2)を参照してください。  
  
## 参照  
 [Outlook フォーム領域の作成に関するガイドライン](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [チュートリアル : Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Outlook フォーム領域のカスタム動作](../vsto/custom-actions-in-outlook-form-regions.md)   
 [フォーム領域の Outlook メッセージ クラスへの関連付け](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [チュートリアル : Outlook でデザインしたフォーム領域のインポート](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [方法 : Outlook にフォーム領域が表示されないようにする](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  