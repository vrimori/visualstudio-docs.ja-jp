---
title: "SharePoint ソリューションの開発"
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
  - "VS.SharePointTools.Project.ProjectProperties"
  - "VS.SharePointTools.Project.ProjectItemProperties"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発の概要"
ms.assetid: 059bce0f-c301-4234-a0b4-9c14b7cdfa3e
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# SharePoint ソリューションの開発
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には、SharePoint サイトおよびサイト要素を作成するための SharePoint プロジェクトの種類のテンプレートがいくつか用意されています。 使用可能なプロジェクトの種類の一覧は、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)します。 次に、SharePoint プロジェクトの要素およびプロパティについて説明します。

 SharePoint 2013 および SharePoint について追加\-ins を参照してください [SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) と [ビルド SharePoint を追加\-ins](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx)します。

## <a name="elements-of-a-sharepoint-project"></a>SharePoint プロジェクトの要素
 SharePoint プロジェクトのノードは、 *SharePoint アイテム*と呼ばれます。 また、SharePoint アイテムには、 *SharePoint アイテム ファイル*と呼ばれる 1 つ以上のサブ ファイル ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 構成ファイル、.aspx フォームなど) が含まれる場合があります。

 プロジェクト項目ファイルから成るプロジェクト テンプレートを使用してプロジェクトを作成する代わりに、 **[空のプロジェクト]** テンプレートを使用して、空の SharePoint プロジェクトを作成し、それにプロジェクト項目を手動で追加することもできます。 SharePoint プロジェクトが 1 つまたは複数の機能ファイルを必要に応じて含める \(SharePoint でのアクティブ化\) とパッケージ ファイルをプロジェクトの配布先となります。

### <a name="special-nodes"></a>特殊なノード
 すべての SharePoint プロジェクトに、名前変更、削除、切り取り、コピー、プロジェクトからのドラッグなどの操作ができないノードが 2 つ含まれています。 これらのノードを次に示します。

-   機能

-   パッケージ

 プロジェクトにフィーチャーまたはパッケージが定義されているかどうかに関係なく、この 2 つのノードはすべての SharePoint プロジェクトに必ず表示されます。

