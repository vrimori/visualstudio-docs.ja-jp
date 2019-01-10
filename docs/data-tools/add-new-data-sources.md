---
title: 新しいデータ ソースの追加
ms.date: 11/21/2018
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
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: d203fc6c0ecb61310a31ae172fe68bcdf77f66a8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863853"
---
# <a name="add-new-data-sources"></a>新しいデータ ソースの追加

Visual Studio での .NET データ ツールのコンテキストでは、用語*データ ソース*データ ストアに接続してデータを .NET アプリケーションを使用できるようにする .NET オブジェクトを参照します。 Visual Studio のデザイナーにドラッグしてからデータベース オブジェクトを削除すると、フォームにデータをバインドする定型コードを生成するデータ ソースの出力を使用できる、**データソース**ウィンドウ。 この種類のデータ ソースを指定できます。

- いくつかの種類のデータベースに関連付けられている Entity Framework モデル内のクラス。

- いくつかの種類のデータベースに関連付けられているデータセットです。

- Windows Communication Foundation (WCF) のデータ サービス、または REST サービスなどのネットワーク サービスを表すクラス。

- SharePoint サービスを表すクラス。

- クラスまたはソリューション内のコレクション。

> [!NOTE]
> データ バインド機能を使用していない場合のデータセットや Entity Framework、LINQ to SQL、WCF では、SharePoint、"data source"の概念は適用されません。 SQLCommand オブジェクトを使用して、データベースに直接接続して、データベースと直接通信だけです。

作成してデータ ソースを使用して、編集、**データ ソース構成ウィザード**Windows フォームや Windows Presentation Foundation アプリケーションでします。 Entity Framework では、まず、エンティティ クラスを作成し、選択して、ウィザードを開始**プロジェクト** > **新しいデータ ソースの追加**(この記事の後半で詳しく説明します)。

![データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>[データ ソース] ウィンドウ

データ ソースを作成した後に表示されます、**データソース**ツール ウィンドウです。

> [!TIP]
> 開くには、**データソース**ウィンドウで、プロジェクトが開いているかどうかを確認し、キーを押します**Shift**+**Alt**+**D**選択または**ビュー** > **その他の Windows** > **データソース**します。

データ ソースをドラッグすることができます、**データソース**フォームのデザイン画面またはコントロールの上にウィンドウ。 これにより、データ ストアからデータを表示する定型コードを生成します。

次の図は、Windows フォームにドロップされたデータセットを示します。 選択した場合**F5**アプリケーションでは、基になるデータベースからデータがフォームのコントロールに表示されます。

![データ ソースのドラッグ操作](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>データベースまたはデータベース ファイルのデータ ソース

データセットやデータベースまたはデータベース ファイルのデータ ソースとして使用する Entity Framework モデルを作成できます。

### <a name="dataset"></a>データセット

データ ソースとしてのデータセットを作成するには、実行、**データ ソース構成ウィザード**を選択して**プロジェクト** > **新しいデータ ソースの追加**します。 選択、**データベース**データ ソース型、および新規または既存のデータベース接続、またはデータベース ファイルのいずれかを指定する指示に従います。

### <a name="entity-classes"></a>エンティティ クラス

データ ソースとして Entity Framework モデルを作成します。

1. 実行、 **Entity Data Model ウィザード**エンティティ クラスを作成します。 選択**プロジェクト** > **新しい項目の追加** > **ADO.NET Entity Data Model**します。

   ![新しい Entity Framework モデルのプロジェクト アイテム](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. モデルを生成するメソッドを選択します。

   ![エンティティ データ モデル ウィザード](../data-tools/media/raddata-entity-data-model-wizard.png)

1. データ ソースとしてモデルを追加します。 生成されるクラスが表示される、**データ ソース構成ウィザード**を選択すると、**オブジェクト**カテゴリ。

   ![エンティティ クラスとデータ ソース構成ウィザード](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>サービスのデータ ソース

サービスからのデータ ソースを作成するには、実行、**データ ソース構成ウィザード**を選択し、**サービス**データ ソースの種類。 これのショートカットに過ぎない、**サービス参照の追加**でプロジェクトを右クリックしてアクセスすることもできますこのダイアログ ボックスで、**ソリューション エクスプ ローラー**を選択すると**サービス参照の追加。**.

サービスからデータ ソースを作成すると、Visual Studio によりサービス参照がプロジェクトに追加されます。 Visual Studio には、サービスで返されるオブジェクトに対応するプロキシ オブジェクトも作成します。 たとえば、データセットを返すサービスは、プロジェクト内でデータセットとして表現され、特定の型を返すサービスは、プロジェクト内で、返される型として表現されます。

次の種類のサービスからデータ ソースを作成できます。

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Web サービス

    > [!NOTE]
    > 表示される項目、**データソース**ウィンドウは、サービスが返すデータに依存します。 サービスによっては、**データ ソース構成ウィザード**でバインドできるオブジェクトを作成するための十分な情報を提供しないものもあります。 たとえば、サービスは、型指定されていないデータセットを返す場合項目表示されません、**データ ソース**ウィンドウ、ウィザードを完了するとします。 これは、型指定されていないデータセットからはスキーマが提供されず、したがってウィザードでデータ ソースを作成するための十分な情報が得られないためです。

## <a name="data-source-for-an-object"></a>オブジェクトのデータ ソース

1 つ以上のパブリック プロパティを公開する任意のオブジェクトからデータ ソースを作成できます。それには、**データ ソース構成ウィザード**を実行し、データ ソースの種類として **[オブジェクト]** を選択します。 オブジェクトのすべてのパブリック プロパティは、**[データ ソース]** ウィンドウに表示されます。 Entity Framework を使用している、モデルを生成した場合は、これは、アプリケーションのデータ ソースであるエンティティ クラスを検索します。

**データ オブジェクトの選択** ページで、ツリー ビューにバインドするオブジェクトを検索するノードを展開します。 ツリー ビューには、ノード、プロジェクトおよびアセンブリやプロジェクトによって参照されている他のプロジェクトが含まれています。

アセンブリまたはツリー ビューで表示されていないプロジェクトでオブジェクトにバインドする場合は、クリックして**参照の追加**を使用して、 **Add Reference Dialog Box**アセンブリまたはプロジェクトへの参照を追加します。 参照を追加した後は、アセンブリまたはプロジェクトがツリー ビューに追加されます。

> [!NOTE]
> オブジェクトのツリー ビューに表示される前に、オブジェクトを含むプロジェクトをビルドする必要があります。

> [!NOTE]
> 実装するオブジェクトにドラッグ アンド ドロップのデータ バインディングをサポートするために、<xref:System.ComponentModel.ITypedList>または<xref:System.ComponentModel.IListSource>インターフェイスは、既定のコンス トラクターをいる必要があります。 それ以外の場合、Visual Studio は、データ ソース オブジェクトをインスタンス化できないし、デザイン サーフェイスに項目をドラッグすると、エラーが表示されます。

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint リストのデータ ソース

**データ ソース構成ウィザード**を実行し、データ ソースの種類として **[SharePoint]** を選択すると、SharePoint リストからデータ ソースを作成できます。 SharePoint は、サービスからデータ ソースの作成と同じでは SharePoint データ ソースを作成するために WCF Data Services でのデータを公開します。 **データ ソース構成ウィザード**で **[SharePoint]** 項目をクリックすると、**[サービス参照の追加]** ダイアログ ボックスが表示されます。このダイアログ ボックスで、SharePoint サーバーを指定することにより SharePoint データ サービスに接続します。 これには、SharePoint の SDK が必要です。

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)