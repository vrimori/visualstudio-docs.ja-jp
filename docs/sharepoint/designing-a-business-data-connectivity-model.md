---
title: ビジネス データ接続モデルの設計 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97172f0b3a03d015c087a58077696ceff2b4369d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858384"
---
# <a name="design-a-business-data-connectivity-model"></a>ビジネス データ接続モデルを設計します。
  モデル ファイルへのエンティティとメソッドを追加することで、ビジネス データ接続 (BDC) サービスのモデルを開発できます。 エンティティには、データ フィールドのコレクションについて説明します。 たとえば、エンティティは、データベース内のテーブルを表すことができます。 メソッドは、追加、削除、またはエンティティによって表されるデータの更新などのタスクを実行します。 詳細については、次を参照してください。 [SharePoint ビジネス データを統合](../sharepoint/integrating-business-data-into-sharepoint.md)します。  
  
## <a name="add-entities"></a>エンティティを追加します。
 エンティティを追加するにはドラッグまたはコピーして、**エンティティ**Visual Studio から**ツールボックス**BDC デザイナーにします。 詳細については、「[方法 :エンティティ モデルを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)します。  
  
 クラスでは、エンティティのフィールドを定義します。 たとえば、という名前のフィールドを追加する場合があります`Address`を`Customer`クラス。 プロジェクトに新しいクラスを追加するか、オブジェクト リレーショナル デザイナー (O/R デザイナー) などの他のツールを使用して作成された既存のクラスを使用します。 エンティティの名前と、エンティティを表すクラスの名前は一致する必要はありません。 クラスは、モデル内のメソッドを定義するときに、エンティティに関連します。  
  
## <a name="add-methods"></a>メソッドを追加します。
 BDC サービスは、ユーザーを表示、追加、更新、またはリストや、モデルに基づく Web パーツで情報を削除するときに、モデルのメソッドを呼び出します。 メソッドは、タスクごとに、ユーザーが実行できるモデルに追加する必要があります。 メソッドの作成から 5 つの基本的なメソッドの型のいずれかを選択して、 **BDC メソッドの詳細**ウィンドウ。 次の表では、BDC モデルの 5 つの基本的な方法について説明します。  
  
|メソッド|説明|  
|------------|-----------------|  
|ファインダー|エンティティ インスタンスのコレクションを返します。 ユーザーがリストまたは Web パーツを開いたときに呼び出されます。 詳細については、「[方法 :Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)します。|  
|SpecificFinder|特定のエンティティ インスタンスを返します。 リスト内の特定の項目の詳細を表示するときに呼び出されます。 詳細については、「[方法 :特定の Finder メソッドを追加](../sharepoint/how-to-add-a-specific-finder-method.md)します。|  
|Creator|エンティティのデータ ソースに新しいデータを追加します。 ユーザーが選択すると呼び出されます、**新しい項目の**モデルに基づいているリストのリボンのボタンをクリックします。 詳細については、「[方法 :Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)します。|  
|Updater|一覧内のデータを変更します。 ユーザー一覧の情報を更新するときに呼び出されます。 詳細については、「[方法 :Updater メソッドを追加](../sharepoint/how-to-add-an-updater-method.md)します。|  
|Deleter|データを削除します。 ユーザーの一覧から項目を削除するときに呼び出されます。 詳細については、「[方法 :Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)します。|  
  
## <a name="define-method-parameters"></a>メソッドのパラメーターを定義します。
 メソッドを作成するときに、Visual Studio は、メソッドの種類に適切な入力と出力のパラメーターを追加します。 これらのパラメーターは、単なるプレース ホルダーです。 ほとんどの場合、それらで渡すか、正しい種類のデータを返すようにパラメーターを変更する必要があります。 たとえば、既定では、Finder メソッドは文字列を返します。 ほとんどの場合、エンティティのコレクションを返すように Finder メソッドの戻り値パラメーターを変更したいです。 パラメーターの型記述子を変更することによって実現できます。 型記述子は、パラメーターのデータ型を記述する属性のコレクションです。 詳細については、「[方法 :パラメーターの型記述子を定義](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)します。  
  
 Visual Studio では、モデルのパラメーターの型記述子をコピーすることができます。 たとえば、という名前の型記述子を定義する場合があります`CustomerTD`の戻り値パラメーターの`GetCustomer`メソッド。 コピーすることができます、`CustomerTD`入力記述子、 **BDC エクスプ ローラー**の入力パラメーターには、その型記述子を貼り付けると、`CreateCustomer`メソッド。 こうと、同じ型記述子を 2 回以上定義する必要がなくなります。  
  
