---
title: "ビジネス データ接続モデルをデザイン |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
ms.assetid: 19cad8cf-8a82-4000-84cf-1e5aff54e5af
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 886522cacff9359b3516b9e09530bfb1c41acfe6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="designing-a-business-data-connectivity-model"></a>Business Data Connectivity モデルのデザイン
  モデル ファイルにエンティティとメソッドを追加することで、ビジネス データ接続 (BDC) サービスのモデルを開発できます。 エンティティは、データ フィールドのコレクションを表します。 たとえば、エンティティは、データベース内のテーブルを表すことができます。 メソッドは、追加、削除、またはエンティティによって表されるデータの更新などのタスクを実行します。 詳細については、次を参照してください。 [SharePoint にビジネス データを統合する](../sharepoint/integrating-business-data-into-sharepoint.md)です。  
  
## <a name="adding-entities"></a>エンティティの追加  
 ドラッグまたはコピーしてエンティティを追加することができます、**エンティティ**Visual Studio から**ツールボックス**BDC デザイナーにします。 詳細については、次を参照してください。[する方法: エンティティをモデルに追加](../sharepoint/how-to-add-an-entity-to-a-model.md)です。  
  
 クラスでは、エンティティのフィールドを定義します。 たとえば、という名前のフィールドを追加する場合があります`Address`を`Customer`クラスです。 プロジェクトに新しいクラスを追加するか、オブジェクト リレーショナル デザイナー (O/R デザイナー) などの他のツールを使用して作成された既存のクラスを使用します。 エンティティの名前とエンティティを表すクラスの名前に一致するありません。 クラスは、モデル内のメソッドを定義するときに、エンティティに関連します。  
  
## <a name="adding-methods"></a>メソッドの追加  
 BDC サービスは、ユーザーを表示、追加、更新、またはリストや、モデルに基づく Web パーツ内の情報を削除するときに、モデルのメソッドを呼び出します。 ユーザーが実行できる各タスクのモデルにメソッドを追加する必要があります。 5 つの基本的なメソッドの型のいずれかを選択してメソッドを作成、 **BDC メソッドの詳細**ウィンドウです。 次の表では、BDC モデルの 5 つの基本的な方法について説明します。  
  
|メソッド|説明|  
|------------|-----------------|  
|Finder|エンティティ インスタンスのコレクションを返します。 ユーザーがリストまたは Web パーツを開いたときに呼び出されます。 詳細については、次を参照してください。[する方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)です。|  
|SpecificFinder|特定のエンティティ インスタンスを返します。 ユーザーの一覧で、特定のアイテムの詳細を表示するときに呼び出されます。 詳細については、次を参照してください。[する方法: 特定の Finder メソッドを追加](../sharepoint/how-to-add-a-specific-finder-method.md)です。|  
|Creator|エンティティのデータ ソースに新しいデータを追加します。 ユーザーを選択すると呼び出されます、**新しい項目の**モデルに基づいているリストのリボンのボタンをクリックします。 詳細については、次を参照してください。[する方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)です。|  
|Updater|リストのデータを変更します。 ユーザー一覧の情報を更新するときに呼び出されます。 詳細については、次を参照してください。[する方法: Updater メソッドを追加](../sharepoint/how-to-add-an-updater-method.md)です。|  
|Deleter|データを削除します。 ユーザーの一覧から項目を削除するときに呼び出されます。 詳細については、次を参照してください。[する方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)です。|  
  
## <a name="defining-method-parameters"></a>メソッドのパラメーターを定義します。  
 メソッドを作成するときに、Visual Studio は、メソッドの型に適した入力呼び出し力パラメーターを追加します。 これらのパラメーターは、単なるプレース ホルダーです。 ほとんどの場合は、それらに渡すか、正しい種類のデータを返すようにパラメーターを変更する必要があります。 たとえば、Finder メソッドは、既定では、文字列を返します。 エンティティのコレクションを返すように Finder メソッドの戻り値パラメーターを変更するほとんどの場合は、します。 パラメーターの型記述子を変更することにより、ことを行うことができます。 型記述子とは、パラメーターのデータ型を記述する属性のコレクションです。 詳細については、次を参照してください。[する方法: パラメーターの型記述子を定義する](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)です。  
  
 Visual Studio では、モデル内のパラメーターの型記述子をコピーすることができます。 たとえば、という名前の型記述子を定義する場合があります`CustomerTD`の戻り値のパラメーターに、`GetCustomer`メソッドです。 コピーすることができます、`CustomerTD`入力記述子に、 **BDC エクスプ ローラー**の入力パラメーターには、その型記述子を貼り付けると、`CreateCustomer`メソッドです。 こうと、同じの型記述子を複数回定義する必要がなくなります。  
  
