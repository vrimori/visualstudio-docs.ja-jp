---
title: 新しいデータ ソースを追加します。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: efcc167ba42469aa8e32198161612db7521d22ba
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="add-new-data-sources"></a>新しいデータ ソースを追加します。
Visual Studio での .NET data tools のコンテキストで用語*データ ソース*データ ストアに接続し、.NET アプリケーションにデータを公開する .NET オブジェクトを参照します。 Visual Studio のデザイナーにドラッグしてから、データベース オブジェクトをドロップすると、フォームにデータをバインドする定型コードを生成するデータ ソースの出力を使用できる、**データソース**ウィンドウです。 この種類のデータ ソースを指定できます。

-   いくつかの種類のデータベースに関連付けられている Entity Framework モデル内のクラスです。

-   いくつかの種類のデータベースに関連付けられているデータセットです。

-   Windows Communication Foundation (WCF) データ サービスまたは REST サービスなどのネットワーク サービスを表すクラス。

-   SharePoint サービスを表すクラスです。

-   クラスまたはソリューション内のコレクション。

> [!NOTE]
>  データ バインディング機能を使用していないデータセットや Entity Framework、LINQ to SQL、WCF、SharePoint、"data source"の概念は適用されません。 SQLCommand オブジェクトを使用して、データベースに直接接続して、データベースと直接通信だけです。

 作成しを使用してデータ ソースの編集、**データ ソース構成ウィザード**Windows フォームや Windows Presentation Foundation アプリケーションでします。 Entity Framework では、まず、エンティティ クラスを作成し、 を選択して、ウィザードを開始して**プロジェクト** > **新しいデータ ソースの追加**(この記事の後半で詳しく説明します)。

 ![データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png "データ ソース構成ウィザード")

 データ ソースを作成するに表示され、**データソース**ツール ウィンドウ (Shift + Alt + D または**ビュー** > **その他のウィンドウ** >  **データソース**)。 データ ソースをドラッグすることができます、**データソース**ウィンドウ、フォームのデザイン サーフェイスまたはコントロールからにします。 これにより、定型的なコードを生成する-ユーザーにデータ ストアで生成されたデータを表示するコードです。 次の図は、Windows フォームからドロップするデータセットを示します。 アプリケーションで f5 キーを選択した場合、データベースのデータを基になると、フォームのコントロールに表示されます。

 ![データ ソースはドラッグ操作](../data-tools/media/raddata-data-source-drag-operation.png "raddata データ ソースはドラッグ操作")

## <a name="data-source-for-a-database-or-a-database-file"></a>データベースまたはデータベース ファイルのデータ ソース

### <a name="dataset"></a>データセット
 データ ソースとしてデータセットを作成するには、実行、**データ ソース構成ウィザード**(**プロジェクト** > **新しいデータ ソースの追加**) を選択し、 **データベース**データ ソースの種類。 指示に従って、新規または既存のデータベース接続、またはデータベース ファイルを指定します。

