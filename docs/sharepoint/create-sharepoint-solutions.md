---
title: "SharePoint ソリューションの作成"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発"
ms.assetid: 4bfb1e59-97c9-4594-93f8-3068b4eb9631
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# SharePoint ソリューションの作成
  SharePoint Designer の代わりに Visual Studio で SharePoint アプリケーションを作成できます。 Visual Studio には、高度なデバッグ ツール、IntelliSense、ステートメント入力候補、プロジェクト テンプレートなど、迅速な SharePoint 開発を促進する機能が用意されています。 さらに、Visual Studio では、高度な .NET Framework ベースのツールと言語も活用されています。 SharePoint プロジェクトは Visual Basic または Visual C\# を使用して開発できます。また、SharePoint 用アプリのプロジェクトは JavaScript を使用して開発できます。  
  
 SharePoint 2013 アドインと SharePoint アドインについては、「[SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx)」および「[SharePoint アプリの作成](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx)」を参照してください。  
  
> [!NOTE]  
>  新しい [SharePoint アドイン モデル](https://msdn.microsoft.com/library/office/fp179930.aspx)を使用してユーザーにとっての SharePoint の操作感を拡張する方法をご覧ください。 これらのアドインのフットプリントは、SharePoint ソリューションと比較して非常に小さく、その作成には、HTML5、JavaScript、CSS3、XML など、ほぼすべての Web プログラミング テクノロジを使用できます。  
  
|||  
|-|-|  
|![ドキュメント](../sharepoint/media/vs-icon-documentation.png "ドキュメント")|**Documentation**<br /><br /> -   [Getting Started &#40;SharePoint Development in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)<br />-   [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)<br />-   [SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)<br />-   [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)<br />-   [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)<br />-   [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)|  
|![ドキュメント](../sharepoint/media/vs-icon-documentation.png "ドキュメント")|**Featured Tasks**<br /><br /> -   [チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)<br />-   [方法: イベント レシーバーを作成する](../sharepoint/how-to-create-an-event-receiver.md)<br />-   [方法: BDC モデルを作成する](../sharepoint/how-to-create-a-bdc-model.md)<br />-   [方法: SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part.md)<br />-   [方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|  
|![チュートリアル](../sharepoint/media/vs-icon-walkthroughs.png "チュートリアル")|**Walkthroughs**<br /><br /> -   [SharePoint 開発のチュートリアル](../sharepoint/sharepoint-development-walkthroughs.md)|  
|![コード サンプル](../sharepoint/media/vs-icon-codesamples.png "コード サンプル")|**Code Samples**<br /><br /> -   [SharePoint 開発のサンプル](../sharepoint/sharepoint-development-samples.md)<br />-   [SharePoint 開発者向けダウンロード](http://msdn.microsoft.com/sharepoint/aa905690.aspx)|  
|![トレーニング](../sharepoint/media/vs-icon-training.png "トレーニング")|**Training**<br /><br /> -   [SharePoint の開発者向けトレーニング](http://msdn.microsoft.com/sharepoint/aa905692.aspx)|  
|![フォーラム](../sharepoint/media/vs-icon-forums.png "フォーラム")|**Forums**<br /><br /> -   [Visual Studio を使用した SharePoint 開発](http://social.msdn.microsoft.com/Forums/vssharepointdevelopment/threads)<br />-   [SharePoint 2010](http://social.msdn.microsoft.com/Forums/category/sharepoint2010,sharepoint/)|  
|![トレーニング](../sharepoint/media/vs-icon-training.png "トレーニング")|**Blogs**<br /><br /> -   [Visual Studio SharePoint 開発チームのブログ](http://blogs.msdn.com/b/vssharepointtoolsblog/)|  
|![操作方法 ビデオ](../sharepoint/media/vs-icon-howdoivideos.png "操作方法 ビデオ")|**How Do I? Videos**<br /><br /> -   [操作方法: Visual Studio 2010 で SharePoint 2010 の視覚的 Web パーツを作成する](http://msdn.microsoft.com/vstudio/ff623014.aspx)<br />-   [操作方法: Visual Studio 2010 で SharePoint 2010 のコンテンツ タイプを作成する](http://msdn.microsoft.com/vstudio/ff623016.aspx)<br />-   [操作方法: Visual Studio 2010 で SharePoint 2010 のサイト定義を作成する](http://msdn.microsoft.com/vstudio/ff623012.aspx)<br />-   [操作方法: Visual Studio 2010 を使用して SharePoint 2010 のビジネス データ接続モデルを作成する](http://msdn.microsoft.com/vstudio/ff623022.aspx)|  
|![Channel 9 ビデオ](../sharepoint/media/vs-icon-channel9videos.png "Channel 9 ビデオ")|**Channel 9 Videos**<br /><br /> -   [Visual Studio 2010 での SharePoint 開発の概要](http://channel9.msdn.com/posts/funkyonex/Overview-of-SharePoint-Development-in-Visual-Studio-2010/)<br />-   [Visual Studio 2010 で SharePoint 2010 Web パーツを構築する際のベスト プラクティス](http://channel9.msdn.com/posts/funkyonex/Best-Practices-on-Building-SharePoint-2010-Web-Parts-with-Visual-Studio-2010/)<br />-   [Visual Studio 2010 の SharePoint フィーチャー デザイナーとパッケージ デザイナー](http://channel9.msdn.com/posts/funkyonex/SharePoint-Feature-and-Package-Designers-in-Visual-Studio-2010/)|  
|![MSDN デベロッパー センター](../sharepoint/media/vs-icon-msdndevcenter.png "MSDN デベロッパー センター")|**MSDN Developer Centers**<br /><br /> -   [Visual Studio 開発者向け技術情報](http://msdn.microsoft.com/vstudio/default.aspx)<br />-   [SharePoint デベロッパー センター](http://msdn.microsoft.com/sharepoint/default.aspx)<br />-   [SharePoint Server デベロッパー センター](http://msdn.microsoft.com/office/aa905503.aspx)<br />-   [SharePoint Designer デベロッパー センター](http://msdn.microsoft.com/office/bb421303.aspx)<br />-   [ASP.NET デベロッパー センター](http://msdn.microsoft.com/aa336522.aspx)|  
|![フィードバックの送信](../sharepoint/media/vs-icon-feedback.png "フィードバックの送信")|**Providing Feedback**<br /><br /> Visual Studio に関するフィードバックを送ることができます。<br /><br /> -   [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=150463)<br /><br /> Visual Studio のドキュメントに関するフィードバックを送ることができます。<br /><br /> -   **簡易表示:**トピックの上部から、**\[このトピックを評価する\]** リンクを選択してトピックの下部に移動します。そこで、**\[この情報は役にたちましたか。\]** に対する応答として、**\[はい\]** または **\[いいえ\]** を指定できます。**\[いいえ\]** を選択した場合は、表示される 1 つ以上のチェック ボックスを選択し、テキスト ボックスに詳細情報を入力できます。 終了したら、**\[投稿\]** ボタンをクリックします。<br />-   **スクリプトを使用しない表示:**トピックの上部で、**\[フィードバック\]** リンクを選択し、MSDN、TechNet および式ライブラリ フィードバック フォーラムにフィードバックします。<br />-   **クラシック ビュー**トピックの上部にある **\[クリックして評価とフィードバックをお寄せください\]** のアイコンを選択し、ドキュメント チームにそのトピックについてフィードバックしてください。|  
  
  