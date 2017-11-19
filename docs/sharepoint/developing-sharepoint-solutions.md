---
title: "SharePoint ソリューションの開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, overview
ms.assetid: 059bce0f-c301-4234-a0b4-9c14b7cdfa3e
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 836568ff9c8b18c944ed2fe9e1e407c2176b48c1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="developing-sharepoint-solutions"></a>SharePoint ソリューションの開発
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には、SharePoint サイトおよびサイト要素を作成するための SharePoint プロジェクトの種類のテンプレートがいくつか用意されています。 使用可能なプロジェクトの種類の一覧は、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)です。 次に、SharePoint プロジェクトの要素およびプロパティについて説明します。  
  
 SharePoint 2013 アドインと SharePoint アドインについては、「 [SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) 」および「 [SharePoint アドインの作成](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx)」を参照してください。  
  
## <a name="elements-of-a-sharepoint-project"></a>SharePoint プロジェクトの要素  
 SharePoint プロジェクトのノードは、 *SharePoint アイテム*と呼ばれます。 SharePoint の項目と呼ばれる 1 つまたは複数のサブが含まれることも*SharePoint アイテム ファイル*など[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]構成ファイル、.aspx フォームなどです。  
  
 プロジェクト項目ファイルから成るプロジェクト テンプレートを使用してプロジェクトを作成する代わりに、 **[空のプロジェクト]** テンプレートを使用して、空の SharePoint プロジェクトを作成し、それにプロジェクト項目を手動で追加することもできます。 SharePoint プロジェクトには、必要に応じて 1 つ以上のフィーチャー ファイル (SharePoint でのアクティブ化に使用) およびパッケージ ファイル (プロジェクトの配布に使用) を含めることができます。  
  
### <a name="special-nodes"></a>特殊なノード  
 すべての SharePoint プロジェクトに、名前変更、削除、切り取り、コピー、プロジェクトからのドラッグなどの操作ができないノードが 2 つ含まれています。 これらのノードを次に示します。  
  
-   機能  
  
-   パッケージ  
  
 プロジェクトにフィーチャーまたはパッケージが定義されているかどうかに関係なく、この 2 つのノードはすべての SharePoint プロジェクトに必ず表示されます。  
  
