---
title: "Office プログラミングの共通タスク |Microsoft ドキュメント"
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
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
ms.assetid: 7afc9bad-1d31-486e-beea-91e6d308cd67
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9f3ed53011bca8d3ab7aa4f9d6be8e619ce1b8b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="common-tasks-in-office-programming"></a>Office プログラミングの共通タスク
  このトピックは、Visual Studio を使用した Office ソリューションのプログラミングに共通する質問のうち、次のカテゴリの質問に対する回答を簡単に見つけることができるように構成されています。  
  
-   [セットアップ タスクと一般的なタスク](#projects)。  
  
-   [ユーザー インターフェイスのカスタマイズ タスク](#ui)。  
  
-   [Excel の自動化タスク](#excel)。  
  
-   [Word の自動化タスク](#word)。  
  
-   [データ タスク](#data)。  
  
-   [サーバー側のドキュメント管理タスク](#server)  
  
-   [セキュリティ タスク](#security)  
  
-   [配置タスク](#deployment)  
  
##  <a name="projects"></a> Setup and General Tasks  
  
-   [方法: Visual Studio で Office プロジェクトを作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
-   [方法: Office ソリューションをアップグレードする](http://msdn.microsoft.com/en-us/a269e539-b717-4680-a568-2152b070347e)。  
  
-   [How to: Install Office Primary Interop Assemblies](../vsto/how-to-install-office-primary-interop-assemblies.md)。  
  
-   [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)。  
  
-   [方法: Office プロジェクトでイベント ハンドラーを作成](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
-   [How to: Open Office Solutions without Running Code](../vsto/how-to-open-office-solutions-without-running-code.md)。  
  
-   [How to: Set Up Configuration Information for an Office Solution](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)。  
  
-   [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
-   [How to: Show Add-in User Interface Errors](../vsto/how-to-show-add-in-user-interface-errors.md)。  
  
##  <a name="ui"></a> User Interface Customization Tasks  
  
### <a name="controls-on-documents-and-worksheets"></a>ドキュメントとワークシートに含まれるコントロール  
  
-   [How to: Add Windows Forms Controls to Office Documents](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)。  
  
-   [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md)。  
  
-   [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md)。  
  
-   [How to: Add Windows Forms Controls to Office Documents](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)。  
  
-   [How to: Add Content Controls to Word Documents](../vsto/how-to-add-content-controls-to-word-documents.md)。  
  
-   [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)。  
  
### <a name="task-panes-in-document-level-customizations"></a>ドキュメント レベルのカスタマイズに含まれる作業ウィンドウ  
  
-   [方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)です。  
  
### <a name="task-panes-in-vsto-add-ins"></a>VSTO アドインに含まれる作業ウィンドウ  
  
-   [How to: Add a Custom Task Pane to an Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)。  
  
### <a name="ribbon-customizations"></a>リボンのカスタマイズ  
  
-   [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
-   [方法: リボンのタブの位置を変更](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)です。  
  
-   [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md)。  
  
-   [方法: Backstage ビューにコントロールを追加](../vsto/how-to-add-controls-to-the-backstage-view.md)です。  
  
-   [How to: Export a Ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)。  
  
### <a name="outlook-form-regions"></a>Outlook フォーム領域  
  
-   [How to: Add a Form Region to an Outlook Add-in Project](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
-   [How to: Prevent Outlook from Displaying a Form Region](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)。  
  
### <a name="custom-menus"></a>カスタム メニュー  
  
-   [方法: ショートカット メニューにコマンドを追加](../vsto/how-to-add-commands-to-shortcut-menus.md)です。  
  
##  <a name="excel"></a> Excel Automation Tasks  
  
-   [方法: プログラムによってワークシートのセルに文字列を表示](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md)です。  
  
-   [方法: プログラムによって新しいブックを作成する](../vsto/how-to-programmatically-create-new-workbooks.md)です。  
  
-   [方法: プログラムによってブックを開く](../vsto/how-to-programmatically-open-workbooks.md)です。  
  
-   [方法: プログラムによってブックを保存](../vsto/how-to-programmatically-save-workbooks.md)です。  
  
-   [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)です。  
  
-   [方法: プログラムによって新しいワークシートをブックに追加](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)です。  
  
-   [方法: プログラムによってワークシートを非表示に](../vsto/how-to-programmatically-hide-worksheets.md)です。  
  
-   [方法: プログラムによってブック内のワークシートを移動](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)です。  
  
-   [方法: プログラムによってブックを保護する](../vsto/how-to-programmatically-protect-workbooks.md)です。  
  
-   [方法: プログラムによってワークシートの範囲をコード内を参照してください](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)です。  
  
-   [方法: プログラムによってブック内の範囲にスタイルを適用](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)です。  
  
-   [方法: 選択したセルを含むワークシートの行で書式設定をプログラムで変更](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)です。  
  
-   [方法: プログラムによってワークシートの範囲内のテキストの検索](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)です。  
  
-   [方法: プログラムによってワークシートを印刷](../vsto/how-to-programmatically-print-worksheets.md)です。  
  
-   [方法: プログラムによって Excel の計算を実行](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)です。  
  
-   [方法: プログラムによってワークシートのデータを並べ替える](../vsto/how-to-programmatically-sort-data-in-worksheets.md)です。  
  
##  <a name="word"></a> Word Automation Tasks  
  
-   [方法: プログラムによって新しいドキュメントを作成する](../vsto/how-to-programmatically-create-new-documents.md)です。  
  
-   [方法: プログラムによって既存のドキュメントを開く](../vsto/how-to-programmatically-open-existing-documents.md)です。  
  
-   [方法: プログラムによって文書を保存](../vsto/how-to-programmatically-save-documents.md)です。  
  
-   [方法: プログラムによって文書を閉じる](../vsto/how-to-programmatically-close-documents.md)です。  
  
-   [方法: プログラムによって Word 文書にテキストを挿入](../vsto/how-to-programmatically-insert-text-into-word-documents.md)です。  
  
-   [方法: プログラムによってを定義し、ドキュメントで範囲を選択](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)です。  
  
-   [方法: プログラムによって Word の範囲をリセット文書](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)です。  
  
-   [方法: プログラムによって文書内のテキストを書式設定](../vsto/how-to-programmatically-format-text-in-documents.md)です。  
  
-   [How to: Add XMLNode Controls to Word Documents](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)。  
  
-   [方法: プログラムによってブックマークのテキストを更新](../vsto/how-to-programmatically-update-bookmark-text.md)です。  
  
-   [方法: プログラムによって検索し、文書内のテキストを置換](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)です。  
  
-   [方法: プログラムによって文書を印刷](../vsto/how-to-programmatically-print-documents.md)です。  
  
-   [方法: プログラムによって Word の表を作成する](../vsto/how-to-programmatically-create-word-tables.md)です。  
  
-   [方法: プログラムによって Word の表に行と列を追加](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)です。  
  
-   [方法: 文書内の文字をプログラムでカウント](../vsto/how-to-programmatically-count-characters-in-documents.md)です。  
  
##  <a name="data"></a> Data Tasks  
  
### <a name="data-bound-controls"></a>データ バインド コントロール  
  
-   [How to: Populate Worksheets with Data from a Database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)。  
  
-   [How to: Populate Documents with Data from a Database](../vsto/how-to-populate-documents-with-data-from-a-database.md)。  
  
-   [How to: Populate Documents with Data from Services](../vsto/how-to-populate-documents-with-data-from-services.md)。  
  
-   [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md)。  
  
-   [How to: Populate Documents with Data from a Database](../vsto/how-to-populate-documents-with-data-from-a-database.md)。  
  
-   [How to: Populate Documents with Data from Services](../vsto/how-to-populate-documents-with-data-from-services.md)。  
  
-   [How to: Update a Data Source with Data from a Host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
### <a name="cached-data-in-document-level-solutions"></a>ドキュメント レベルのソリューションでキャッシュされるデータ  
  
-   [How to: Cache Data for Use Offline or on a Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   [How to: Programmatically Cache a Data Source in an Office Document](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)。  
  
-   [How to: Cache Data in a Password-Protected Document](../vsto/how-to-cache-data-in-a-password-protected-document.md)。  
  
### <a name="custom-xml-data"></a>カスタム XML データ  
  
-   [How to: Add Custom XML Parts to Document-Level Customizations](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)。  
  
-   [How to: Add Custom XML Parts to Documents by Using VSTO Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)。  
  
##  <a name="server"></a> Server-side Document Management Tasks  
  
-   [方法: マネージ コード拡張をドキュメントから削除](../vsto/how-to-remove-managed-code-extensions-from-documents.md)です。  
  
-   [方法: マネージ コード拡張機能をドキュメントにアタッチ](../vsto/how-to-attach-managed-code-extensions-to-documents.md)です。  
  
##  <a name="security"></a> Security Tasks  
  
-   [方法: Office ソリューションの署名](../vsto/how-to-sign-office-solutions.md)です。  
  
##  <a name="deployment"></a> Deployment Tasks  
  
-   [方法: ClickOnce を使用して Office ソリューションを発行する](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)。  
  
-   [方法: ClickOnce を使用してドキュメント レベルの Office ソリューションを SharePoint Server に発行する](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58)。  
  
-   [方法: ClickOnce Office ソリューションをインストールする](http://msdn.microsoft.com/en-us/14702f48-9161-4190-994c-78211fe18065)。  
  
-   [方法: Office ソリューションを実行するために、エンド ユーザーのコンピューターに必須コンポーネントをインストールする](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)。  
  
-   [方法: Office ソリューションの配置用に IIS を準備する](http://msdn.microsoft.com/en-us/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4)。  
  
-   [方法: 配置した Office ソリューションを更新する](http://msdn.microsoft.com/en-us/be96db53-b6ea-46ab-b8d9-b76b098b3b13)。  
  
-   [方法: Office ソリューションのインストール パスを変更する](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)。  
  
## <a name="see-also"></a>参照  
 [作業の開始 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office アプリケーションおよびプロジェクト タイプで使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)  
  
  