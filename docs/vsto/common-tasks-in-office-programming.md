---
title: Office プログラミングで一般的なタスク
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a92a0e9cc8c82345e1d8a57449317f8e6937dad6
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671939"
---
# <a name="common-tasks-in-office-programming"></a>Office プログラミングで一般的なタスク
  このトピックは、Visual Studio を使用した Office ソリューションのプログラミングに共通する質問のうち、次のカテゴリの質問に対する回答を簡単に見つけることができるように構成されています。  
  
-   [セットアップ タスクと一般的なタスク](#projects)。  
  
-   [ユーザー インターフェイスのカスタマイズ タスク](#ui)。  
  
-   [Excel の自動化タスク](#excel)。  
  
-   [Word の自動化タスク](#word)。  
  
-   [データ タスク](#data)。  
  
-   [サーバー側のドキュメント管理タスク](#server)  
  
-   [セキュリティ タスク](#security)  
  
-   [配置タスク](#deployment)  
  
##  <a name="projects"></a> セットアップと一般的なタスク  
  
-   [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
-   [方法: アップグレードの Office ソリューション](http://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)します。  
  
-   [方法: Office プライマリ相互運用機能アセンブリ](../vsto/how-to-install-office-primary-interop-assemblies.md)します。  
  
-   [方法: ターゲットの Office アプリケーション プライマリ相互運用機能アセンブリを介して](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)します。  
  
-   [方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
-   [方法: Open Office ソリューションのコードを実行することがなく](../vsto/how-to-open-office-solutions-without-running-code.md)します。  
  
-   [方法: Office ソリューションの構成情報を設定](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)します。  
  
-   [方法: リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
-   [方法: ユーザー インターフェイスのエラーを表示するアドイン](../vsto/how-to-show-add-in-user-interface-errors.md)します。  
  
##  <a name="ui"></a> ユーザー インターフェイスのカスタマイズ タスク  
  
### <a name="controls-on-documents-and-worksheets"></a>文書やワークシート上のコントロール  
  
-   [方法: Windows フォーム コントロールを Office ドキュメントに追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)します。  
  
-   [方法: ワークシートに NamedRange コントロールを追加](../vsto/how-to-add-namedrange-controls-to-worksheets.md)します。  
  
-   [方法: ワークシートに ListObject コントロールを追加](../vsto/how-to-add-listobject-controls-to-worksheets.md)します。  
  
-   [方法: Windows フォーム コントロールを Office ドキュメントに追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)します。  
  
-   [方法: コンテンツを追加するコントロールを Word 文書に](../vsto/how-to-add-content-controls-to-word-documents.md)します。  
  
-   [方法: Word 文書に Bookmark コントロールを追加](../vsto/how-to-add-bookmark-controls-to-word-documents.md)します。  
  
### <a name="task-panes-in-document-level-customizations"></a>ドキュメント レベルのカスタマイズでの作業ウィンドウ  
  
-   [方法: Word 文書に操作ウィンドウを追加したり、Excel ブック](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)します。  
  
### <a name="task-panes-in-vsto-add-ins"></a>VSTO アドインで作業ウィンドウ  
  
-   [方法: カスタム作業ウィンドウをアプリケーションに追加](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)します。  
  
### <a name="ribbon-customizations"></a>リボンのカスタマイズ  
  
-   [方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)します。  
  
-   [方法: リボンのタブの位置を変更](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)します。  
  
-   [方法: 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)します。  
  
-   [方法: Backstage ビューにコントロールを追加](../vsto/how-to-add-controls-to-the-backstage-view.md)します。  
  
-   [方法: リボンをリボン デザイナーからリボン XML にエクスポートする](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)。  
  
### <a name="outlook-form-regions"></a>Outlook フォーム領域  
  
-   [方法: フォーム領域を Outlook アドイン プロジェクトに追加](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)します。  
  
-   [方法: Outlook フォーム領域が表示されないようにする](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)します。  
  
### <a name="custom-menus"></a>カスタム メニュー  
  
-   [方法: ショートカット メニュー コマンドを追加](../vsto/how-to-add-commands-to-shortcut-menus.md)します。  
  
##  <a name="excel"></a> Excel の自動化タスク  
  
-   [方法: プログラムによってワークシートのセルに文字列を表示](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md)します。  
  
-   [方法: プログラムによって新しいブックを作成](../vsto/how-to-programmatically-create-new-workbooks.md)です。  
  
-   [方法: プログラムによってブックを開く](../vsto/how-to-programmatically-open-workbooks.md)します。  
  
-   [方法: プログラムによってブックを保存](../vsto/how-to-programmatically-save-workbooks.md)します。  
  
-   [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)します。  
  
-   [方法: プログラムによって新しいワークシートをブックに追加](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)します。  
  
-   [方法: プログラムによってワークシートを非表示に](../vsto/how-to-programmatically-hide-worksheets.md)します。  
  
-   [方法: プログラムによってブック内のワークシートを移動](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)します。  
  
-   [方法: プログラムによってブックを保護](../vsto/how-to-programmatically-protect-workbooks.md)します。  
  
-   [方法: プログラムによってコード内でワークシートの範囲を参照](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)します。  
  
-   [方法: プログラムによってブック内の範囲にスタイルを適用](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)します。  
  
-   [方法: 選択したセルを含むワークシートの行の書式設定をプログラムで変更](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)します。  
  
-   [方法: プログラムによってワークシートの範囲内のテキストを検索](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)します。  
  
-   [方法: プログラムによってワークシートを印刷する](../vsto/how-to-programmatically-print-worksheets.md)します。  
  
-   [方法: プログラムによって Excel の計算を実行](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)します。  
  
-   [方法: プログラムによってワークシートのデータを並べ替える](../vsto/how-to-programmatically-sort-data-in-worksheets.md)します。  
  
##  <a name="word"></a> Word の自動化タスク  
  
-   [方法: プログラムによって新しい文書を作成](../vsto/how-to-programmatically-create-new-documents.md)です。  
  
-   [方法: プログラムによって既存文書を開く](../vsto/how-to-programmatically-open-existing-documents.md)します。  
  
-   [方法: プログラムによってドキュメントを保存](../vsto/how-to-programmatically-save-documents.md)します。  
  
-   [方法: プログラムによって文書を閉じる](../vsto/how-to-programmatically-close-documents.md)します。  
  
-   [方法: プログラムによって Word 文書にテキストを挿入](../vsto/how-to-programmatically-insert-text-into-word-documents.md)します。  
  
-   [方法: プログラムで定義し、ドキュメントで範囲を選択](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)します。  
  
-   [方法: プログラムによって Word のドキュメント内の範囲をリセット](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)します。  
  
-   [方法: プログラムによって文書内のテキストを書式設定](../vsto/how-to-programmatically-format-text-in-documents.md)します。  
  
-   [方法: Word 文書に XMLNode コントロールを追加](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)します。  
  
-   [方法: プログラムによってブックマークのテキストを更新](../vsto/how-to-programmatically-update-bookmark-text.md)します。  
  
-   [方法: プログラムによって検索し、文書内のテキストを置換](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)します。  
  
-   [方法: プログラムによってドキュメントを印刷](../vsto/how-to-programmatically-print-documents.md)します。  
  
-   [方法: プログラムによって Word の表を作成](../vsto/how-to-programmatically-create-word-tables.md)です。  
  
-   [方法: プログラムによって Word の表に行と列を追加](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)します。  
  
-   [方法: プログラムによって文書内の文字をカウント](../vsto/how-to-programmatically-count-characters-in-documents.md)します。  
  
##  <a name="data"></a> データ タスク  
  
### <a name="data-bound-controls"></a>データ バインド コントロール  
  
-   [方法: データベースからデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)します。  
  
-   [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)します。  
  
-   [方法: データ サービスからドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)します。  
  
-   [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)します。  
  
-   [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)します。  
  
-   [方法: データ サービスからドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)します。  
  
-   [方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)します。  
  
### <a name="cached-data-in-document-level-solutions"></a>ドキュメント レベルのソリューションでキャッシュされたデータ  
  
-   [方法: オフラインか、サーバーで使用するデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)します。  
  
-   [方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュ](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)します。  
  
-   [方法: パスワードで保護されたドキュメント内のデータをキャッシュ](../vsto/how-to-cache-data-in-a-password-protected-document.md)します。  
  
### <a name="custom-xml-data"></a>カスタムの XML データ  
  
-   [方法: ドキュメント レベルのカスタマイズにカスタム XML 部分を追加する](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)します。  
  
-   [方法: VSTO アドインを使用して、カスタム XML 部分をドキュメントに追加](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)します。  
  
##  <a name="server"></a> サーバー側のドキュメント管理タスク  
  
-   [方法: ドキュメントからマネージ コード拡張機能を削除](../vsto/how-to-remove-managed-code-extensions-from-documents.md)します。  
  
-   [方法: アタッチ マネージ コードの拡張機能のドキュメントを](../vsto/how-to-attach-managed-code-extensions-to-documents.md)します。  
  
##  <a name="security"></a> セキュリティ タスク  
  
-   [方法: Office ソリューションに署名](../vsto/how-to-sign-office-solutions.md)します。  
  
##  <a name="deployment"></a> 展開タスク  
  
-   [方法: ClickOnce を使用して、Office ソリューションを発行する](http://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)します。  
  
-   [方法: ClickOnce を使用して、ドキュメント レベルの Office ソリューションを SharePoint サーバーに発行](http://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)します。  
  
-   [方法: ClickOnce Office ソリューション インストール](http://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)します。  
  
-   [方法: Office ソリューションを実行するためにエンド ユーザー コンピューターの前提条件をインストール](http://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)します。  
  
-   [方法: Office ソリューションの配置の IIS を準備する](http://msdn.microsoft.com/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4)します。  
  
-   [方法: 更新プログラムには、Office ソリューションが展開されている](http://msdn.microsoft.com/be96db53-b6ea-46ab-b8d9-b76b098b3b13)します。  
  
-   [方法: Office ソリューションのインストール パスを変更して](http://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)します。  
  
## <a name="see-also"></a>関連項目  
 [開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office アプリケーションおよびプロジェクトの種類で使用できる機能](../vsto/features-available-by-office-application-and-project-type.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)  
  
  