##  <a name="MethodInstances"></a>メソッド インスタンス  
 メソッドを作成するときに、Visual Studio は、既定のメソッドのインスタンスを追加します。 メソッドのインスタンスは、メソッド、およびパラメーターの既定値への参照です。 1 つのメソッドは、メソッドの複数のインスタンスを持つことができます。 各インスタンスは、既定値のセットとメソッドのシグネチャの組み合わせです。 詳細については、次を参照してください。[する方法: パラメーターの型記述子を定義する](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)です。  
  
 プロジェクトを実行するときに、SharePoint リストの上のドロップダウン リストでメソッドのインスタンスが表示されます。 ユーザーは、データを表示するメソッドのインスタンスを選択できます。  
  
 メソッドのインスタンスに既定値を追加するには、モデルの XML を直接変更があります。 詳細については、次を参照してください。 [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279)です。  
  
## <a name="adding-filter-descriptors"></a>フィルター記述子の追加  
 モデルのコンシューマーは、いくつかの条件に一致するエンティティのインスタンスを取得する必要があります。 この機能を有効にするには、メソッドにフィルター記述子を追加することができます。 フィルター記述子には、モデルのコンシューマーを実行する前に、値をメソッドに渡すことによって、メソッドの結果セットをフィルター処理が有効にします。 詳細については、次を参照してください。[する方法: フィルター パラメーターを追加して、外部システムからの操作を制限のインスタンスに](http://go.microsoft.com/fwlink/?LinkID=169267)です。  
  
 SharePoint では、フィルター値を指定するユーザーを有効にするいくつかの機能を提供します。 たとえば、ビジネス データ Web パーツは、フィルターのテキスト ボックスを提供します。 ユーザーは、テキスト ボックスに値を入力して一覧内のデータを制限できます。 メソッドにフィルター記述子を追加する方法の詳細については、次を参照してください。[する方法: Finder メソッドにフィルター記述子を追加](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)です。  
  
### <a name="filter-descriptor-properties"></a>フィルター記述子のプロパティ  
 値を設定する必要があります、**型記述子の関連付けられている**、**名前**、および**型**フィルター記述子のプロパティです。 その他のすべてのプロパティはオプションです。  
  
 **型記述子の関連付けられている**プロパティに関連する入力パラメーター、フィルター記述子。 ユーザーがフィルター値を提供するとき、BDC サービスでは、メソッドにその値を入力パラメーターを使用して渡します。  
  
 **型**プロパティを使用するフィルターのパターンを説明します。 SharePoint では、選択したフィルター パターンはユーザー インターフェイス (UI) 内に表示されるテキストに影響します。 たとえば、文字列比較子のフィルター パターン**と等しい**ビジネス データ Web パーツの上のコントロールとして表示されます。 各フィルター パターンの詳細については、次を参照してください。[型のフィルターでサポート、BDC](http://go.microsoft.com/fwlink/?LinkId=169287)です。  
  
 フィルター記述子のプロパティの詳細については、次を参照してください。 [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280)です。  
  
### <a name="providing-default-values"></a>既定値を指定します。  
 場合によっては、ユーザーはフィルター値を指定していない可能性があります。 メソッドのインスタンスに、既定値を追加するか、メソッドのコードで、既定値を設定して、既定値を指定できます。 メソッド インスタンスを既定値を追加する方法の詳細については、次を参照してください。 [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)です。 メソッドのコードの入力パラメーターの既定値を設定する方法の例は、次を参照してください。[する方法: Finder メソッドにフィルター記述子を追加](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)です。  
  
## <a name="validating-the-model"></a>モデルの検証  
 開発時に、モデルを検証できます。 Visual Studio では、期待どおりに動作してから、モデルを妨げる可能性のある問題を識別します。 Visual Studio でこれらの問題が表示される**エラー一覧**です。  
  
 モデルを検証するには、BDC デザイナーのショートカット メニューを開き、を選択して**検証**です。 モデル エラーが含まれている場合に表示されます、**エラー一覧**です。 カーソルは、エラーを含む、リストにエラーをダブルクリックしてコードをすばやく移動できます。 代わりに、一覧に f8 キーまたは shift キーを押しながら F8 キーを繰り返し前方または後方エラー間のステップを選択できます。  
  
 検証エラーは、何らかの方法で、モデルのルールに違反しているときに発生します。 たとえば場合、 **IsCollection**型記述子のプロパティに設定されて**true**が子の型記述子がないので、検証エラーが表示されます。 Visual Studio に表示される一部のエラーを理解する BDC モデルのルールを参照する必要があります**エラー一覧**です。 BDC モデルのルールに関する詳細については、次を参照してください。 [BDCMetadata スキーマ](http://go.microsoft.com/fwlink/?LinkID=169275)です。  
  
## <a name="debugging-the-solution-that-contains-the-model"></a>モデルを含むソリューションのデバッグ  
 Visual Studio でのすべてのコードをデバッグする場合と、コードをデバッグできます。 コードをデバッグするには、任意の場所、コードでブレークポイントを設定し、デバッガーを開始します。 Visual Studio では、SharePoint サイトが開きます。 SharePoint では、リストや、ビジネス データを使用する Web パーツを作成します。 次に、コードをステップすることができます。 SharePoint プロジェクトのデバッグの詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)です。  
  
 プロジェクトに追加するカスタム アセンブリのコードをデバッグすることもできます。 ただし、カスタム アセンブリ コードをデバッグするには、ソリューション パッケージにアセンブリを追加する必要があります。 詳細については、次を参照してください。[する方法: 追加およびその他のアセンブリを削除する](../sharepoint/how-to-add-and-remove-additional-assemblies.md)です。  
  
 カスタム アセンブリをプロジェクトに追加する方法の詳細については、次を参照してください。[する方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)です。  
  
### <a name="configuring-bdc-security"></a>BDC セキュリティを構成します。  
 ソリューションをデバッグする前に、SharePoint のセキュリティ設定を変更する必要があります。 これらの設定を変更するには、SharePoint 2010 中央管理の Web サイトにビジネス データ接続サービス アプリケーションを開きます。 **メタデータ ストアのアクセス許可を設定**ダイアログ ボックスで、ユーザー アカウントを追加し、次のオプションのいずれかを選択します。  
  
|タスク|オプション|  
|----------|------------|  
|BDC サービス モデルを展開します。|編集|  
|外部リストおよびを使用して Web パーツを作成するには、は、コンテンツは、モデルに (エンティティ) を入力します。|クライアントで選択可能|  
|作成するには、読み取り、更新、およびエンティティ データを削除します。|実行|  
  
 これらの設定の詳細については、次を参照してください。[ビジネス データ接続サービスの管理](http://go.microsoft.com/fwlink/?LinkID=178883)です。  
  
 個々 のモデルや外部のコンテンツの種類のセキュリティ アクセス許可を設定することもできます。 モデルのセキュリティのアクセス許可を設定する方法の詳細については、次を参照してください。 [BDC モデル管理](http://go.microsoft.com/fwlink/?LinkID=178884)です。 外部コンテンツ タイプのセキュリティのアクセス許可を設定する方法の詳細については、次を参照してください。[外部コンテンツ タイプを管理](http://go.microsoft.com/fwlink/?LinkID=178885)です。  
  
> [!NOTE]  
>  これらの設定を使用して、ローカル SharePoint サーバーでソリューションをデバッグします。 運用環境の SharePoint サーバーで BDC に関連するセキュリティ設定を構成する方法の詳細については、次を参照してください。 [Business Data Connectivity Services セキュリティ概要](http://go.microsoft.com/fwlink/?LinkID=178886)です。  
  
### <a name="retracting-models-that-become-corrupt"></a>破損したモデルの取り消し  
 初めて、デバッガーを起動する Visual Studio は、SharePoint にモデル全体を配置します。 時間ごとにその後は、Visual Studio は、展開の間で行った変更で SharePoint 内のモデルを更新します。  
  
 Visual Studio で sharepoint サイトからモデルを完全に取り消しを行うことがあります。 など、モデルが破壊される可能性があります。  SharePoint にモデルを再展開するには設定、**増分更新**するモデルのプロパティ**False**、し、デバッガーを起動します。 **増分更新**プロパティに表示されて、**プロパティ**ウィンドウでモデルを表すノードを選択すると、 **BDC エクスプ ローラー**です。 モデルの名前は、既定では、 **BdcModel1**です。  
  
### <a name="changing-identifier-names-of-entities-in-the-model"></a>モデル内のエンティティの識別子の名前を変更します。  
 モデルを配置した後に識別子の名前を変更する場合は、配置エラーが発生する可能性があります。 設定してこのエラーを解決することはできません、**増分更新**するモデルのプロパティ**False**です。 モデルを手動で取り消すし、もう一度ソリューションを展開し、必要があります。 詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)です。 設定してこのエラーを回避することができます、**増分更新**プロパティを**False**モデルを最初に展開する前にします。  
  
## <a name="locating-documentation-for-bdc-model-elements"></a>BDC モデル要素のマニュアルの入手  
 Visual Studio の各エンティティ モデルに XML 要素を追加するメソッド、またはその他の項目を作成することです。 要素の属性がプロパティとして表示、**プロパティ**ウィンドウです。 要素と、モデルを設計する際に Visual Studio がによって生成される属性については、次を参照してください。 [BDCMetadata スキーマ](http://go.microsoft.com/fwlink/?LinkID=169275)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)|BDC モデルを視覚的にデザインに使用できるツールについて説明します。|  
|[方法: モデルにエンティティを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)|外部コンテンツ タイプ、またはエンティティをモデルに追加する方法を示します。|  
|[方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)|ユーザー リストまたは Web パーツ内のエンティティの一覧を表示できるようにするメソッドを追加する方法を示します。|  
|[方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)|特定のエンティティの詳細を表示できるようにするメソッドを追加する方法を示します。|  
|[方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)|リストまたは Web パーツから直接データ ソースにレコードを追加できるようにするメソッドを追加する方法を示します。|  
|[方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)|一覧のユーザー インターフェイス (UI) または Web パーツでオプションを使用して、データ ソースからデータを削除できるようにするメソッドを追加する方法を示します。|  
|[方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)|ユーザーの一覧や Web パーツから直接データ ソースのデータ レコードを変更できるようにするメソッドを追加する方法を示します。|  
|[方法: メソッドにパラメーターを追加する](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Visual Studio でのメソッドの詳細 ウィンドウを使用して、メソッドに入力パラメーターと戻り値パラメーターを追加する方法を示します。|  
|[方法: パラメーターの型記述子を定義する](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|モデルのパラメーターのデータ型を定義する方法を示します。|  
|[方法: メソッド インスタンスを定義する](../sharepoint/how-to-define-a-method-instance.md)|BDC を実行するメソッドのインスタンスを作成する方法を示します。|  
|[方法: Finder メソッドにフィルター記述子を追加する](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Finder メソッドによって返されるインスタンスの数を制限するユーザーを有効にする方法を示します。|  
|[エンティティ間の関連付けの作成](../sharepoint/creating-an-association-between-entities.md)|モデル内のエンティティ間のリレーションシップを定義する方法について説明します。 ビジネス データ Web パーツ、外部リスト、およびカスタム アプリケーションは、ユーザー インターフェイス (UI) にそれらの関係を表示できます。|  
|[方法: エンティティ間の関連付けを作成します。](../sharepoint/how-to-create-an-association-between-entities.md)|モデル内のエンティティ間のリレーションシップを定義する方法を示します。|  
|[チュートリアル: ビジネス データを使用した SharePoint での外部リストの作成](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|作成し、SharePoint の外部リストで連絡先を表示するモデルをテストする方法を示す手順を説明します。|  
|[SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)|作成して、BDC サービスのモデルのデザインの概要を示します。|  
  
  