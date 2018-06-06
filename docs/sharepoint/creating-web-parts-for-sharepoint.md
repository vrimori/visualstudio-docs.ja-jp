---
title: SharePoint の Web パーツの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2a9cb18d1b9de7f4f67f8c3d153a9dfa4598612d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765727"
---
# <a name="create-web-parts-for-sharepoint"></a>For SharePoint web パーツを作成します。
  Web パーツを作成すると、SharePoint サイト ページのコンテンツ、外観、および動作をユーザーがブラウザーから変更できます。 Web パーツは、Web パーツ ページ内で実行されるサーバー側コントロールです。SharePoint サイトに表示されるページはこれらの Web パーツで構成されます。 参照してください[ビルディング ブロック: Web パーツ](http://go.microsoft.com/fwlink/?LinkID=182097)です。  
  
 SharePoint サイトの Web パーツを作成およびデバッグするには、Visual Studio のテンプレートを使用します。  
  
## <a name="create-a-web-part-in-visual-studio"></a>Visual Studio での web パーツを作成します。
 追加することで、web パーツを作成、 **Web パーツ**を SharePoint プロジェクト項目です。 使用することができます、 **Web パーツ**サンド ボックス ソリューションまたはファーム ソリューション内のアイテムです。  
  
 デザイナーを使用して web パーツを視覚的にデザインを作成する場合、**視覚的 Web パーツ**プロジェクトまたは追加**視覚的 Web パーツ**を SharePoint プロジェクト項目です。 使用することができます、**視覚的 Web パーツ**ファーム ソリューションのみ内の項目。  
  
### <a name="web-part-item"></a>Web パーツ項目
 A **Web パーツ**項目には、SharePoint サイトの web パーツをデザインに使用できるファイルが用意されています。 追加すると、 **Web パーツ**項目、Visual Studio は、プロジェクトのフォルダーが作成され、フォルダーにいくつかのファイルを追加します。 各ファイルの説明を次の表に示します。  
  
|ファイル|説明|  
|----------|-----------------|  
|*Elements.xml*|Web パーツを配置する際、プロジェクトのフィーチャー定義ファイルで使用する情報が格納されます。|  
|.webpart ファイル|SharePoint の Web パーツ ギャラリーに Web パーツを表示するために必要な情報を指定します。|  
|コード ファイル|Web パーツにコントロールを追加するメソッド、および Web パーツ内にカスタム コンテンツを生成するメソッドが保存されます。|  
  
 詳細については、次を参照してください。[する方法: SharePoint Web パーツを作成](../sharepoint/how-to-create-a-sharepoint-web-part.md)です。  
  
### <a name="visual-web-part-item"></a>視覚的 web パーツ項目
 視覚的 Web パーツは、Visual Studio の Visual Web Developer デザイナーを使用して作成する Web パーツです。 視覚的 Web パーツの機能は他の Web パーツと同じです。 ボタンやテキスト ボックスなどのコントロールを Web パーツに追加するときは、XML ファイルにコードを追加します。 ただし、コントロールを追加する視覚的 web パーツをドラッグするか、Visual Studio から web パーツ上にコピーする**ツールボックス**です。 その後、XML ファイルで必要なコードを生成します。 参照してください[する方法: デザイナーを使用して SharePoint Web パーツを作成](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)です。  
  
## <a name="sharepoint-controls"></a>SharePoint コントロール
 Visual Studio には、アプリケーションのページなど、SharePoint ページを作成するためのコントロールが用意されています。 これらのコントロールに表示されます、**ツールボックス** **SharePoint コントロール**です。 派生して、これらのコントロールの機能、[な処理](http://go.microsoft.com/fwlink/?LinkId=235315)名前空間は、SharePoint サイトおよびリストのページで使用されている ASP.NET サーバー コントロールが含まれています。  
  
|コントロール名|説明|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|ASP メニューを挿入します。 詳細については、次を参照してください。[メニュー コントロールの概要](http://go.microsoft.com/fwlink/?LinkId=235316)です。|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|挿入、**リンク**に要素を *.aspx*ページし、によって定義された 1 つまたは複数の外部スタイル シートを適用**CssRegistration**です。|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|DateTime コントロールを挿入、 *.aspx*ページ。|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|セキュリティ検証を挿入、 *.aspx*ページ|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|指定されたリストのプロパティを返します。|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|現在の Web サイトのグローバル プロパティを返します。|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|RSS フィードにへのリンクを挿入、 *.aspx*ページ。|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|スクリプトなどのリソースをページに登録し、ページのレンダリング時に要求できるようにするためのプロパティとメソッドを提供します。|  
|[テーマ](http://go.microsoft.com/fwlink/?LinkId=235314)|テーマを適用、 *.aspx*ページ。|  
  
## <a name="debug-a-web-part"></a>Web パーツをデバッグします。
 他の Visual Studio プロジェクトをデバッグする場合と同様に、Web パーツを含む SharePoint プロジェクトをデバッグできます。 Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 コードのデバッグを開始するには、SharePoint で Web パーツ ページに Web パーツを追加します。  
  
 SharePoint プロジェクトをデバッグする方法の詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)です。  
  
## <a name="visual-web-part-limitations"></a>視覚的 web パーツの制限
 Visual Studio では、SharePoint のサンドボックス ソリューションおよびファーム ソリューションに視覚的 Web パーツを追加できます。 ただし、視覚的 Web パーツには次のような制限があります。  
  
-   視覚的 Web パーツでは置き換え可能パラメーターを使用できません。 詳細については、次を参照してください。[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)です。  
  
-   ユーザー コントロールと視覚的 Web パーツは、視覚的 Web パーツ上にドラッグ アンド ドロップしたり、コピーしたりできません。 これらの操作を実行するとビルド エラーが発生します。  
  
-   視覚的 Web パーツは、$SPUrl などの SharePoint サーバー トークンを直接サポートしません。 詳細についてを参照してください"トークン制限のサンド ボックス視覚的 Web パーツ"トピック[SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)です。  
  
-   サンドボックス ソリューションの視覚的 Web パーツは、"Sandboxed Code Host Service がビジー状態で要求を処理できなかったので、セキュリティで保護されたコード実行要求が拒否されました" というエラーが発生する場合があります。 このエラーの詳細についてでこの投稿を参照してください、 [SharePoint 開発者チーム ブログ](http://go.microsoft.com/fwlink/?LinkId=225932)です。  
  
-   Visual Studio では、サーバー側 JavaScript のデバッグがサポートされていません。ただし、クライアント側 JavaScript のデバッグはサポートされています。  
  
     サーバー側のマークアップ ファイルにインライン JavaScript を追加できますが、マークアップに追加したブレークポイントはデバッグできません。 JavaScript をデバッグするには、マークアップ ファイルで外部の JavaScript ファイルを参照し、JavaScript ファイルにブレークポイントを設定します。  
  
-   インライン [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] コードのデバッグは、マークアップ ファイルではなく、生成されたコード ファイルで実行する必要があります。  
  
-   視覚的 Web パーツでは、`<@ Assembly Src=` ディレクティブを使用できません。  
  
-   SharePoint の Web コントロールと一部の [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] コントロールは、SharePoint サンドボックス環境でサポートされていません。 サンドボックス ソリューションの視覚的 web パーツでサポート対象外のコントロールを使用すると、"型または名前空間の名前 'Theme' は名前空間 'Microsoft.SharePoint.WebControls' に存在しません" というエラーが表示されます。  
  
 サンド ボックス ソリューションの詳細については、次を参照してください。[違いサンド ボックス ソリューションとファーム ソリューション](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)です。  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>古いスタイルの SharePoint ベースの web パーツを作成します。
 Visual Studio のテンプレートを使用すると、SharePoint 用の独自の [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web パーツを作成できます。 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web パーツは [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Web パーツのインフラストラクチャ上にビルドされるので、新しいプロジェクトに適しています。  
  
 ごくまれに、古い形式の SharePoint に対応する Web パーツを使用して Web パーツを作成しなければならない場合があります。 こうした Web パーツも Visual Studio で作成できますが、Visual Studio にはその際に役立つテンプレートがありません。  
  
 詳細については、古いスタイル SharePoint ベースの web パーツを作成する場合、次を参照してください。 [Windows SharePoint Services での Web パーツのインフラストラクチャ](http://go.microsoft.com/fwlink/?LinkId=169290)です。 古いスタイル SharePoint ベースの web パーツを使用して、web パーツを作成する方法の詳細については、次を参照してください。[基本的な SharePoint Web パーツを作成するチュートリアル](http://go.microsoft.com/fwlink/?LinkId=169288)です。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part.md)|SharePoint ページの Web パーツを作成する方法について説明します。|  
|[方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|視覚的なデザイン サーフェイスを使用して、SharePoint の Web パーツを作成する方法について説明します。|  
|[方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint で実行されるアプリケーション ページと Web パーツで使用できる、再利用可能なカスタム コントロールを作成する方法について説明します。|  
|[チュートリアル: SharePoint の Web パーツを作成する](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|SharePoint の Web パーツをデザインする方法について説明します。|  
|[チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|視覚的なデザイン サーフェイスにコントロールをドラッグして、SharePoint の Web パーツをデザインする方法について説明します。|  
|[チュートリアル: SharePoint の OData を表示する Silverlight Web パーツの作成](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Silverlight アプリケーションをホストし、SharePoint リストのデータを表示する、SharePoint の Web パーツをデザインする方法について説明します。|  
  
