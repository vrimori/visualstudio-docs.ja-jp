---
title: "SharePoint の Web パーツの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.SharePoint.WebControls.DateTimeControl"
  - "Microsoft.SharePoint.WebControls.CssLink"
  - "Microsoft.SharePoint.WebControls.RssLink"
  - "Microsoft.SharePoint.WebControls.Theme"
  - "Microsoft.SharePoint.WebControls.AspMenu"
  - "Microsoft.SharePoint.WebControls.ListProperty"
  - "Microsoft.SharePoint.WebControls.ProjectProperty"
  - "Microsoft.SharePoint.WebControls.FormsDigest"
  - "Microsoft.SharePoint.WebControls.ScriptLink"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, Web パーツ"
  - "Web パーツ [Visual Studio での SharePoint 開発], デザイン"
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# SharePoint の Web パーツの作成
  Web パーツを作成すると、SharePoint サイト ページのコンテンツ、外観、および動作をユーザーがブラウザーから変更できます。  Web パーツは、Web パーツ ページ内で実行されるサーバー側コントロールです。SharePoint サイトに表示されるページはこれらの Web パーツで構成されます。  「[構成要素: Web パーツ](http://go.microsoft.com/fwlink/?LinkID=182097)」を参照してください。  
  
 SharePoint サイトの Web パーツを作成およびデバッグするには、Visual Studio のテンプレートを使用します。  
  
## Visual Studio で Web パーツを作成する  
 Web パーツを作成するには、SharePoint プロジェクトに **Web パーツ**項目を追加します。  サンドボックス ソリューションまたはファーム ソリューションに **Web パーツ**項目を使用できます。  
  
 デザイナーを使用して Web パーツを視覚的にデザインする場合は、**視覚的 Web パーツ** プロジェクトを作成するか、**視覚的 Web パーツ**項目を SharePoint プロジェクトに追加します。  **視覚的 Web パーツ**項目を使用できるのは、ファーム ソリューションのみです。  
  
### Web パーツ項目  
 **Web パーツ**項目には、SharePoint サイト用の Web パーツをデザインするためのファイルが用意されています。  **Web パーツ**項目を追加すると、プロジェクトにフォルダーが作成され、そのフォルダーにいくつかのファイルが追加されます。  各ファイルの説明を次の表に示します。  
  
|File|説明|  
|----------|--------|  
|Elements.xml|Web パーツを配置する際、プロジェクトのフィーチャー定義ファイルで使用する情報が格納されます。|  
|.webpart ファイル|SharePoint の Web パーツ ギャラリーに Web パーツを表示するために必要な情報を指定します。|  
|コード ファイル|Web パーツにコントロールを追加するメソッド、および Web パーツ内にカスタム コンテンツを生成するメソッドが保存されます。|  
  
 詳細については、「[方法: SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part.md)」を参照してください。  
  
### 視覚的 Web パーツ項目  
 視覚的 Web パーツは、Visual Studio の Visual Web Developer デザイナーを使用して作成する Web パーツです。  「[Visual Studio Web Development Content Map](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)」を参照してください。  
  
 視覚的 Web パーツの機能は他の Web パーツと同じです。  ボタンやテキスト ボックスなどのコントロールを Web パーツに追加するときは、XML ファイルにコードを追加します。  ただし、視覚的 Web パーツにコントロールを追加するときは、Visual Studio の**ツールボックス**から Web パーツへコントロールをドラッグまたはコピーします。  その後、XML ファイルで必要なコードを生成します。  「[方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)」を参照してください。  
  
## SharePoint コントロール  
 Visual Studio には、アプリケーションのページなど、SharePoint ページを作成するためのコントロールが用意されています。  これらのコントロールは、**ツールボックス**の **\[SharePoint コントロール\]** の下に表示されます。  これらのコントロールの機能は、[Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) 名前空間から取得されます。この名前空間には、SharePoint のサイト ページやリスト ページで使用する ASP.NET サーバー コントロールが含まれています。  
  
|コントロール名|説明|  
|-------------|--------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|ASP メニューを挿入します。  詳細については、「[メニュー コントロールの概要](http://go.microsoft.com/fwlink/?LinkId=235316)」を参照してください。|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|**LINK** 要素を .aspx ページに挿入し、**CssRegistration** で定義されている外部スタイル シートを適用します。|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|.aspx ページに DateTime コントロールを挿入します。|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|.aspx ページにセキュリティ検証を挿入します。|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|指定されたリストのプロパティを返します。|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|現在の Web サイトのグローバル プロパティを返します。|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|RSS フィードへのリンクを .aspx ページに挿入します。|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|スクリプトなどのリソースをページに登録し、ページのレンダリング時に要求できるようにするためのプロパティとメソッドを提供します。|  
|[Theme](http://go.microsoft.com/fwlink/?LinkId=235314)|.aspx ページにテーマを適用します。|  
  
## Web パーツをデバッグする  
 他の Visual Studio プロジェクトをデバッグする場合と同様に、Web パーツを含む SharePoint プロジェクトをデバッグできます。  Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 コードのデバッグを開始するには、SharePoint で Web パーツ ページに Web パーツを追加します。  
  
 SharePoint プロジェクトのデバッグ方法の詳細については、「[SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)」を参照してください。  
  
## 視覚的 Web パーツの制限  
 Visual Studio では、SharePoint のサンドボックス ソリューションおよびファーム ソリューションに視覚的 Web パーツを追加できます。  ただし、視覚的 Web パーツには次のような制限があります。  
  
-   視覚的 Web パーツでは置き換え可能パラメーターを使用できません。  詳細については、「[置き換え可能パラメーター](../sharepoint/replaceable-parameters.md)」を参照してください。  
  
-   ユーザー コントロールと視覚的 Web パーツは、視覚的 Web パーツ上にドラッグ アンド ドロップしたり、コピーしたりできません。  これらの操作を実行するとビルド エラーが発生します。  
  
-   視覚的 Web パーツは、$SPUrl などの SharePoint サーバー トークンを直接サポートしません。  詳細については、「[SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)」トピックの「Token Restrictions in Sandboxed Visual Web Parts \(サンドボックス視覚的 Web パーツでのトークンの制約\)」を参照してください。  
  
-   サンドボックス ソリューションの視覚的 Web パーツは、"Sandboxed Code Host Service がビジー状態で要求を処理できなかったので、セキュリティで保護されたコード実行要求が拒否されました" というエラーが発生する場合があります。このエラーの詳細については、[SharePoint 開発者チーム ブログの投稿](http://go.microsoft.com/fwlink/?LinkId=225932)を参照してください。  
  
-   Visual Studio では、サーバー側 JavaScript のデバッグがサポートされていません。ただし、クライアント側 JavaScript のデバッグはサポートされています。  
  
     サーバー側のマークアップ ファイルにインライン JavaScript を追加できますが、マークアップに追加したブレークポイントはデバッグできません。  JavaScript をデバッグするには、マークアップ ファイルで外部の JavaScript ファイルを参照し、JavaScript ファイルにブレークポイントを設定します。  
  
-   インライン [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] コードのデバッグは、マークアップ ファイルではなく、生成されたコード ファイルで実行する必要があります。  
  
-   視覚的 Web パーツでは、`<@ Assembly Src=` ディレクティブを使用できません。  
  
-   SharePoint の Web コントロールと一部の [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] コントロールは、SharePoint サンドボックス環境でサポートされていません。  サンドボックス ソリューションの視覚的 web パーツでサポート対象外のコントロールを使用すると、"型または名前空間の名前 'Theme' は名前空間 'Microsoft.SharePoint.WebControls' に存在しません" というエラーが表示されます。  
  
 サンドボックス ソリューションの詳細については、「[サンドボックス ソリューションとファーム ソリューションの違い](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)」を参照してください。  
  
## 古い形式の SharePoint に基づく Web パーツを作成する  
 Visual Studio のテンプレートを使用すると、SharePoint 用の独自の [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web パーツを作成できます。  [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web パーツは [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Web パーツのインフラストラクチャ上にビルドされるので、新しいプロジェクトに適しています。  
  
 ごくまれに、古い形式の SharePoint に対応する Web パーツを使用して Web パーツを作成しなければならない場合があります。  こうした Web パーツも Visual Studio で作成できますが、Visual Studio にはその際に役立つテンプレートがありません。  
  
 古い形式の SharePoint に対応する Web パーツを作成するケースについては、「[SharePoint Foundation の Web パーツ インフラストラクチャ](http://go.microsoft.com/fwlink/?LinkId=169290)」を参照してください。  古い形式の SharePoint に基づく Web パーツを使用して Web パーツを作成する方法については、「[チュートリアル: 基本的な SharePoint Web パーツの作成](http://go.microsoft.com/fwlink/?LinkId=169288)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[方法: SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part.md)|SharePoint ページの Web パーツを作成する方法について説明します。|  
|[方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|視覚的なデザイン サーフェイスを使用して、SharePoint の Web パーツを作成する方法について説明します。|  
|[方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint で実行されるアプリケーション ページと Web パーツで使用できる、再利用可能なカスタム コントロールを作成する方法について説明します。|  
|[チュートリアル: SharePoint の Web パーツを作成する](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|SharePoint の Web パーツをデザインする方法について説明します。|  
|[チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|視覚的なデザイン サーフェイスにコントロールをドラッグして、SharePoint の Web パーツをデザインする方法について説明します。|  
|[チュートリアル: SharePoint の OData を表示する Silverlight Web パーツの作成](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Silverlight アプリケーションをホストし、SharePoint リストのデータを表示する、SharePoint の Web パーツをデザインする方法について説明します。|  
|[Visual Web Developer の操作](http://msdn.microsoft.com/ja-jp/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|プロジェクトで Web ページを開くと表示されるデザイナーの使用方法について説明します。|  
  
  