#### <a name="features-node"></a>[Features] ノード  
 **[Features]** ノードには、SharePoint プロジェクトのフィーチャーが 1 つ以上含まれています。 フィーチャーとは、SharePoint の拡張機能のコンテナーのことです。 SharePoint サーバーにフィーチャーを配置すると、SharePoint サイトの SharePoint 管理者が、そのフィーチャーをサイト定義に追加したり、個別にアクティブ化したりすることができます。 詳細については、「 [フィーチャーの使用](http://go.microsoft.com/fwlink/?LinkID=147704)」を参照してください。  
  
 コンテンツ タイプやリスト インスタンスなどのアイテムを SharePoint プロジェクトに追加すると、 **[Features]** ノード内のフィーチャーに追加されます。 新しいフィーチャーに追加されるか、既存のフィーチャーに追加されるかは、そのアイテムのスコープによって決まります。 新しい項目が既存のフィーチャーと同じスコープを持つ場合は、そのフィーチャーに追加されます。 それ以外の場合は、新しいフィーチャーに追加されます。  
  
 フィーチャーを手動で追加するには、そのフィーチャー ノードのショートカット メニューから **[フィーチャーの追加]** コマンドを実行します。 フィーチャーの内容は、フィーチャー デザイナーを使用して表示または変更することができます。 詳細については、次を参照してください。[する方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)です。  
  
 SharePoint プロジェクトに追加したフィーチャーは、 **ソリューション エクスプローラー** にノードとして表示され、"Feature*x*.feature" という既定の名前が付けられます ( *x* は一意の番号)。 SharePoint Server にフィーチャーが配置されると、SharePoint 管理者は SharePoint サイト ユーザーが使用できるようにそれをアクティブ化することができます。  
  
#### <a name="package-node"></a>[Package] ノード  
 **[Package]** ノードには、SharePoint プロジェクトの配布メカニズムとして機能するファイルが 1 つだけ含まれています。 これは *ソリューション**package*と呼ばれ、.WSP という拡張子を持つ .CAB ベースのファイルです。 ソリューション パッケージは、SharePoint サイトに適用される一連のフィーチャー、サイト定義、およびアセンブリを含んでいる配置可能で再利用可能なファイルであり、これは個別に有効または無効にできます。 **パッケージ**ノードがである Package.wspdef というファイルにはも必ず含まれています、[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]パッケージ定義ファイルです。 SharePoint を実行しているサーバーにパッケージが配置されると、SharePoint 管理者はそのパッケージをインストールしてフィーチャーをアクティブにできます。  
  
 表示したりを [パッケージ] ノードをダブルクリックするか、ショートカット メニューを開き、選択し、パッケージ デザイナーでパッケージの内容を変更する**開く**です。 詳細については、次を参照してください。 [SharePoint ソリューション パッケージの作成](../sharepoint/creating-sharepoint-solution-packages.md)です。  
  
## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint プロジェクトとプロジェクト項目のプロパティ  
 SharePoint プロジェクトでは、他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトと同様、[プロパティ] ウィンドウおよび [プロパティ] ページにプロパティが表示されます。 表示されるプロパティは、選択したノードによって異なります。  
  
 **ソリューション エクスプローラー**で SharePoint プロジェクト ノード、プロジェクト項目ノード、またはプロジェクト項目ファイル ノードを選択すると、次のプロパティが [プロパティ] ウィンドウまたは [プロパティ] ページに表示されます。  
  
### <a name="project-properties"></a>プロジェクトのプロパティ  
  
|プロパティ名|説明|  
|-------------------|-----------------|  
|アクティブな配置構成|配置中に実行される一連の手順を指定します。 詳細については、次を参照してください。[する方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)です。|  
|アセンブリの配置先|*SharePoint アプリケーション アセンブリ* の場所を決定します。 アセンブリの場所として有効な値は、 *GlobalAssemblyCache* (既定値) または *WebApplication*です。<br /><br /> *Sandboxed Solution* プロパティが **true**に設定されている場合、このプロパティは無効です。|  
|デバッグ後に自動取り消し|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のデバッグ モードでアプリケーションを実行した後、配置されたソリューションを SharePoint から自動的に取り消すかどうかを指定します。 オンにすると、デバッグ後に IDE がデザイン ビューに戻ると、ソリューションは取り消されます。 オフにすると、ソリューションは取り消されません。 詳細については、「 [ソリューションを取り消す](http://go.microsoft.com/fwlink/?LinkId=183819)」を参照してください。|  
|構成の編集|プロジェクトに使用する配置の構成を指定します。 詳細については、次を参照してください。[する方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)と[を展開する、発行、および SharePoint ソリューション パッケージのアップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)です。|  
|Script デバッグの代わりに Silverlight デバッグを有効にする|オンにすると、Silverlight デバッガーがデバッグ プロセスにアタッチされます。 オフにすると、スクリプト デバッガーがデバッグ プロセスにアタッチされます。 詳細については、「 [Silverlight デバッグの概要](http://go.microsoft.com/fwlink/?LinkId=179826)」を参照してください。|  
|パッケージにアセンブリを含める|プロジェクト アセンブリをビルド時にパッケージ化するかどうかを指定します。|  
|配置後コマンド ライン|SharePoint ソリューションを配置した後で実行するコマンドを指定します。 この行では、MSBuild 変数が解決されさえすれば、どのようなバッチ コマンドでも指定できます。 詳細については、次を参照してください。[する方法: SharePoint の配置コマンドを設定](../sharepoint/how-to-set-sharepoint-deployment-commands.md)です。|  
|配置前コマンド ライン|SharePoint ソリューションを配置する前に実行するコマンドを指定します。 この行では、MSBuild 変数が解決されさえすれば、どのようなバッチ コマンドでも指定できます。 詳細については、次を参照してください。[する方法: SharePoint の配置コマンドを設定](../sharepoint/how-to-set-sharepoint-deployment-commands.md)です。|  
|プロジェクト ファイル|プロジェクトのビルド、構成、およびその他の情報を含むファイルの名前です。|  
|プロジェクト フォルダー|システム上のプロジェクト ファイルの場所。 システム テーブルは読み取り専用です。|  
|Sandboxed Solution|プロジェクトを *サンドボックス ソリューション*( *ユーザー作成のソリューション*とも呼ばれる) として配置するかどうかを指定します。 サンドボックス ソリューションは必ずしも信頼できません。 値が **true** の場合、プロジェクトはサンドボックス ソリューションとして配置され、 **false** の場合、プロジェクトはファーム ソリューションとして配置されます。 詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)と[違いサンド ボックス ソリューションとファーム ソリューション](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)です。|  
|サイト URL|このプロジェクトの対象サイトの [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] を指定します。|  
|スタートアップ アイテム|プロジェクトで最初に実行される項目を指定します。|  
  
 SharePoint の項目ファイル (ワークフローや [Features] ノードのフィーチャーなど) を選択すると、[プロパティ] ウィンドウに次のプロパティが表示されます。  
  
### <a name="project-item-properties"></a>プロジェクト項目のプロパティ  
  
|プロパティ名|説明|  
|-------------------|-----------------|  
|配置競合の解決|配置するプロジェクト アイテムのプロパティが既にサーバー上にあるアイテムのプロパティと同じであった場合に実行される動作を指定します。 詳細については、次を参照してください。[トラブルシューティング SharePoint のパッケージ化と配置](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)です。|  
|機能のプロパティ|フィーチャーが SharePoint に配置されるときに一緒に含まれる一連の値 (キー/値のペアとして格納されます) を指定します。 フィーチャーが配置されると、そのプロパティ値にコードでアクセスできるようになります。 詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。|  
|フィーチャー レシーバー|プロジェクト項目の対象フィーチャーで特定のイベントが発生した場合に実行されるコードが用意されています。 詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。|  
|フォルダー名|SharePoint プロジェクト項目フォルダーの名前。|  
|プロジェクト出力参照|プロジェクト項目の実行に必要な依存関係 (アセンブリなど) を指定します。 詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。|  
|安全なコントロール エントリ|信頼関係のないユーザーが編集しても安全なコントロールを指定します。 詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)です。|  
  
### <a name="project-item-file-properties"></a>プロジェクト項目ファイルのプロパティ  
  
|プロパティ名|説明|  
|-------------------|-----------------|  
|ビルド アクション|ファイルとビルド プロセスおよび配置プロセスの関係を指定します。 詳細については、「 [ファイルのプロパティ](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)」を参照してください。|  
|出力ディレクトリにコピー|出力ディレクトリにソース ファイルをコピーするかどうかを指定します。 次のいずれかの値になります。<br /><br /> -   *コピーしません。*<br />-   *常にコピーします。*<br />-   *新しい場合はコピーします。*<br /><br /> 詳細については、「 [ファイルのプロパティ](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)」を参照してください。|  
|カスタム ツール|デザイン時にファイルを変換し、変換の結果を別のファイルに出力するツールが存在する場合に、そのツールの名前を指定します。 たとえば、データセット (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) ファイルでは既定のカスタム ツールを使用できます。 詳細については、「 [ファイルのプロパティ](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)」を参照してください。|  
|カスタム ツールの名前空間|カスタム ツールの出力がコピーされる名前空間です。 詳細については、「 [ファイルのプロパティ](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)」を参照してください。|  
|配置場所|SharePoint サーバー上のファイルの完全修飾パス。 このパスは、[配置ルート] プロパティと [配置パス] プロパティで構成されます。|  
|配置パス|Workflow1 など、SharePoint サーバー上のファイルの相対パス\\です。 ファイルの完全修飾パスは、 *Deployment Path* 値の末尾に *Deployment Root* 値を連結することによって作成されます。<br /><br /> 値を選択する*RootFile*の*展開の種類*プロパティが変更された、*配置ルート*プロパティ {sharepointroot} を\\、その結果には完全修飾パスが {sharepointroot} \Workflow1\\です。 詳細については、次を参照してください。[パッケージ化と SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)です。|  
|Deployment Root|文字列。 ファイルの配置先となる SharePoint Server 上のルート フォルダーです たとえば、{sharepointroot} \Template\Features\\{FeatureName}\\です。<br /><br /> *Deployment Root* プロパティの値は、 *Deployment Type* の設定に依存します。|  
|Deployment Type|ファイルの配置の種類です。 *Deployment Root* 値に依存します。 次のいずれかの値になります。<br /><br /> NoDeployment:\<値なし ><br /><br /> ElementManifest: {sharepointroot} \Template\Features\\{FeatureName}\\<br /><br /> ElementFile: {sharepointroot} \Template\Features\\{FeatureName}\\<br /><br /> TemplateFile: {sharepointroot} \Template\\<br /><br /> RootFile: {sharepointroot}\\<br /><br /> GlobalResource: {sharepointroot} \Resources\\<br /><br /> ClassResource: {ClassResourcePath}\\<br /><br /> 詳細については、「<xref:Microsoft.VisualStudio.SharePoint.DeploymentType>」を参照してください。|  
|ファイル名|項目ファイルの名前またはフォルダーの名前です。|  
|完全パス|項目ファイルの場所です。 システム テーブルは読み取り専用です。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で使用できる SharePoint プロジェクトおよびプロジェクト項目テンプレートについて説明します。|  
|[方法: SharePoint プロジェクトに項目を追加する](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|新規または既存の項目を [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトに追加する方法を説明します。|  
|[チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|カスタム フィールド、コンテンツ タイプ、リスト定義、およびリスト インスタンスの作成手順について説明します。|  
|[方法: イベント レシーバーを作成する](../sharepoint/how-to-create-an-event-receiver.md)|作成されたプロジェクトのイベント レシーバーを追加する方法について説明[チュートリアル: サイト内の列、コンテンツ タイプ、および SharePoint のリストを作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)です。|  
|[SharePoint ワークフロー ソリューションの作成](../sharepoint/creating-sharepoint-workflow-solutions.md)|ワークフローの関連付けフォームおよびワークフローの開始フォームを含んだワークフロー プロジェクトの作成方法を説明します。|  
|[SharePoint 用ページの作成](../sharepoint/creating-pages-for-sharepoint.md)|SharePoint で使用するページ (アプリケーション ページ、サイト ページ、マスター ページなど) の作成方法とページ レイアウトについて説明します。|  
|[SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)|ユーザーがブラウザーから SharePoint サイト ページのコンテンツ、外観、および動作を直接変更できるようにするコントロールを追加する方法について説明します。|  
|[Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|SharePoint で実行されるアプリケーション ページと Web パーツで使用できるユーザー コントロールの作成方法について説明します。|  
|[SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)|Web サービスとバック エンド サーバー アプリケーションのデータを SharePoint アプリケーションに統合する方法を説明します。|  
|[SharePoint のサイト定義の作成](../sharepoint/creating-site-definitions-for-sharepoint.md)|サイト定義 (SharePoint サイトを作成するために使用されるテンプレート) を作成する方法を説明します。|  
|[既存の SharePoint サイトからの項目のインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|既存の SharePoint サイトから [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトにコンテンツ タイプやモジュールなどの項目をインポートする方法を説明します。|  
|[モジュールを使用してソリューションにファイルを含める](../sharepoint/using-modules-to-include-files-in-the-solution.md)|モジュールを使用して [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトのファイルを SharePoint サイトに配置する方法を説明します。|  
|[サーバー エクスプローラーを使用した SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|サーバー エクスプローラーを使用してローカルの SharePoint サイトを閲覧する方法について説明します。|  
|[プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|プロジェクト項目のプロパティを使用して、プロジェクトのパッケージ化と配置に関する情報を提供する方法について説明します。たとえば、コントロール エントリ、プロジェクト出力参照、フィーチャーのプロパティなどです。|  
|[方法: マップされたフォルダーを追加および削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)|SharePoint のリソースに容易にアクセスできるよう、マップされたフォルダーをプロジェクトに追加する方法を説明します。|  
|[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)|サンドボックス ソリューションに関連した問題について説明します。|  
|[SharePoint ソリューションのセキュリティ](../sharepoint/security-for-sharepoint-solutions.md)|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint ソリューションを開発する際のセキュリティ上の考慮事項について説明します。|  
|[URL ピッカー ダイアログ ボックス &#40;です。Visual Studio &#41; での SharePoint 開発](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|プロジェクト内またはローカル SharePoint サーバー上のリソースへのパス参照を追加するために使用できるダイアログ ボックスについて説明します。|  
  
## <a name="see-also"></a>関連項目  
 [作業の開始 (&) #40 です。Visual Studio &#41; での SharePoint 開発](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [サーバー エクスプ ローラーを使用して SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  