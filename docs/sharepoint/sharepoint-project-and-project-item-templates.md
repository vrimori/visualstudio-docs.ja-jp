---
title: SharePoint プロジェクトとプロジェクト項目テンプレート |Microsoft Docs
ms.date: 02/22/2017
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
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f2479d58dfb8e1e28a2de230c0838ef8c8f3768
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872199"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint プロジェクトとプロジェクト項目テンプレート
  以下のセクションでは、SharePoint プロジェクトとプロジェクト項目の使用可能なテンプレート、およびそれらの使用方法について説明します。 
  
## <a name="project-and-project-item-templates-overview"></a>プロジェクトとプロジェクト項目テンプレートの概要
 Visual Studio で新しい SharePoint プロジェクトを作成すると、SharePoint プロジェクトは、すべてのプロジェクトの種類で必要なプロジェクト項目と共にソリューションに追加されます。 たとえば、Silverlight Web パーツ プロジェクトを作成した場合、視覚的 Web パーツ プロジェクト項目と Silverlight アプリケーション プロジェクト項目、およびそれらのプロジェクト項目に必要なすべてのファイルを含むソリューションが作成されます。 プロジェクト項目テンプレートは、既存の SharePoint プロジェクトにプロジェクト項目 (イベント レシーバー、サイト列、リストなど) を追加する目的で使用されます。  
  
 SharePoint の基礎については、次を参照してください。 [SharePoint Foundation のビルド ブロック](http://go.microsoft.com/fwlink/?LinkId=179404)します。 上級ユーザーは、プロジェクトやプロジェクト項目のテンプレートを独自に作成することもできます。 詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張](../sharepoint/extending-the-sharepoint-project-system.md)します。  
  
## <a name="project-templates"></a>プロジェクト テンプレート
 ここでは、それぞれの SharePoint プロジェクト テンプレートについて説明します。 Visual Studio で SharePoint プロジェクト テンプレートを表示する、**新しいプロジェクト** ダイアログ ボックスで、展開、 **SharePoint**のどちらかのノード**Visual c#** または**Visual Basic**を選び、 **2010**します。  
  
### <a name="sharepoint-2010-project"></a>SharePoint 2010 プロジェクト
 内容を*SharePoint 2010 プロジェクト*すべての SharePoint プロジェクト テンプレートに含まれます。 SharePoint 2010 プロジェクトの内容は次のとおりです。  
  
-   プロジェクト ファイル。  
  
-   プロジェクトのプロパティ ページ。  
  
-   A**参照**フォルダーのすべてのプロジェクトでアセンブリ参照の一覧を表示します。  
  
-   A**機能**を含むフォルダーを *.feature*構成ファイル、SharePoint サーバーに機能を展開するために使用します。  
  
-   A**パッケージ**を含むフォルダーを*Package.package*ファイル、ソリューションを SharePoint に配置するために使用します。  
  
-   key.snk (厳密名キー) ファイル。セキュリティ対策としてアセンブリに厳密な名前で署名するために使用されます。  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight web パーツ
 *SharePoint 2010 Silverlight Web パーツ*プロジェクトを有効にする web パーツの作成を Silverlight アプリケーションを表示する SharePoint の。 このプロジェクトを作成するときは、新しい Silverlight アプリケーションを追加するか既存の Silverlight アプリケーションを参照するかを指定できます。 詳細については、次を参照してください。[の SharePoint web パーツを作成](../sharepoint/creating-web-parts-for-sharepoint.md)と[チュートリアル。SharePoint の OData を表示する Silverlight web パーツを作成する](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)します。  
  
### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 視覚的 web パーツ
 A *SharePoint 2010 視覚的 Web パーツ*プロジェクトが含まれています、 *Elements.xml*定義ファイルを**Web パーツ**項目、および**ユーザー コントロール**項目. ドラッグするか、ユーザー コントロールの画面に、Visual Studio のツールボックスからコントロールをコピーして、視覚的 web パーツの外観をデザインできます。 詳細については、「[方法 :デザイナーを使用して、SharePoint web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)と[ビルディング ブロック。Web パーツ](http://go.microsoft.com/fwlink/?LinkId=179438)します。  
  
### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010 ソリューション パッケージのインポート
 *SharePoint 2010 ソリューション パッケージのインポート*プロジェクトでは、SharePoint ソリューションにエクスポートする、既存の SharePoint 2010 サイトのすべてまたは一部をインポートできます (*.wsp*) ファイル、Visual Studio にします。 Visual Studio にインポートした後は、その項目をカスタマイズして再配置することができます。 詳細については、次を参照してください。[既存の SharePoint サイトからアイテムをインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)します。  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>再利用可能な SharePoint 2010 ワークフローをインポートします。
 *再利用可能な SharePoint 2010 ワークフローのインポート*プロジェクトでは、Visual Studio SharePoint Designer 2010 で作成した再利用可能な宣言型ワークフローをインポートできます。 ワークフローは、SharePoint サイトからエクスポート、 *.wsp*ファイル。 Visual Studio にインポートした後は、カスタマイズしたりコードを追加したりして、SharePoint サイトに配置できます。 詳細については、「[チュートリアル:SharePoint Designer の再利用可能なワークフローを Visual Studio にインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)します。  
  
## <a name="project-item-templates"></a>プロジェクト項目テンプレート
 ここでは、それぞれの SharePoint プロジェクト項目テンプレートについて説明します。 プロジェクト項目テンプレートでは、サイト列、リスト、コンテンツ タイプなどの SharePoint 機能をサポートするために、SharePoint ソリューションにファイルを追加します。 ソリューションへのサイト内の列の追加を含むサイト列プロジェクトを追加するなど、 *Elements.xml*定義ファイル。 含むソリューションを視覚的 web パーツのプロジェクトを視覚的 web パーツを追加する追加、 *Elements.xml*ファイルやユーザー コントロールの項目を視覚的 web パーツの項目。  
  
 SharePoint プロジェクト項目テンプレートを表示する**ソリューション エクスプ ローラー**SharePoint プロジェクトのショートカット メニューを開き、選択し、**追加**、**新しい項目の**します。 展開、 **SharePoint**のどちらかのノード**Visual c#** または**Visual Basic**を選び、 **2010**します。  
  
### <a name="application-page-farm-solution-only"></a>アプリケーション ページ (ファーム ソリューションのみ)
 **アプリケーション ページ (ファーム ソリューションのみ)** 項目では、設計することができます、 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] SharePoint サイトの web ページ。 アプリケーション ページは、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、「[方法 :アプリケーション ページを作成](../sharepoint/how-to-create-an-application-page.md)と[アプリケーション _layouts ページの種類](http://go.microsoft.com/fwlink/?LinkId=179434)します。  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>ビジネス データ接続モデル (ファーム ソリューションのみ)
 A**ビジネス データ接続モデル (ファーム ソリューションのみ)** 項目により、ビジネス データの統合を SharePoint にします。 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]、Siebel、Service Advertising Protocol (SAP) などのバック エンドのサーバー アプリケーションからのデータを使用できます。 ビジネス データ接続モデル (ファーム ソリューションのみ) は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、「[方法 :BDC モデルを作成](../sharepoint/how-to-create-a-bdc-model.md)、[方法。ローカライズされた名前、プロパティ、およびアクセス許可を指定するリソース ファイルを使用して](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)、および[はの新機能。Business Connectivity Services](http://go.microsoft.com/fwlink/?LinkId=179411)します。  
  
### <a name="content-type"></a>コンテンツ タイプ
 *コンテンツの種類*項目では、ドキュメント、お知らせ、タスクなど既存の (基本) コンテンツ タイプに基づいて、カスタム コンテンツ タイプを作成できます。 カスタム コンテンツ タイプでは、独自に定義したサイト列 (フィールド) に加えて、ベース コンテンツ タイプと同じ属性およびフィールドを使用できます。 たとえば、SharePoint に付属している基本の Contact コンテンツ タイプを基にしてカスタムの Contact コンテンツ タイプを作成できます。 コンテンツ タイプのカスタマイズでは、基本コンテンツ タイプの既存のサイト列を変更したり、別のサイト列を追加したりできます。  
  
> [!NOTE]  
>  SharePoint の制限により、サンドボックス ソリューション コンテンツ タイプを基にしてファーム ソリューション コンテンツ タイプを作成することはできません。  
  
 詳細については、「[チュートリアル:For SharePoint のサイト列、コンテンツの種類、および一覧の作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)と[ビルディング ブロック。コンテンツの種類](http://go.microsoft.com/fwlink/?LinkId=179413)します。  
  
### <a name="empty-element"></a>空要素
 *空の要素*プロジェクトまたは Visual Studio でプロジェクト項目テンプレートを持たない SharePoint プロジェクト項目を定義する最もよく使用されます。 EmptyElement というノードで、プロジェクトに空の要素を追加すると [x](where [x] is a unique number\) is created. EmptyElement [x] を含む 1 つのファイルは名前付き*Elements.xml します。* 使用[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]で目的の要素を定義するステートメント*Elements.xml*します。  
  
### <a name="event-receiver"></a>イベント レシーバー
 *イベント レシーバー*リストに項目を追加するときに、web 項目が削除されたとき、またはワークフローの開始など、SharePoint サイト内の項目のイベントを処理します。 イベント レシーバー プロジェクト項目テンプレートで処理できるイベントは次のとおりです。  
  
- リスト イベント  
  
- リスト アイテム イベント  
  
- リスト電子メール イベント  
  
- Web イベント  
  
- リスト ワークフロー イベント  
  
  イベント レシーバー プロジェクト項目を作成、**イベント レシーバー**フォルダーで、プロジェクトの作成時に指定するすべてのイベントのイベント ハンドラーを含む 1 つのクラス ファイルを使用して、 **SharePoint のカスタマイズウィザード**します。 イベント レシーバー クラスには、ファイル、フィールド、アイテム、リスト、添付ファイル、web パーツ、およびワークフローなどの項目が追加、更新、削除、または削除するときに、SharePoint サイトで発生するイベントを処理できます。 詳細については、「[方法 :イベント レシーバーを作成](../sharepoint/how-to-create-an-event-receiver.md)と[ビルディング ブロック。イベント処理](http://go.microsoft.com/fwlink/?LinkId=179416)します。  
  
### <a name="list"></a>リスト  
 リストは、再利用可能な基本の SharePoint リスト定義のインスタンスです (予定表、タスク リストなど)。 ソリューションにリストを追加した後、リスト デザイナーで、リストにサイト列を追加したり、リストのカスタム列を作成したりできます。 これにはコンテンツ タイプのサイト列が含まれます。 指定することができます、*ビュー*一覧については、一覧に表示される列が決まります。 詳細については、「[チュートリアル:For SharePoint のサイト列、コンテンツの種類、および一覧の作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)と[ビルディング ブロック。リストとドキュメント ライブラリ](http://go.microsoft.com/fwlink/?LinkId=179421)します。  
  
### <a name="module"></a>Module  
 *モジュール*(と混同しないように[!include[vbprvb](../sharepoint/includes/vbprvb-md.md)]モジュール) イメージやメモなど、SharePoint サーバーに配置したいファイルが含まれています。 モジュール プロジェクト項目が含まれています、**モジュール**ノード。 モジュールのノードには、2 つのプロジェクト項目テンプレートが含まれています: モジュールのマニフェストとして機能する、XML 定義ファイルと*sample.txt*ファイル、プレース ホルダー ファイル。 詳細については、次を参照してください。[ソリューション内のインクルード ファイルにモジュールを使用して](../sharepoint/using-modules-to-include-files-in-the-solution.md)と[モジュール](http://go.microsoft.com/fwlink/?LinkId=179425)します。  
  
### <a name="sequential-workflow-farm-solution-only"></a>シーケンシャル ワークフロー (ファーム ソリューションのみ)
 A*シーケンシャル ワークフロー*一連の最後の手順を完了するまで、順番に実行されるビジネス ロジック ステップです。 シーケンシャル ワークフローは、リストやドキュメントなどの SharePoint アイテムが関係するプロセスを管理する目的で使用します。 サイト レベル (グローバル) のワークフローまたはリスト レベル (ローカル) のワークフローを作成できるほか、ワークフローを自動的に開始するか、手動で開始するかを選択することもできます。 このプロジェクト項目は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。[作成 SharePoint ワークフロー ソリューション](../sharepoint/creating-sharepoint-workflow-solutions.md)、 [SharePoint Server 2010 のワークフロー](http://go.microsoft.com/fwlink/?LinkId=260555)、および[新機能。ワークフローの改善](http://go.microsoft.com/fwlink/?LinkId=179418)します。  
  
### <a name="silverlight-web-part"></a>Silverlight web パーツ
 *Silverlight web パーツ*プロジェクト項目を有効にする web パーツの作成を Silverlight アプリケーションを表示する SharePoint の。 このプロジェクト項目ソリューションに追加するときは、新しい Silverlight アプリケーションを追加するか既存の Silverlight アプリケーションを後で参照するかを選択できます。 詳細については、次を参照してください。[の SharePoint web パーツを作成](../sharepoint/creating-web-parts-for-sharepoint.md)と[チュートリアル。SharePoint の OData を表示する Silverlight web パーツを作成する](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)します。  
  
### <a name="site-column"></a>サイト内の列
 A*サイト列*とも呼ばれる、*フィールド*、SharePoint プロジェクトに追加できる最も基本的な要素の 1 つです。 サイト列はデータの種類を表します。たとえば、連絡先一覧であれば、連絡先の電話番号、テキスト コメント、都市名などです。 詳細については、次を参照してください。 [for SharePoint のサイト列、コンテンツの種類、およびリストの作成](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)と[列](http://go.microsoft.com/fwlink/?LinkId=226840)します。  
  
### <a name="site-definition-farm-solution-only"></a>サイト定義 (ファーム ソリューションのみ)
 *サイト定義*プロジェクト項目には、次のファイルを含むサイト定義フォルダーが含まれています。  
  
- 既定の .aspx ページ。サイトの既定の Web ページとして使用されます。  
  
- *Onet.xml*サイトの構成要素を定義するファイル。  
  
- Webtemp xml ファイルに表示されるサイト定義構成を指定する、**テンプレートの選択**のセクション、**新しい SharePoint サイト**ページ。  
  
  サイト定義の追加後は、コードおよびファイルを追加して機能を導入できます。 このプロジェクト項目は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。 [for SharePoint のサイト定義を作成](../sharepoint/creating-site-definitions-for-sharepoint.md)と[サイト定義と構成](http://go.microsoft.com/fwlink/?LinkId=260554)します。  
  
### <a name="state-machine-workflow-farm-solution-only"></a>ステート マシン ワークフロー (ファーム ソリューションのみ)
 A*ステート マシン ワークフロー*ビジネス ロジックの状態、遷移、およびアクションのセットです。 ステート マシン ワークフローに含まれる各ステップは、順番に実行されるのではなく、アクションおよび状態によってトリガーされます。 シーケンシャル ワークフローと同様に、ステート マシン ワークフローは、リストやドキュメントなどの SharePoint アイテムに関連付けられます。 サイト レベル (グローバル) のワークフローまたはリスト レベル (ローカル) のワークフローを作成できることも、シーケンシャル ワークフローと同じです。 ワークフローを自動的に開始するか手動で開始するかを選択することもできます。 このプロジェクト項目は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。[作成 SharePoint ワークフロー ソリューション](../sharepoint/creating-sharepoint-workflow-solutions.md)、 [SharePoint Server 2010 のワークフロー](http://go.microsoft.com/fwlink/?LinkId=260555)、および[新機能。ワークフローの改善](http://go.microsoft.com/fwlink/?LinkId=179418)します。  
  
### <a name="user-control-farm-solution-only"></a>ユーザー コントロール (ファーム ソリューションのみ)
 A*ユーザー コントロール*、再利用可能なカスタム コントロールが他の ASP.NET コントロールや SharePoint コントロールを追加できます。 ユーザー コントロールは、SharePoint で実行されるアプリケーション ページと Web パーツに追加できます。 このプロジェクト項目は、ファーム ソリューションでのみ使用できます。 このプロジェクト項目はファーム ソリューションにしか追加できません。 詳細については、次を参照してください。 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成する](http://go.microsoft.com/fwlink/?LinkId=226841)します。  
  
### <a name="visual-web-part"></a>視覚的 web パーツ
 A*視覚的 web パーツ*プロジェクト アイテムが含まれて、 *Elements.xml*定義ファイルを**Web パーツ**項目、および**ユーザー コントロール**項目。 ドラッグするか、ユーザー コントロールの画面に、Visual Studio のツールボックスからコントロールをコピーして、視覚的 web パーツの外観をデザインできます。 詳細については、「[方法 :デザイナーを使用して、SharePoint web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)と[ビルディング ブロック。Web パーツ](http://go.microsoft.com/fwlink/?LinkId=179438)します。  
  
### <a name="web-part"></a>Web パーツ
 A *web パーツ*は特殊な種類の Web パーツ ページと呼ばれるページ内で実行されるサーバー側コントロールです。 これらは、SharePoint サイトに表示されるページのビルド ブロックです。 Web パーツ項目には、SharePoint サイト用の Web パーツをデザインするためのファイルが用意されています。 詳細については、「[方法 :SharePoint web パーツを作成](../sharepoint/how-to-create-a-sharepoint-web-part.md)と[ビルディング ブロック。Web パーツ](http://go.microsoft.com/fwlink/?LinkId=179438)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint 製品とテクノロジ](http://go.microsoft.com/fwlink/?LinkId=178818)  