#### <a name="features-node"></a>[Features] ノード
 **[Features]** ノードには、SharePoint プロジェクトのフィーチャーが 1 つ以上含まれています。 フィーチャーとは、SharePoint の拡張機能のコンテナーのことです。 SharePoint サーバーにフィーチャーを配置すると、SharePoint サイトの SharePoint 管理者が、そのフィーチャーをサイト定義に追加したり、個別にアクティブ化したりすることができます。 詳細については、「 [フィーチャーの使用](http://go.microsoft.com/fwlink/?LinkID=147704)」を参照してください。

 コンテンツ タイプやリスト インスタンスなどのアイテムを SharePoint プロジェクトに追加すると、 **[Features]** ノード内のフィーチャーに追加されます。 新しいフィーチャーに追加されるか、既存のフィーチャーに追加されるかは、そのアイテムのスコープによって決まります。 新しい項目が既存のフィーチャーと同じスコープを持つ場合は、そのフィーチャーに追加されます。 それ以外の場合は、新しいフィーチャーに追加されます。

 フィーチャーを手動で追加するには、そのフィーチャー ノードのショートカット メニューから **[フィーチャーの追加]** コマンドを実行します。 フィーチャーの内容は、フィーチャー デザイナーを使用して表示または変更することができます。 詳細については、次を参照してください。 [方法: SharePoint フィーチャーをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-feature.md)です。

 SharePoint プロジェクトに追加したフィーチャーは、 **ソリューション エクスプローラー** にノードとして表示され、"Feature*x*.feature" という既定の名前が付けられます ( *x* は一意の番号)。 SharePoint Server にフィーチャーが配置されると、SharePoint 管理者は SharePoint サイト ユーザーが使用できるようにそれをアクティブ化することができます。

#### <a name="package-node"></a>[Package] ノード
 **[Package]** ノードには、SharePoint プロジェクトの配布メカニズムとして機能するファイルが 1 つだけ含まれています。 呼ばれるこのファイルを *ソリューション**パッケージ*, 、です。CAB\-基に、です。WSP 拡張子です。 ソリューション パッケージは、SharePoint サイトに適用される一連のフィーチャー、サイト定義、およびアセンブリを含んでいる配置可能で再利用可能なファイルであり、これは個別に有効または無効にできます。 **[Package]** ノードには、パッケージの [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 定義ファイルである Package.wspdef というファイルも必ず含まれています。 SharePoint を実行しているサーバーにパッケージが配置されると、SharePoint 管理者はそのパッケージをインストールしてフィーチャーをアクティブにできます。

 表示したり、ダブルクリックして、パッケージ デザイナーでパッケージの内容を変更する\-パッケージ ノードをクリックするか、ショートカット メニューを開くことによって]、[ **開く**します。 詳細については、次を参照してください。 [SharePoint ソリューション パッケージの作成](../sharepoint/creating-sharepoint-solution-packages.md)します。

## <a name="sharepoint-project-and-project-item-properties"></a>SharePoint プロジェクトとプロジェクト項目のプロパティ
 SharePoint プロジェクトでは、他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトと同様、[プロパティ] ウィンドウおよび [プロパティ] ページにプロパティが表示されます。 表示されるプロパティは、選択したノードによって異なります。

 **ソリューション エクスプローラー**で SharePoint プロジェクト ノード、プロジェクト項目ノード、またはプロジェクト項目ファイル ノードを選択すると、次のプロパティが [プロパティ] ウィンドウまたは [プロパティ] ページに表示されます。

### <a name="project-properties"></a>プロジェクトのプロパティ

|プロパティ名|説明|
|-------------------|-----------------|
|アクティブな配置構成|配置中に実行される一連の手順を指定します。 詳細については、「 [How to: Edit a SharePoint Deployment Configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)」を参照してください。|
|アセンブリの配置先|*SharePoint アプリケーション アセンブリ* の場所を決定します。 有効なアセンブリの場所の値は、 *GlobalAssemblyCache* \(既定\), 、または *WebApplication*します。<br /><br /> *Sandboxed Solution* プロパティが **true**に設定されている場合、このプロパティは無効です。|
|自動\-デバッグ後に取り消し|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]のデバッグ モードでアプリケーションを実行した後、配置されたソリューションを SharePoint から自動的に取り消すかどうかを指定します。 オンにすると、デバッグ後に IDE がデザイン ビューに戻ると、ソリューションは取り消されます。 オフにすると、ソリューションは取り消されません。 詳細については、「 [ソリューションを取り消す](http://go.microsoft.com/fwlink/?LinkId=183819)」を参照してください。|
|構成の編集|プロジェクトに使用する配置の構成を指定します。 詳細については、次を参照してください。 [方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) と [を展開する、発行、および SharePoint ソリューション パッケージのアップグレード](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)します。|
|Silverlight デバッグを有効にする \(スクリプトのデバッグではなく\)|オンにすると、Silverlight デバッガーがデバッグ プロセスにアタッチされます。 オフにすると、スクリプト デバッガーがデバッグ プロセスにアタッチされます。 詳細については、「 [Silverlight デバッグの概要](http://go.microsoft.com/fwlink/?LinkId=179826)」を参照してください。|
|パッケージにアセンブリを含める|プロジェクト アセンブリをビルド時にパッケージ化するかどうかを指定します。|
|Post\-デプロイ コマンドライン|SharePoint ソリューションを配置した後で実行するコマンドを指定します。 この行では、MSBuild 変数が解決されさえすれば、どのようなバッチ コマンドでも指定できます。 詳細については、「 [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md)」を参照してください。|
|プレ\-デプロイ コマンドライン|SharePoint ソリューションを配置する前に実行するコマンドを指定します。 この行では、MSBuild 変数が解決されさえすれば、どのようなバッチ コマンドでも指定できます。 詳細については、「 [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md)」を参照してください。|
|プロジェクト ファイル|プロジェクトのビルド、構成、およびその他の情報を含むファイルの名前です。|
|プロジェクト フォルダー|システム上のプロジェクト ファイルの場所。 \(読み取り\-のみです。\)|
|Sandboxed Solution|としてプロジェクトを配置するかどうかを指定、 *サンド ボックス ソリューション*, とも呼ばれる、 *ユーザー\-ソリューションを作成*します。 サンドボックス ソリューションは必ずしも信頼できません。 値が **true** の場合、プロジェクトはサンドボックス ソリューションとして配置され、 **false** の場合、プロジェクトはファーム ソリューションとして配置されます。 詳細については、次のトピックを参照してください。 [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) および [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|
|サイト URL|このプロジェクトの対象サイトの [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] を指定します。|
|スタートアップ アイテム|プロジェクトで最初に実行される項目を指定します。|

 SharePoint の項目ファイルを選択すると \(ワークフローや [Features] ノードのフィーチャーなど\), 、プロパティ ウィンドウで、次のプロパティが表示されます。

### <a name="project-item-properties"></a>プロジェクト項目のプロパティ

|プロパティ名|説明|
|-------------------|-----------------|
|配置競合の解決|配置するプロジェクト アイテムのプロパティが既にサーバー上にあるアイテムのプロパティと同じであった場合に実行される動作を指定します。 詳細については、「 [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)」を参照してください。|
|機能のプロパティ|一連の値を示す \(キーとして格納されている\/値のペア\) を SharePoint に展開するときに使用できる機能に含まれます。 フィーチャーが配置されると、そのプロパティ値にコードでアクセスできるようになります。 詳細については、「 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。|
|フィーチャー レシーバー|プロジェクト項目の対象フィーチャーで特定のイベントが発生した場合に実行されるコードが用意されています。 詳細については、「 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。|
|フォルダー名|SharePoint プロジェクト項目フォルダーの名前。|
|プロジェクト出力参照|プロジェクト項目の実行に必要な依存関係 (アセンブリなど) を指定します。 詳細については、「 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。|
|安全なコントロール エントリ|信頼関係のないユーザーが編集しても安全なコントロールを指定します。 詳細については、「 [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」を参照してください。|

### <a name="project-item-file-properties"></a>プロジェクト項目ファイルのプロパティ

|プロパティ名|説明|
|-------------------|-----------------|
|ビルド アクション|ファイルとビルド プロセスおよび配置プロセスの関係を指定します。 詳細については、「 [ファイルのプロパティ](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)」を参照してください。|
|出力ディレクトリにコピー|指定するかどうか、ソース ファイル\(s\) 出力ディレクトリにコピーされます。 次のいずれかの値になります。<br /><br /> -   *コピーしません。*<br />-   *常にコピーします。*<br />-   *新しい場合はコピーします。*<br /><br /> 詳細については、「 [ファイルのプロパティ](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)」を参照してください。|
|カスタム ツール|デザイン時にファイルを変換し、変換の結果を別のファイルに出力するツールが存在する場合に、そのツールの名前を指定します。 たとえば、データセット \(します。[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]\) ファイルには、既定のカスタム ツールがあります。 詳細については、「 [ファイルのプロパティ](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)」を参照してください。|
|カスタム ツールの名前空間|カスタム ツールの出力がコピーされる名前空間です。 詳細については、「 [ファイルのプロパティ](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx)」を参照してください。|
|配置場所|完全に\-、SharePoint サーバー上のファイルのパスを修飾します。 このパスは配置ルートと [配置パスのサブから成る\-プロパティです。|
|配置パス|Workflow1 など、SharePoint サーバー上のファイルの相対パス\\します。 完全に\-連結することによって、ファイルの修飾パスを作成、 *展開パス* 値の末尾に、 *配置ルート* 値。<br /><br /> 値を選択する *RootFile* の *展開の種類* プロパティが変更された、 *配置ルート* プロパティ {sharepointroot} を\\, でその結果、完全に\-{sharepointroot} の修飾パス\\Workflow1\\します。 詳細については、次を参照してください。 [パッケージ化と SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)します。|
|Deployment Root|文字列。 ファイルの配置先となる SharePoint Server 上のルート フォルダーです たとえば、{sharepointroot}\\テンプレート\\機能\\{FeatureName}\\します。<br /><br /> *Deployment Root* プロパティの値は、 *Deployment Type* の設定に依存します。|
|Deployment Type|ファイルの配置の種類です。 *Deployment Root* 値に依存します。 次のいずれかの値になります。<br /><br /> NoDeployment: \<値はありません\><br /><br /> ElementManifest: {sharepointroot}\\テンプレート\\機能\\{FeatureName}\\<br /><br /> ElementFile: {sharepointroot}\\テンプレート\\機能\\{FeatureName}\\<br /><br /> TemplateFile: {sharepointroot}\\テンプレート\\<br /><br /> RootFile: {sharepointroot}\\<br /><br /> GlobalResource: {sharepointroot}\\リソース\\<br /><br /> ClassResource: {ClassResourcePath}\\<br /><br /> 詳細については、次を参照してください。 <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>します。|
|ファイル名|項目ファイルの名前またはフォルダーの名前です。|
|完全パス|項目ファイルの場所です。 \(読み取り\-のみです。\)|

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で使用できる SharePoint プロジェクトおよびプロジェクト項目テンプレートについて説明します。|
|[方法: SharePoint プロジェクトに項目を追加](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|新規または既存の項目を [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトに追加する方法を説明します。|
|[チュートリアル: サイト内の列、コンテンツ タイプ、および SharePoint のリストを作成します。](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|ステップ実行する潜在顧客\-によって\-フィールド、コンテンツ タイプ、リスト定義、およびリスト インスタンスは、顧客を作成する手順です。|
|[方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)|作成したプロジェクトのイベント レシーバーを追加する方法について説明 [チュートリアル: サイト内の列、コンテンツの種類、および SharePoint のリストを作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)します。|
|[SharePoint ワークフロー ソリューションを作成します。](../sharepoint/creating-sharepoint-workflow-solutions.md)|ワークフローの関連付けフォームおよびワークフローの開始フォームを含んだワークフロー プロジェクトの作成方法を説明します。|
|[SharePoint 用ページの作成](../sharepoint/creating-pages-for-sharepoint.md)|SharePoint で使用するページ (アプリケーション ページ、サイト ページ、マスター ページなど) の作成方法とページ レイアウトについて説明します。|
|[SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)|ユーザーがブラウザーから SharePoint サイト ページのコンテンツ、外観、および動作を直接変更できるようにするコントロールを追加する方法について説明します。|
|[Web パーツまたはアプリケーション ページの再利用可能なコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|SharePoint で実行されるアプリケーション ページと Web パーツで使用できるユーザー コントロールの作成方法について説明します。|
|[SharePoint にビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)|Web サービスからデータを統合し、バックアップを作成する方法について説明\-SharePoint アプリケーションにサーバー アプリケーションを終了します。|
|[SharePoint のサイト定義を作成します。](../sharepoint/creating-site-definitions-for-sharepoint.md)|サイト定義 (SharePoint サイトを作成するために使用されるテンプレート) を作成する方法を説明します。|
|[既存の SharePoint サイトからのアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|既存の SharePoint サイトから [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトにコンテンツ タイプやモジュールなどの項目をインポートする方法を説明します。|
|[モジュールを使用して、ソリューションにファイルを含める](../sharepoint/using-modules-to-include-files-in-the-solution.md)|モジュールを使用して [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトのファイルを SharePoint サイトに配置する方法を説明します。|
|[サーバー エクスプ ローラーを使用して SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|サーバー エクスプローラーを使用してローカルの SharePoint サイトを閲覧する方法について説明します。|
|[パッケージとプロジェクト アイテムの展開情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|プロジェクト項目のプロパティを使用して、プロジェクトのパッケージ化と配置に関する情報を提供する方法について説明します。たとえば、コントロール エントリ、プロジェクト出力参照、フィーチャーのプロパティなどです。|
|[方法: 追加およびマップされたフォルダーの削除](../sharepoint/how-to-add-and-remove-mapped-folders.md)|SharePoint のリソースに容易にアクセスできるよう、マップされたフォルダーをプロジェクトに追加する方法を説明します。|
|[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)|サンドボックス ソリューションに関連した問題について説明します。|
|[SharePoint ソリューションのセキュリティ](../sharepoint/security-for-sharepoint-solutions.md)|[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で SharePoint ソリューションを開発する際のセキュリティ上の考慮事項について説明します。|
|[URL ピッカー ダイアログ ボックスと #40 です。Visual Studio &#41; での SharePoint 開発](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|プロジェクト内またはローカル SharePoint サーバー上のリソースへのパス参照を追加するために使用できるダイアログ ボックスについて説明します。|

## <a name="see-also"></a>関連項目
 [基本情報および #40 です。Visual Studio &#41; での SharePoint 開発](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md) 
 [サーバー エクスプ ローラーを使用して SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md) 
 [のビルドと SharePoint ソリューションをデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md) 
 [パッケージ化と SharePoint ソリューションの配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

  