### <a name="entity-classes"></a>エンティティ クラス
 データ ソースとして Entity Framework モデルを作成するには、最初に実行、 **Entity Data Model ウィザード**エンティティ クラスを作成する (**プロジェクト** > **新しい項目の追加** >  **ADO.NET Entity Data Model**)。

 ![新しいモデル プロジェクト項目の Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata Entity Framework の新しいモデル プロジェクト項目")

 モデルを生成するメソッドを選択します。

 ![Entity Data Model ウィザード](../data-tools/media/raddata-entity-data-model-wizard.png "raddata Entity Data Model ウィザード")

 データ ソースとしてモデルを追加します。 生成されたクラスが表示されます、**データ ソース構成ウィザード**を選択すると、**オブジェクト**カテゴリ。

 ![エンティティ クラスとデータ ソース構成ウィザード](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata エンティティ クラスとデータ ソース構成ウィザード")

## <a name="data-source-for-a-service"></a>サービスのデータ ソース
 サービスからデータ ソースを作成するには、実行、**データ ソース構成ウィザード**を選択し、**サービス**データ ソースの種類。 これへのショートカットを実際には、**サービス参照の追加** ダイアログ ボックスで、プロジェクトを右クリックしてアクセスすることもできます**ソリューション エクスプ ローラー**を選択すると**サービス参照の追加**。

 サービスからデータ ソースを作成すると、Visual Studio によりサービス参照がプロジェクトに追加されます。 Visual Studio では、サービスで返されるオブジェクトに対応するプロキシ オブジェクトも作成します。 たとえば、データセットを返すサービスは、プロジェクト内でデータセットとして表現され、特定の型を返すサービスは、プロジェクト内で、返される型として表現されます。

 次の種類のサービスからデータ ソースを作成できます。

-   WCF Data Services。 詳細については、次を参照してください。[概要](/dotnet/framework/data/wcf/wcf-data-services-overview)です。

-   WCF サービス。 詳細については、次を参照してください。 [Windows Communication Foundation サービスと Visual Studio での WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)です。

-   Web サービス

    > [!NOTE]
    >  表示される項目、**データソース**ウィンドウは、サービスから返されるデータに依存します。 一部のサービス可能性がありますのに十分な情報を提供していない、**データ ソース構成ウィザード**バインド可能なオブジェクトを作成します。 などの場合は、サービスでは、型指定されていないデータセットを返します、アイテムにはありません、**データソース**ウィンドウ、ウィザードを完了するとします。 これは、型指定されていないデータセットからはスキーマが提供されず、したがってウィザードでデータ ソースを作成するための十分な情報が得られないためです。

## <a name="data-source-for-an-object"></a>オブジェクトのデータ ソース
 実行して、1 つまたは複数のパブリック プロパティを公開する任意のオブジェクトからデータ ソースを作成することができます、**データ ソース構成ウィザード**を選択し、**オブジェクト**データ ソースの種類。 オブジェクトのすべてのパブリック プロパティが表示されます、**データソース**ウィンドウです。   Entity Framework を使用しているモデルを生成していて、これは、アプリケーションのデータ ソースとなるエンティティ クラスを検索します。

 **データ オブジェクトの選択** ページで、ツリー ビューにバインドするオブジェクトを特定のノードを展開します。 ツリー ビューには、プロジェクトおよびアセンブリとプロジェクトによって参照されている他のプロジェクトのノードが含まれています。

 アセンブリまたはツリー ビューで表示されていないプロジェクト内のオブジェクトにバインドする場合は、クリックして**参照の追加**を使用して、**参照の追加 ダイアログ ボックス**アセンブリまたはプロジェクトへの参照を追加します。 参照を追加した後、アセンブリまたはプロジェクトがツリー ビューに追加されます。

> [!NOTE]
>  オブジェクトのツリー ビューに表示される前に、オブジェクトを含むプロジェクトをビルドする必要があります。

> [!NOTE]
>  実装するオブジェクトにドラッグ アンド ドロップのデータ バインディングをサポートするために、<xref:System.ComponentModel.ITypedList>または<xref:System.ComponentModel.IListSource>インターフェイスは、既定のコンス トラクターを持つ必要があります。 それ以外の場合、Visual Studio は、データ ソース オブジェクトをインスタンス化できませんし、デザイン サーフェイスに項目をドラッグするときにエラーが表示されます。

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint リストのデータ ソース
 実行して、SharePoint リストから、データ ソースを作成することができます、**データ ソース構成ウィザード**を選択して、 **SharePoint**データ ソースの種類。 SharePoint を使用してデータを公開する[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]では、サービスからデータ ソースの作成と同じ SharePoint データ ソースを作成するため、します。 選択すると、 **SharePoint**内の項目、**データ ソース構成ウィザード**開きます、**サービス参照の追加**ダイアログ ボックスで、SharePoint データ サービスに接続します。SharePoint サーバーをポイントします。  これには、SharePoint SDK が必要です。

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)