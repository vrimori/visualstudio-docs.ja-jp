---
title: SharePoint プロジェクトとプロジェクト項目テンプレート |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d671c397f139cfaa51bd664e5324a32cce671361
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint プロジェクトとプロジェクト項目テンプレート
  以下のセクションでは、SharePoint プロジェクトとプロジェクト項目の使用可能なテンプレート、およびそれらの使用方法について説明します。 
  
##  <a name="project-and-project-item-templates-overview"></a>プロジェクトとプロジェクト項目テンプレートの概要  
 Visual Studio で新しい SharePoint プロジェクトを作成するときに、SharePoint プロジェクトがすべてのプロジェクトの種類で必要なプロジェクト項目と共にソリューションに追加されます。 たとえば、Silverlight Web パーツ プロジェクトを作成した場合、視覚的 Web パーツ プロジェクト項目と Silverlight アプリケーション プロジェクト項目、およびそれらのプロジェクト項目に必要なすべてのファイルを含むソリューションが作成されます。 プロジェクト項目テンプレートは、既存の SharePoint プロジェクトにプロジェクト項目 (イベント レシーバー、サイト列、リストなど) を追加する目的で使用されます。  
  
 SharePoint の基本事項については、次を参照してください。 [SharePoint Foundation のビルド ブロック](http://go.microsoft.com/fwlink/?LinkId=179404)です。 上級ユーザーは、プロジェクトやプロジェクト項目のテンプレートを独自に作成することもできます。 詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張する](../sharepoint/extending-the-sharepoint-project-system.md)です。  
  
##  <a name="project-templates"></a>プロジェクト テンプレート  
 ここでは、それぞれの SharePoint プロジェクト テンプレートについて説明します。 Visual Studio での SharePoint プロジェクト テンプレートを表示する、**新しいプロジェクト** ダイアログ ボックスで、展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し**2010**です。  
  
### <a name="sharepoint-2010-project"></a>SharePoint 2010 プロジェクト  
 内容、 *SharePoint 2010 プロジェクト*すべての SharePoint プロジェクト テンプレートに含まれています。 SharePoint 2010 プロジェクトの内容は次のとおりです。  
  
-   プロジェクト ファイル。  
  
-   プロジェクトのプロパティ ページ。  
  
-   A**参照**フォルダーのすべてのプロジェクトでアセンブリ参照の一覧を表示します。  
  
-   A**機能**フィーチャーを配置する SharePoint サーバーに使用される .feature 構成ファイルを格納するフォルダーです。  
  
-   A**パッケージ**Package.package ファイルを SharePoint にソリューションを配置するために使用が含まれているフォルダーです。  
  
-   key.snk (厳密名キー) ファイル。セキュリティ対策としてアセンブリに厳密な名前で署名するために使用されます。  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight Web パーツ  
 *SharePoint 2010 Silverlight Web パーツ*プロジェクトでは、Silverlight アプリケーションを表示する SharePoint の web パーツを作成することができます。 このプロジェクトを作成するときは、新しい Silverlight アプリケーションを追加するか既存の Silverlight アプリケーションを参照するかを指定できます。 詳細については、次を参照してください。 [for SharePoint Web パーツを作成する](../sharepoint/creating-web-parts-for-sharepoint.md)と[チュートリアル: SharePoint のその表示 OData Silverlight Web パーツを作成](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)です。  
  
### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 視覚的 Web パーツ  
 A *SharePoint 2010 視覚的 Web パーツ*、Elements.xml 定義ファイルがプロジェクトに含まれています、 **Web パーツ**項目、および**ユーザー コントロール**項目。 ドラッグするか、ユーザー コントロールの画面に、Visual Studio のツールボックスからコントロールをコピーして、視覚的 web パーツの外観をデザインできます。 詳細については、次を参照してください。[する方法: デザイナーを使用して、SharePoint Web パーツを作成](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)と[ビルディング ブロック: Web パーツ](http://go.microsoft.com/fwlink/?LinkId=179438)です。  
  
### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010 ソリューション パッケージのインポート  
 *SharePoint 2010 ソリューション パッケージのインポート*プロジェクト ファイルにエクスポートする SharePoint ソリューション (.wsp)、Visual Studio に、既存の SharePoint 2010 サイトのすべてまたは一部をインポートできます。 Visual Studio にインポートした後は、その項目をカスタマイズして再配置することができます。 詳細については、次を参照してください。[既存の SharePoint サイトからインポートする項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)です。  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>再利用可能な SharePoint 2010 ワークフローのインポート  
 *再利用可能な SharePoint 2010 ワークフローのインポート*プロジェクトでは、Visual Studio SharePoint Designer 2010 で作成した再利用可能な宣言型ワークフローをインポートできます。 ワークフローは、SharePoint サイトから .wsp ファイルとしてエクスポートされます。 Visual Studio にインポートした後は、カスタマイズしたりコードを追加したりして、SharePoint サイトに配置できます。 詳細については、次を参照してください。[チュートリアル: SharePoint Designer の再利用可能なワークフローを Visual Studio にインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)です。  
  
##  <a name="project-item-templates"></a>プロジェクト項目テンプレート  
 ここでは、それぞれの SharePoint プロジェクト項目テンプレートについて説明します。 プロジェクト項目テンプレートでは、サイト列、リスト、コンテンツ タイプなどの SharePoint 機能をサポートするために、SharePoint ソリューションにファイルを追加します。 たとえば、サイト列をソリューションに追加すると、Elements.xml 定義ファイルを含むサイト列プロジェクトが追加されます。 また、視覚的 Web パーツを追加すると、Elements.xml ファイル、ユーザー コントロール項目、および視覚的 Web パーツ項目を含む視覚的 Web パーツ プロジェクトがソリューションに追加されます。  
  
 SharePoint プロジェクト項目テンプレートを表示する**ソリューション エクスプ ローラー**SharePoint プロジェクトのショートカット メニューを開きを選択し、**追加**、**新しい項目の**します。 展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し**2010**です。  
  
### <a name="application-page-farm-solution-only"></a>アプリケーション ページ (ファーム ソリューションのみ)  
 **アプリケーション ページ (ファーム ソリューションのみ)**項目では、設計することができます、 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] SharePoint サイトの web ページ。 アプリケーション ページは、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。[する方法: アプリケーション ページを作成](../sharepoint/how-to-create-an-application-page.md)と[アプリケーション _layouts ページ型](http://go.microsoft.com/fwlink/?LinkId=179434)です。  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>ビジネス データ接続モデル (ファーム ソリューションのみ)  
 A**ビジネス データ接続モデル (ファーム ソリューションのみ)**項目では、SharePoint にビジネス データを統合することができます。 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]、Siebel、Service Advertising Protocol (SAP) などのバック エンドのサーバー アプリケーションからのデータを使用できます。 ビジネス データ接続モデル (ファーム ソリューションのみ) は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください[する方法: BDC モデルを作成](../sharepoint/how-to-create-a-bdc-model.md)、[する方法: ローカライズされた名前の指定、プロパティ、およびアクセス許可をリソース ファイルを使用して](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)、および[新機能: ビジネス接続。サービス](http://go.microsoft.com/fwlink/?LinkId=179411)です。  
  
### <a name="content-type"></a>コンテンツ タイプ  
 *コンテンツの種類*項目では、既存の (基本) コンテンツ タイプのドキュメント、お知らせ、タスクなどに基づくカスタム コンテンツ タイプを作成できます。 カスタム コンテンツ タイプでは、独自に定義したサイト列 (フィールド) に加えて、ベース コンテンツ タイプと同じ属性およびフィールドを使用できます。 たとえば、SharePoint に付属している基本の Contact コンテンツ タイプを基にしてカスタムの Contact コンテンツ タイプを作成できます。 コンテンツ タイプのカスタマイズでは、基本コンテンツ タイプの既存のサイト列を変更したり、別のサイト列を追加したりできます。  
  
> [!NOTE]  
>  SharePoint の制限により、サンドボックス ソリューション コンテンツ タイプを基にしてファーム ソリューション コンテンツ タイプを作成することはできません。  
  
 詳細については、次を参照してください。[チュートリアル: サイト内の列、コンテンツ タイプ、および SharePoint のリストを作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)と[ビルディング ブロック: コンテンツの種類](http://go.microsoft.com/fwlink/?LinkId=179413)です。  
  
### <a name="empty-element"></a>空の要素  
 *要素を空にする*プロジェクトまたは Visual Studio でプロジェクト項目テンプレートを持たない SharePoint プロジェクト項目を定義する最もよく使用されます。 EmptyElement というノードで、プロジェクトに空の要素を追加するときに [x](where [x] is a unique number\) is created. EmptyElement [x] には、Elements.xml という 1 つのファイルが含まれています。 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ステートメントを使用して、必要な要素を Elements.xml で定義します。  
  
### <a name="event-receiver"></a>イベント レシーバー  
 *イベント レシーバー*など、アイテムを一覧に追加するときに、web 項目が削除されたとき、またはワークフローが開始されたときに、SharePoint サイト内の項目のイベントを処理します。 イベント レシーバー プロジェクト項目テンプレートで処理できるイベントは次のとおりです。  
  
-   リスト イベント  
  
-   リスト アイテム イベント  
  
-   リスト電子メール イベント  
  
-   Web イベント  
  
-   リスト ワークフロー イベント  
  
 イベント レシーバー プロジェクト項目を作成、**イベント レシーバー**でプロジェクトを作成したときに指定したすべてのイベントのイベント ハンドラーを含む 1 つのクラス ファイルとフォルダー、 **SharePoint のカスタマイズウィザード**です。 イベント レシーバー クラスでは、ファイル、フィールド、アイテム、リスト、添付ファイル、web パーツ、およびワークフローなどの項目が追加、更新、削除、または削除時に、SharePoint サイトで発生するイベントを処理できます。 詳細については、次を参照してください。[する方法: イベント レシーバーを作成する](../sharepoint/how-to-create-an-event-receiver.md)と[ビルディング ブロック: イベント処理の](http://go.microsoft.com/fwlink/?LinkId=179416)します。  
  
### <a name="list"></a>リスト  
 リストは、再利用可能な基本の SharePoint リスト定義のインスタンスです (予定表、タスク リストなど)。 ソリューションにリストを追加した後、リスト デザイナーで、リストにサイト列を追加したり、リストのカスタム列を作成したりできます。 これにはコンテンツ タイプのサイト列が含まれます。 指定することができます、*ビュー*一覧については、一覧に表示される列が決まります。 詳細については、次を参照してください。[チュートリアル: サイト内の列、コンテンツ タイプ、および SharePoint のリストを作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)と[ビルディング ブロック: リストとドキュメント ライブラリ](http://go.microsoft.com/fwlink/?LinkId=179421)です。  
  
### <a name="module"></a>Module  
 *モジュール*(と混同しないでください[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]モジュール) イメージやメモなど、SharePoint サーバーに配置するファイルが含まれています。 モジュールのプロジェクト アイテムが含まれています、**モジュール**ノード。 そのノードに 2 つのプロジェクト項目テンプレートが含まれています。1 つはモジュールのマニフェストとして機能する XML 定義ファイルで、もう 1 つはプレースホルダー ファイルの sample.txt ファイルです。 詳細については、次を参照してください。[ソリューション内のインクルード ファイルを使用してモジュール](../sharepoint/using-modules-to-include-files-in-the-solution.md)と[モジュール](http://go.microsoft.com/fwlink/?LinkId=179425)です。  
  
### <a name="sequential-workflow-farm-solution-only"></a>シーケンシャル ワークフロー (ファーム ソリューションのみ)  
 A*シーケンシャル ワークフロー*する一連の最後の手順を完了するまで順番に実行されるビジネス ロジック ステップです。 シーケンシャル ワークフローは、リストやドキュメントなどの SharePoint アイテムが関係するプロセスを管理する目的で使用します。 サイト レベル (グローバル) のワークフローまたはリスト レベル (ローカル) のワークフローを作成できるほか、ワークフローを自動的に開始するか、手動で開始するかを選択することもできます。 このプロジェクト項目は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。 [SharePoint ワークフロー ソリューションの作成](../sharepoint/creating-sharepoint-workflow-solutions.md)、 [SharePoint Server 2010 でのワークフロー](http://go.microsoft.com/fwlink/?LinkId=260555)、および[新機能: ワークフローの機能強化](http://go.microsoft.com/fwlink/?LinkId=179418)です。  
  
### <a name="silverlight-web-part"></a>Silverlight Web パーツ  
 *Silverlight web パーツ*プロジェクト項目を使用すると、Silverlight アプリケーションを表示する SharePoint の web パーツを作成します。 このプロジェクト項目ソリューションに追加するときは、新しい Silverlight アプリケーションを追加するか既存の Silverlight アプリケーションを後で参照するかを選択できます。 詳細については、次を参照してください。 [for SharePoint Web パーツを作成する](../sharepoint/creating-web-parts-for-sharepoint.md)と[チュートリアル: SharePoint のその表示 OData Silverlight Web パーツを作成](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)です。  
  
### <a name="site-column"></a>サイト列  
 A*サイト列*とも呼ばれる、*フィールド*、SharePoint プロジェクトに追加できる最も基本的な要素の 1 つです。 サイト列はデータの種類を表します。たとえば、連絡先一覧であれば、連絡先の電話番号、テキスト コメント、都市名などです。 詳細については、次を参照してください。[を作成するサイト内の列、コンテンツの種類、および SharePoint のリスト](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)と[列](http://go.microsoft.com/fwlink/?LinkId=226840)です。  
  
### <a name="site-definition-farm-solution-only"></a>サイト定義 (ファーム ソリューションのみ)  
 *サイト定義*プロジェクト項目には、次のファイルを含むサイト定義フォルダーが含まれます。  
  
-   既定の .aspx ページ。サイトの既定の Web ページとして使用されます。  
  
-   onet.xml ファイル。サイトの構成要素の定義が含まれています。  
  
-   Webtemp xml ファイルに表示されるサイト定義構成を指定する、**テンプレートの選択**のセクションで、**新しい SharePoint サイト**ページ。  
  
 サイト定義の追加後は、コードおよびファイルを追加して機能を導入できます。 このプロジェクト項目は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。 [SharePoint のサイト定義を作成する](../sharepoint/creating-site-definitions-for-sharepoint.md)と[サイト定義および構成](http://go.microsoft.com/fwlink/?LinkId=260554)です。  
  
### <a name="state-machine-workflow-farm-solution-only"></a>ステート マシンのワークフロー (ファーム ソリューションのみ)  
 A*ステート マシン ワークフロー*ビジネス ロジックの状態、遷移、およびアクションのセットです。 ステート マシン ワークフローに含まれる各ステップは、順番に実行されるのではなく、アクションおよび状態によってトリガーされます。 シーケンシャル ワークフローと同様に、ステート マシン ワークフローは、リストやドキュメントなどの SharePoint アイテムに関連付けられます。 サイト レベル (グローバル) のワークフローまたはリスト レベル (ローカル) のワークフローを作成できることも、シーケンシャル ワークフローと同じです。 ワークフローを自動的に開始するか手動で開始するかを選択することもできます。 このプロジェクト項目は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。 [SharePoint ワークフロー ソリューションの作成](../sharepoint/creating-sharepoint-workflow-solutions.md)、 [SharePoint Server 2010 でのワークフロー](http://go.microsoft.com/fwlink/?LinkId=260555)、および[新機能: ワークフローの機能強化](http://go.microsoft.com/fwlink/?LinkId=179418)です。  
  
### <a name="user-control-farm-solution-only"></a>ユーザー コントロール (ファーム ソリューションのみ)  
 A*ユーザー コントロール*他の ASP.NET コントロールや SharePoint コントロールを追加できる、再利用可能なカスタム コントロールです。 ユーザー コントロールは、SharePoint で実行されるアプリケーション ページと Web パーツに追加できます。 このプロジェクト項目は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成する](http://go.microsoft.com/fwlink/?LinkId=226841)です。  
  
### <a name="visual-web-part"></a>可視 Web パーツ  
 A*視覚的 web パーツ*プロジェクト項目には、Elements.xml 定義ファイルが含まれています、 **Web パーツ**項目、および**ユーザー コントロール**項目。 ドラッグするか、ユーザー コントロールの画面に、Visual Studio のツールボックスからコントロールをコピーして、視覚的 web パーツの外観をデザインできます。 詳細については、次を参照してください。[する方法: デザイナーを使用して、SharePoint Web パーツを作成](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)と[ビルディング ブロック: Web パーツ](http://go.microsoft.com/fwlink/?LinkId=179438)です。  
  
### <a name="web-part"></a>Web パーツ  
 A *web パーツ*特殊な種類の Web パーツ ページをという名前のページ内で実行されるサーバー側コントロールです。 これらは、SharePoint サイトに表示されるページのビルド ブロックです。 Web パーツ項目には、SharePoint サイト用の Web パーツをデザインするためのファイルが用意されています。 詳細については、次を参照してください。[する方法: SharePoint Web パーツを作成](../sharepoint/how-to-create-a-sharepoint-web-part.md)と[ビルディング ブロック: Web パーツ](http://go.microsoft.com/fwlink/?LinkId=179438)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint 製品およびテクノロジ](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