## <a name="method-instances"></a>メソッド インスタンス
 メソッドを作成するときに、Visual Studio は、既定のメソッドのインスタンスを追加します。 メソッドのインスタンスは、メソッド、およびパラメーターの既定値への参照です。 1 つのメソッドは、メソッドの複数のインスタンスでことができます。 各インスタンスは、既定値のセットと、メソッド シグネチャの組み合わせです。 詳細については、「[方法 :パラメーターの型記述子を定義](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)します。  
  
 プロジェクトを実行するメソッドのインスタンスは、SharePoint リストの上のドロップダウン リストに表示されます。 ユーザーは、データを表示するメソッドのインスタンスを選択できます。  
  
 メソッドのインスタンスには、既定値を追加するには、モデルの XML を直接変更があります。 詳細については、次を参照してください。 [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279)します。  
  
## <a name="add-filter-descriptors"></a>フィルター記述子を追加します。
 モデルのコンシューマーは、いくつかの条件に一致するエンティティのインスタンスを取得する必要があります。 この機能を有効にするには、メソッドにフィルター記述子を追加できます。 フィルター記述子は、モデルのコンシューマーを実行する前に、メソッドに値を渡すことによってメソッドの結果セットをフィルター処理を有効にします。 詳細については、「[方法 :外部システムからインスタンスを制限する操作にフィルター パラメーターを追加](http://go.microsoft.com/fwlink/?LinkID=169267)します。  
  
 SharePoint では、フィルター値を指定するユーザーを有効にするいくつかの機能を提供します。 たとえば、ビジネス データ Web パーツは、フィルター テキスト ボックスを提供します。 ユーザーは、テキスト ボックスに値を入力して、リスト内のデータを制限できます。 メソッドにフィルター記述子を追加する方法の詳細については、次を参照してください。[方法。Finder メソッドにフィルター記述子を追加](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)します。  
  
### <a name="filter-descriptor-properties"></a>記述子のプロパティをフィルター処理します。
 値を設定する必要があります、**関連付けられた型記述子**、**名前**、および**型**フィルター記述子のプロパティ。 その他のすべてのプロパティは省略可能です。  
  
 **関連付けられた型記述子**プロパティに関連する入力パラメーター、フィルター記述子。 ユーザーがフィルター値と、ときに、BDC サービスは、入力パラメーターを使用してメソッドにその値を渡します。  
  
 **型**プロパティが使用するフィルターのパターンについて説明します。 SharePoint では、選択したフィルター パターンはユーザー インターフェイス (UI) で表示されるテキストに影響します。 たとえば、テキスト比較子のフィルター パターン**と等しい**ビジネス データ Web パーツの上のコントロールとして表示されます。 各フィルター パターンの詳細については、次を参照してください。[のフィルターでサポートされる型、BDC](http://go.microsoft.com/fwlink/?LinkId=169287)します。  
  
 フィルター記述子のプロパティの詳細については、次を参照してください。 [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280)します。  
  
### <a name="provide-default-values"></a>既定値を提供します。
 場合によっては、ユーザーはフィルター値を指定していない可能性があります。 メソッドのインスタンスに既定値を追加するか、メソッドのコードで、既定値を設定して、既定値を行うことができます。 メソッド インスタンスを既定値を追加する方法の詳細については、次を参照してください。 [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)します。 メソッドのコードで、入力パラメーターの既定値を設定する方法の例は、次を参照してください。[方法。Finder メソッドにフィルター記述子を追加](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)します。  
  
## <a name="validate-the-model"></a>モデルを検証します。
 開発中に、モデルを検証できます。 Visual Studio は、想定どおりに動作してから、モデルを妨げる可能性のある問題を特定します。 Visual Studio でこれらの問題が表示される**エラー一覧**します。  
  
 モデルを検証するには、BDC デザイナーのショートカット メニューを開き、して**検証**です。 表示されるモデルにエラーが含まれている場合、**エラー一覧**します。 リストにエラーをダブルクリックしてエラーが発生したコードにカーソルをすばやく移動できます。 代わりに、選択することができます、 **F8**または**Shift**+**F8**前方または後方の一覧でエラーの手順を繰り返しキー。  
  
 検証エラーは、何らかの方法でモデルのルールに違反しているときに発生します。 たとえば場合、 **IsCollection**型記述子のプロパティに設定されて**true**が子の型記述子がないので、検証エラーが表示されます。 Visual Studio に表示されるいくつかのエラーを理解する BDC モデルのルールを参照する必要があります**エラー一覧**します。 BDC モデルのルールの詳細については、次を参照してください。 [BDCMetadata スキーマ](http://go.microsoft.com/fwlink/?LinkID=169275)します。  
  
## <a name="debug-the-solution-that-contains-the-model"></a>モデルを含むソリューションをデバッグします。
 Visual Studio 内のコードをデバッグする場合と、コードをデバッグすることができます。 コードをデバッグするには、任意の場所、コードにブレークポイントを設定し、デバッガーを起動します。 Visual Studio では、SharePoint サイトを開きます。 SharePoint では、リストや、ビジネス データを使用する Web パーツを作成します。 次に、ステップ、コード実行することができます。 SharePoint プロジェクトのデバッグの詳細については、次を参照してください。[のトラブルシューティングを行う SharePoint ソリューション](../sharepoint/troubleshooting-sharepoint-solutions.md)します。  
  
 プロジェクトに追加するカスタム アセンブリのコードをデバッグすることもできます。 ただし、カスタム アセンブリ内のコードをデバッグするには、ソリューション パッケージにアセンブリを追加する必要があります。 詳細については、「[方法 :追加およびその他のアセンブリを削除](../sharepoint/how-to-add-and-remove-additional-assemblies.md)します。  
  
 カスタム アセンブリをプロジェクトに追加する方法の詳細については、次を参照してください。[方法。BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)します。  
  
### <a name="configure-bdc-security"></a>BDC のセキュリティを構成します。
 ソリューションをデバッグする前に、SharePoint のセキュリティ設定を変更する必要があります。 これらの設定を変更するには、ビジネス データ接続サービス アプリケーションで SharePoint 2010 サーバーの全体管理 Web サイトを開きます。 **メタデータ ストアのアクセス許可を設定** ダイアログ ボックスでは、ユーザー アカウントを追加し、次のオプションのいずれかを選択します。  
  
|タスク|オプション|  
|----------|------------|  
|BDC サービス モデルを展開できます。|編集|  
|外部リストとを使用して Web パーツを作成するには、コンテンツ タイプで、モデル (エンティティ)。|クライアントで選択可能|  
|作成するには、読み取り、更新、およびエンティティ データを削除します。|実行|  
  
 これらの設定の詳細については、次を参照してください。[ビジネス データ接続サービス管理](http://go.microsoft.com/fwlink/?LinkID=178883)します。  
  
 個々 のモデルまたは外部コンテンツ タイプのセキュリティ アクセス許可を設定することもできます。 モデルのセキュリティ アクセス許可を設定する方法の詳細については、次を参照してください。 [BDC モデル管理](http://go.microsoft.com/fwlink/?LinkID=178884)します。 外部コンテンツ タイプのセキュリティ アクセス許可を設定する方法の詳細については、次を参照してください。[外部コンテンツ タイプを管理](http://go.microsoft.com/fwlink/?LinkID=178885)します。  
  
> [!NOTE]  
>  これらの設定を使用して、ローカル SharePoint サーバーでのソリューションをデバッグします。 実稼働 SharePoint サーバーで BDC に関連するセキュリティ設定を構成する方法の詳細については、次を参照してください。 [Business Data Connectivity Services セキュリティの概要](http://go.microsoft.com/fwlink/?LinkID=178886)します。  
  
### <a name="retract-models-that-become-corrupt"></a>破損したモデルを取り消し
 最初に、デバッガーを起動する Visual Studio では、SharePoint にモデル全体がデプロイされます。 毎回その後、Visual Studio 展開の間で行った変更を SharePoint でモデルを更新します。  
  
 Visual Studio を SharePoint からモデルを完全に取り消す必要がある場合がある可能性があります。 たとえば、モデルが壊れて可能性があります。  SharePoint にモデルを再デプロイするには設定、**増分更新**にモデルのプロパティ**False**、し、デバッガーを起動します。 **増分更新**プロパティに表示されます、**プロパティ**ウィンドウ内のモデルを表すノードを選択すると、 **BDC エクスプ ローラー**します。 モデルの名前は、既定では、 **BdcModel1**します。  
  
### <a name="change-identifier-names-of-entities-in-the-model"></a>モデル内のエンティティの識別子の名前を変更します。
 モデルは、デプロイ後に識別子の名前を変更する場合は、配置エラーが発生する可能性があります。 設定してこのエラーを解決することはできません、**増分更新**にモデルのプロパティ**False**します。 モデルを手動で取り消すし、もう一度ソリューションをデプロイする必要があります。 詳細については、次を参照してください。[のトラブルシューティングを行う SharePoint ソリューション](../sharepoint/troubleshooting-sharepoint-solutions.md)します。 設定してこのエラーを回避することができます、**増分更新**プロパティを**False**最初に、モデルをデプロイする前にします。  
  
## <a name="locate-documentation-for-bdc-model-elements"></a>BDC モデル要素のドキュメントを見つける
 Visual Studio では、エンティティごとに、モデルに XML 要素を追加メソッド、またはその他の項目を作成します。 要素の属性がプロパティとして表示されます、**プロパティ**ウィンドウ。 要素と属性、モデルを設計する際に Visual Studio が生成する方法については、次を参照してください。 [BDCMetadata スキーマ](http://go.microsoft.com/fwlink/?LinkID=169275)します。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)|視覚的に、bdc モデルを設計するために使用できるツールについて説明します。|  
|[方法: エンティティ モデルを追加します。](../sharepoint/how-to-add-an-entity-to-a-model.md)|外部コンテンツの種類、または、エンティティ モデルを追加する方法を示します。|  
|[方法: Finder メソッドを追加します。](../sharepoint/how-to-add-a-finder-method.md)|ユーザー一覧や Web パーツでエンティティの一覧を表示できるようにするメソッドを追加する方法を示します。|  
|[方法: 特定の Finder メソッドを追加します。](../sharepoint/how-to-add-a-specific-finder-method.md)|ユーザーが特定のエンティティの詳細を表示できるようにするメソッドを追加する方法を示します。|  
|[方法: Creator メソッドを追加します。](../sharepoint/how-to-add-a-creator-method.md)|メソッドにより、リストや Web パーツから直接データ ソースにレコードを追加するユーザーを追加する方法を示します。|  
|[方法: Deleter メソッドを追加します。](../sharepoint/how-to-add-a-deleter-method.md)|メソッドにより、リストのユーザー インターフェイス (UI) または Web パーツでオプションを使用してデータ ソースからデータを削除するユーザーを追加する方法を示します。|  
|[方法: Updater メソッドを追加します。](../sharepoint/how-to-add-an-updater-method.md)|ユーザー一覧や Web パーツから直接データ ソース内のデータ レコードを変更できるようにするメソッドを追加する方法を示します。|  
|[方法: メソッドにパラメーターを追加します。](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Visual Studio でメソッドの詳細 ウィンドウを使用して、メソッドに入力パラメーターと戻り値パラメーターを追加する方法を示します。|  
|[方法: パラメーターの型記述子を定義します。](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|モデルのパラメーターのデータ型を定義する方法を示します。|  
|[方法: メソッド インスタンスを定義します。](../sharepoint/how-to-define-a-method-instance.md)|BDC を実行するメソッドのインスタンスを作成する方法を示します。|  
|[方法: Finder メソッドにフィルター記述子を追加します。](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Finder メソッドによって返されるインスタンスの数を制限するユーザーを有効にする方法を示します。|  
|[エンティティ間の関連付けの作成](../sharepoint/creating-an-association-between-entities.md)|モデルのエンティティ間のリレーションシップを定義する方法について説明します。 ビジネス データ Web パーツ、外部リスト、およびカスタム アプリケーションは、ユーザー インターフェイス (UI) でこれらのデータ リレーションシップを表示できます。|  
|[方法: エンティティ間のアソシエーションを作成します。](../sharepoint/how-to-create-an-association-between-entities.md)|モデルのエンティティ間のリレーションシップを定義する方法を示します。|  
|[チュートリアル: ビジネス データを使用して sharepoint の外部リストを作成します。](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|作成して、SharePoint の外部リストで連絡先を表示するモデルをテストする方法を説明する手順について説明します。|  
|[SharePoint ビジネス データを統合します。](../sharepoint/integrating-business-data-into-sharepoint.md)|作成して、BDC サービスのモデルのデザインの概要を示します。|  
