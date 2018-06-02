---
title: SharePoint ソリューションの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 82eaa5deca395af985017d0db0a98c11b2be9592
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691605"
---
# <a name="create-sharepoint-solutions"></a>SharePoint ソリューションを作成します。
  SharePoint Designer の代わりに Visual Studio で SharePoint アプリケーションを作成できます。 Visual Studio には、高度なデバッグ ツール、IntelliSense、ステートメント入力候補、プロジェクト テンプレートなど、迅速な SharePoint 開発を促進する機能が用意されています。 さらに、Visual Studio では、高度な .NET Framework ベースのツールと言語も活用されています。 SharePoint プロジェクトは Visual Basic または Visual C# を使用して開発できます。また、SharePoint 用アプリのプロジェクトは JavaScript を使用して開発できます。  
  
 SharePoint 2013 アドインと SharePoint アドインについては、「 [SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) 」および「 [SharePoint アプリの作成](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx)」を参照してください。  
  
> [!NOTE]  
>  新しい [SharePoint アドイン モデル](https://msdn.microsoft.com/library/office/fp179930.aspx) を使用してユーザーにとっての SharePoint の操作感を拡張する方法をご覧ください。 これらのアドインのフットプリントは、SharePoint ソリューションと比較して非常に小さく、その作成には、HTML5、JavaScript、CSS3、XML など、ほぼすべての Web プログラミング テクノロジを使用できます。  
  
|||  
|-|-|  
|![ドキュメント](../sharepoint/media/vs-icon-documentation.gif "ドキュメント")|**ドキュメント**<br /><br /> -   [作業の開始&#40;Visual Studio での SharePoint 開発&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)<br />-   [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)<br />-   [SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)<br />-   [ビルドと SharePoint ソリューションのデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)<br />-   [パッケージ化と SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)<br />-   [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)|  
|![ドキュメント](../sharepoint/media/vs-icon-documentation.gif "ドキュメント")|**おすすめのタスク**<br /><br /> -   [チュートリアル: サイト内の列、コンテンツ タイプ、および SharePoint のリストを作成します。](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)<br />-   [方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)<br />-   [方法: BDC モデルを作成](../sharepoint/how-to-create-a-bdc-model.md)<br />-   [方法: SharePoint Web パーツを作成します。](../sharepoint/how-to-create-a-sharepoint-web-part.md)<br />-   [方法: SharePoint アプリケーション ページのユーザー コントロールを作成または Web パーツ](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|  
|![チュートリアル](../sharepoint/media/vs-icon-walkthroughs.gif "チュートリアル")|**チュートリアル**<br /><br /> -   [SharePoint 開発のチュートリアル](../sharepoint/sharepoint-development-walkthroughs.md)|  
|![コード サンプル](../sharepoint/media/vs-icon-codesamples.gif "コード サンプル")|**コード サンプル**<br /><br /> -   [SharePoint 開発のサンプル](../sharepoint/sharepoint-development-samples.md)<br />-   [SharePoint 開発者向けダウンロード](http://msdn.microsoft.com/sharepoint/aa905690.aspx)|  
|![トレーニング](../sharepoint/media/vs-icon-training.gif "トレーニング")|**トレーニング**<br /><br /> -   [学習の SharePoint 開発](http://msdn.microsoft.com/sharepoint/aa905692.aspx)|  
|![フォーラム](../sharepoint/media/vs-icon-forums.gif "フォーラム")|**フォーラム**<br /><br /> -   [Visual Studio での SharePoint 開発](http://social.msdn.microsoft.com/Forums/vssharepointdevelopment/threads)<br />-   [SharePoint 2010](http://social.msdn.microsoft.com/Forums/category/sharepoint2010,sharepoint/)|  
|![トレーニング](../sharepoint/media/vs-icon-training.gif "トレーニング")|**ブログ**<br /><br /> -   [Visual Studio の SharePoint 開発のブログ](http://blogs.msdn.com/b/vssharepointtoolsblog/)|  
|![操作方法ビデオ](../sharepoint/media/vs-icon-howdoivideos.gif "どうすればいいですか?ビデオ")|**操作方法ビデオ**<br /><br /> -   [操作方法: 作成 SharePoint 2010 の視覚的 Web パーツを Visual Studio 2010 のですか。](http://msdn.microsoft.com/vstudio/ff623014.aspx)<br />-   [操作方法: Visual Studio 2010 で SharePoint 2010 のコンテンツ タイプを作成する](http://msdn.microsoft.com/vstudio/ff623016.aspx)<br />-   [操作方法: Visual Studio 2010 で SharePoint 2010 のサイト定義を作成する](http://msdn.microsoft.com/vstudio/ff623012.aspx)<br />-   [操作方法: Visual Studio 2010 を使用して SharePoint 2010 のビジネス データ接続モデルを作成する](http://msdn.microsoft.com/vstudio/ff623022.aspx)|  
|![Channel 9 ビデオ](../sharepoint/media/vs-icon-channel9videos.gif "Channel 9 ビデオ")|**Channel 9 ビデオ**<br /><br /> -   [Visual Studio 2010 での SharePoint 開発の概要](http://channel9.msdn.com/posts/funkyonex/Overview-of-SharePoint-Development-in-Visual-Studio-2010/)<br />-   [Visual Studio 2010 で SharePoint 2010 Web パーツを構築する際のベスト プラクティス](http://channel9.msdn.com/posts/funkyonex/Best-Practices-on-Building-SharePoint-2010-Web-Parts-with-Visual-Studio-2010/)<br />-   [Visual Studio 2010 の SharePoint フィーチャー デザイナーとパッケージ デザイナー](http://channel9.msdn.com/posts/funkyonex/SharePoint-Feature-and-Package-Designers-in-Visual-Studio-2010/)|  
|![MSDN デベロッパー センター](../sharepoint/media/vs-icon-msdndevcenter.gif "MSDN デベロッパー センター")|**MSDN デベロッパー センター**<br /><br /> -   [Visual Studio デベロッパー センター](http://msdn.microsoft.com/vstudio/default.aspx)<br />-   [SharePoint デベロッパー センター](http://msdn.microsoft.com/sharepoint/default.aspx)<br />-   [SharePoint Server デベロッパー センター](http://msdn.microsoft.com/office/aa905503.aspx)<br />-   [SharePoint Designer デベロッパー センター](http://msdn.microsoft.com/office/bb421303.aspx)<br />-   [ASP.NET デベロッパー センター](http://msdn.microsoft.com/aa336522.aspx)|  
|![フィードバックを提供する](../sharepoint/media/vs-icon-feedback.gif "フィードバックを提供します。")|**フィードバックを提供します。**<br /><br /> Visual Studio に関するフィードバックを送ることができます。<br /><br /> -   [Microsoft Connect します。](http://go.microsoft.com/fwlink/?LinkID=150463)<br /><br /> Visual Studio のドキュメントに関するフィードバックを送ることができます。<br /><br /> -   **簡易表示:** トピックの上部から、 **[このトピックを評価する]** リンクを選択してトピックの下部に移動します。そこで、 **[この情報は役にたちましたか。]** に対する応答として、 **[はい]** または **[いいえ]** を指定できます。 **[はい]** を選択した場合は、表示される 1 つ以上のチェック ボックスを選択し、テキスト ボックスに詳細情報を入力できます。 終了したら、 **[投稿]** ボタンをクリックします。<br />-   **スクリプトを使用しない表示:** トピックの上部で、 **[フィードバック]** リンクを選択し、MSDN、TechNet および式ライブラリ フィードバック フォーラムにフィードバックします。<br />-   **クラシック ビュー** トピックの上部で、 **[クリックして評価とフィードバックをお寄せください]** のアイコンを選択し、ドキュメント チームにそのトピックについてフィードバックしてください。|  
  
 