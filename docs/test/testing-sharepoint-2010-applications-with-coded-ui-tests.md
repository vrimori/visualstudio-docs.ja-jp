---
title: "コード化された UI テストを使用した SharePoint 2010 アプリケーションのテスト | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: "30"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 4cf5eac9600be44405142666e1f94408c44b0a13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>コード化された UI テストを使用した SharePoint 2010 アプリケーションのテスト
コード化された UI テストを SharePoint アプリケーションに含めると、UI コントロールを含むアプリケーション全体が正しく機能していることを検証できます。 コード化された UI テストでは、ユーザー インターフェイスの値とロジックも検証できます。  
  
 **必要条件**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>コード化された UI テストについて把握しておくべきこと  
 コード化された UI テストを使用する利点の詳細については、「[UI オートメーションを使用してコードをテストする](../test/use-ui-automation-to-test-your-code.md)」と「[Visual Studio 2012 を使用した継続的配信のためのテスト - 第 5 章: システム テストの自動化](http://go.microsoft.com/fwlink/?LinkID=255196)」を参照してください。  
  
 **ノート**  
  
-   ![必須コンポーネント](../test/media/prereq.png "必須コンポーネント") SharePoint アプリケーションのコード化された UI テストは、SharePoint 2010 でのみサポートされます。  
  
-   ![必須コンポーネント](../test/media/prereq.png "必須コンポーネント") SharePoint アプリケーションでは、Visio および PowerPoint 2010 コントロールはサポートされていません。  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>SharePoint アプリのコード化された UI テストを作成する  
 SharePoint 2010 アプリケーションでの[コード化された UI テストの作成](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) 方法は、他の種類のアプリケーションでのテストの作成方法と同じです。 記録と再生は、Web 編集インターフェイス上のすべてのコントロールでサポートされています。 カテゴリと Web パーツを選択するためのインターフェイスは、すべてが標準 Web コントロールです。  
  
 ![SharePoint Web パーツ](../test/media/cuit_sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  操作を記録している場合は、コードを生成する前に操作を検証します。 マウス ホバーにはいくつかの動作が関連付けられているため、既定で有効になっています。 コード化された UI テストから冗長なホバーを削除するようにしてください。 そのためには、テスト用のコードを編集するか、 [コード化された UI テスト エディター](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)を使用します。  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>SharePoint アプリ内に Office 2010 コントロールのテストを含める  
 SharePoint アプリでいくつかの Office 2010 Web パーツの自動化を有効にするには、コードを少し変更する必要があります。  
  
> [!WARNING]
>  Visio および PowerPoint 2010 コントロールはサポートされていません。  
  
### <a name="excel-2010-cell-controls"></a>Excel 2010 のセル コントロール  
 Excel セル コントロールを含めるには、コード化された UI テストのコードを少し変更する必要があります。  
  
> [!WARNING]
>  Excel のセルにテキストを入力してから方向キーを操作すると、正しく記録されません。 セルの選択にはマウスを使用してください。  
  
 空のセルに対する操作を記録している場合は、セルをダブルクリックしてからテキスト設定操作を実行して、コードを変更する必要があります。 そうする必要があるのは、セルをクリックした後、キーボードを操作すると、セル内の `textarea` がアクティブになるためです。 単に空のセルで `setvalue` を記録すると、セルがクリックされるまでは存在しない `editbox` が検索されます。 例:  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 空でないセルに対する操作を記録している場合は、セルにテキストを追加したときに新しい \<div> コントロールがセルの子として追加されるため、記録はより複雑になります。 新しい \<div> コントロールには、入力したテキストが含まれます。 レコーダーは新しい \<div> コントロールに対する操作を記録する必要がありますが、新しい \<div> コントロールはテキストが入力されるまで存在しないため、記録できません。 この問題に対応するために、手動で次のようにコードを変更する必要があります。  
  
1.  セルの初期化に移動して、 `RowIndex` および `ColumnIndex` プライマリ プロパティを作成します。  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  セルの `HtmlDiv` 子を検索します。  
  
    ```csharp  
    private UITestControl getControlToDoubleClick(HtmlCell cell)   
    {   
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;   
         HtmlDiv pane = new HtmlDiv(cell);   
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;   
         // Class is an important property in finding pane   
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";   
         UITestControlCollection panes = pane.FindMatchingControls();   
         return panes[0];   
    }  
  
    ```  
  
3.  `HtmlDiv`にマウスのダブルクリック操作のコードを追加します。  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  `TextArea`にテキストを設定するコードを追加します。  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>SharePoint 2010 アプリで Silverlight Web パーツのコード化された UI テストを有効にする  
 Visual Studio 2012 以降では、Silverlight のテストはサポートされていません。 しかし、SharePoint 2010 アプリで Silverlight Web パーツをテストしたい場合は、Visual Studio ギャラリーから個別の Silverlight プラグインをインストールすることができます。  
  
#### <a name="setting-up-your-machine"></a>コンピューターを設定する  
  
1.  Visual Studio 2012.1 以降がインストールされていることを確認します。  
  
2.  [Microsoft Visual Studio UI Test Plugin for Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4)をインストールします。  
  
3.  [Fiddler](http://www.fiddler2.com/fiddler2/)をインストールします。 これは、HTTP トラフィックをキャプチャしてログ記録するだけのツールです。  
  
4.  [fiddlerXap プロジェクト](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip)をダウンロードします。 解凍、ビルド後、"CopySLHelper.bat" スクリプトを実行して、Fiddler ツールで Silverlight Web パーツをテストするときに必要なヘルパー DLL をインストールします。  
  
 コンピューターのセットアップ後、Silverlight Web パーツを使用する SharePoint 2010 アプリのテストを開始するために、次の手順に従います。  
  
#### <a name="testing-silverlight-web-parts"></a>Silverlight Web パーツをテストする  
  
1.  Fiddler を起動します。  
  
2.  ブラウザーのキャッシュを消去します。 この操作が必要なのは、Silverlight UI オートメーション ヘルパー DLL が含まれている XAP ファイルが、通常はキャッシュされるためです。 変更した XAP ファイルが確実に格納されるようにするために、ブラウザーのキャッシュを消去します。  
  
3.  Web ページを開きます。  
  
4.  通常の Web アプリケーション テストと同様に、レコーダーを開始し、コードを生成します。  
  
5.  生成されたコードが、Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll を参照することを確認する必要があります。  
  
     詳細については、「 [Visual Studio 2012 での SharePoint 2010 の UI テスト](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)」をご覧ください。  
  
## <a name="external-resources"></a>外部リソース  
  
### <a name="blogs"></a>ブログ  
 [Visual Studio 2012 での SharePoint 2010 の UI テスト](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [コード化された UI テストでの Silverlight コントロールの検索ロジックを理解する](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Silverlight コントロールのプロパティの取得](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [コード化された UI テストのコンテンツ インデックス](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>ガイダンス  
 [Visual Studio 2012 を使用した継続的配信のためのテスト - 第 5 章: システム テストの自動化](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>フォーラム  
 [Visual Studio ALM + Team Foundation Server のブログ](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>参照  
 [UI オートメーションを使用してコードをテストする](../test/use-ui-automation-to-test-your-code.md)   
 [SharePoint 2010 および 2013 アプリケーションの Web パフォーマンス テストおよびロード テスト](/devops-test-docs/test/web-performance-and-load-testing-sharepoint-2010-and-2013-applications)   
 [SharePoint ソリューションの作成](/office-dev/office-dev/create-sharepoint-solutions)   
 [SharePoint コードの検証およびデバッグ](/office-dev/office-dev/verifying-and-debugging-sharepoint-code)   
 [SharePoint ソリューションのビルドとデバッグ](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)   
 [SharePoint アプリケーションのパフォーマンスのプロファイリング](/office-dev/office-dev/profiling-the-performance-of-sharepoint-applications)
