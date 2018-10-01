---
title: 新しいデータ ソースの追加 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb629119655327c7608025d66bb5e42d857d039d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537430"
---
# <a name="add-new-data-sources"></a>新しいデータ ソースを追加します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[新しいデータ ソースの追加](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources)します。  
  
  
Visual Studio での .NET データ ツールのコンテキストでは、用語*データ ソース*データ ストアに接続し、.NET アプリケーションにデータを公開する .NET オブジェクトを参照します。 Visual Studio のデザイナーにドラッグしてからデータベース オブジェクトを削除すると、フォームにデータをバインドする定型コードを生成するデータ ソースの出力を使用できる、**データソース**ウィンドウ。 この種類のデータ ソースを指定できます。  
  
-   いくつかの種類のデータベースに関連付けられている Entity Framework モデル内のクラス。  
  
-   いくつかの種類のデータベースに関連付けられているデータセットです。  
  
-   Windows Communication Foundation (WCF) のデータ サービス、または REST サービスなどのネットワーク サービスを表すクラス。  
  
-   SharePoint サービスを表すクラス。  
  
-   クラスまたはソリューション内のコレクション。  
  
> [!NOTE]
>  データ バインド機能を使用していない場合のデータセットや Entity Framework、LINQ to SQL、WCF では、SharePoint、"data source"の概念は適用されません。 SQLCommand オブジェクトを使用して、データベースに直接接続して、データベースと直接通信だけです。  
  
 作成してデータ ソースを使用して、編集、**データ ソース構成ウィザード**Windows フォームや Windows Presentation Foundation アプリケーションでします。 Entity Framework では、まず、エンティティ クラスを作成し、選択して、ウィザードを開始**プロジェクト** > **新しいデータ ソースの追加**(この記事の後半で詳しく説明します)。  
  
 ![データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png "データ ソース構成ウィザード")  
  
 データ ソースを作成した後に表示されます、**データソース**ツール ウィンドウ (Shift + Alt + D または**ビュー** > **その他の Windows**  >  **データソース**)。 データ ソースをドラッグすることができます、**データソース**フォームのデザイン画面またはコントロールの上にウィンドウ。 これにより、定型コードを生成する、ユーザーにデータ ストアで生成されたデータを表示するコード。 次の図は、Windows フォームにドロップされたデータセットを示します。 アプリケーションで f5 キーを選択した場合、基になるデータベースからのデータは、フォームのコントロールに表示されます。  
  
 ![データ ソースはドラッグ操作](../data-tools/media/raddata-data-source-drag-operation.png "raddata データ ソースはドラッグ操作")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>データベースまたはデータベース ファイルのデータ ソース  
  
### <a name="dataset"></a>データセット  
 データ ソースとしてのデータセットを作成するには、実行、**データ ソース構成ウィザード**(**プロジェクト** > **新しいデータの追加**ソース) を選択し、 **データベース**データ ソースの種類。 指示に従って、新しいまたは既存のデータベース接続、またはデータベース ファイルを指定します。  
  
### <a name="entity-classes"></a>エンティティ クラス  
 データ ソースとして、Entity Framework モデルを作成して最初に実行、 **Entity Data Model ウィザード**エンティティ クラスを作成する (**プロジェクト** > **新しい項目の追加** >  **ADO.NET Entity Data Model**)。  
  
 ![新しい Entity Framework モデルのプロジェクト アイテム](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata 新しい Entity Framework モデルのプロジェクト アイテム")  
  
 モデルを生成するメソッドを選択します。  
  
 ![Entity Data Model ウィザード](../data-tools/media/raddata-entity-data-model-wizard.png "raddata Entity Data Model ウィザード")  
  
 データ ソースとしてモデルを追加します。 生成されたクラスが表示される、**データ ソース構成ウィザード**を選択すると、**オブジェクト**カテゴリ。  
  
 ![エンティティ クラスとデータ ソース構成ウィザード](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata エンティティ クラスとデータ ソース構成ウィザード")  
  
## <a name="data-source-for-a-service"></a>サービスのデータ ソース  
 サービスからのデータ ソースを作成するには、実行、**データ ソース構成ウィザード**を選択し、**サービス**データ ソースの種類。 これへのショートカットを実際には、**サービス参照の追加** ダイアログ ボックスで、プロジェクトを右クリックしてアクセスすることもできます**ソリューション エクスプ ローラー**を選択すると**サービス参照の追加**。  
  
 サービスからデータ ソースを作成すると、Visual Studio によりサービス参照がプロジェクトに追加されます。 Visual Studio には、サービスで返されるオブジェクトに対応するプロキシ オブジェクトも作成します。 たとえば、データセットを返すサービスは、プロジェクト内でデータセットとして表現され、特定の型を返すサービスは、プロジェクト内で、返される型として表現されます。  
  
 次の種類のサービスからデータ ソースを作成できます。  
  
-   WCF Data Services。 詳細については、次を参照してください。[概要](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)します。  
  
-   WCF data services。 詳細については、次を参照してください。 [Windows Communication Foundation サービスと Visual Studio での WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)します。  
  
-   Web サービス  
  
    > [!NOTE]
    >  表示される項目、**データソース**ウィンドウは、サービスが返すデータに依存します。 一部のサービスがのに十分な情報を提供していない、**データ ソース構成ウィザード**バインド可能なオブジェクトを作成します。 などの場合は、サービスは、型指定されていないデータセットを返します、項目は表示されません、**データソース**ウィンドウ、ウィザードを完了するとします。 これは、型指定されていないデータセットからはスキーマが提供されず、したがってウィザードでデータ ソースを作成するための十分な情報が得られないためです。  
  
## <a name="data-source-for-an-object"></a>オブジェクトのデータ ソース  
 実行して 1 つまたは複数のパブリック プロパティを公開する任意のオブジェクトからデータ ソースを作成することができます、**データ ソース構成ウィザード**選択し、**オブジェクト**データ ソースの種類。 オブジェクトのすべてのパブリック プロパティが表示されます、**データソース**ウィンドウ。   Entity Framework を使用している、モデルを生成した場合は、これは、アプリケーションのデータ ソースとなるエンティティ クラスを検索します。  
  
 **データ オブジェクトの選択** ページで、ツリー ビューにバインドするオブジェクトを検索するノードを展開します。 ツリー ビューには、ノード、プロジェクトおよびアセンブリやプロジェクトによって参照されている他のプロジェクトが含まれています。  
  
 アセンブリまたはツリー ビューで表示されていないプロジェクトでオブジェクトにバインドする場合は、クリックして**参照の追加**を使用して、 **Add Reference Dialog Box**アセンブリまたはプロジェクトへの参照を追加します。 参照を追加した後は、アセンブリまたはプロジェクトがツリー ビューに追加されます。  
  
> [!NOTE]
>  オブジェクトのツリー ビューに表示される前に、オブジェクトを含むプロジェクトをビルドする必要があります。  
  
> [!NOTE]
>  実装するオブジェクトにドラッグ アンド ドロップのデータ バインディングをサポートするために、<xref:System.ComponentModel.ITypedList>または<xref:System.ComponentModel.IListSource>インターフェイスは、既定のコンス トラクターをいる必要があります。 それ以外の場合、Visual Studio は、データ ソース オブジェクトをインスタンス化できないし、デザイン サーフェイスに項目をドラッグするときにエラーが表示されます。  
  
## <a name="data-source-for-a-sharepoint-list"></a>SharePoint リストのデータ ソース  
 SharePoint リストからを実行してデータ ソースを作成することができます、**データ ソース構成ウィザード**を選択して、 **SharePoint**データ ソースの種類。 SharePoint を使用してデータを公開する[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]ので、サービスからデータ ソースの作成と同じでは、SharePoint データ ソースを作成します。 選択すると、 **SharePoint**内の項目、**データ ソース構成ウィザード**開きます、**サービス参照の追加** ダイアログ ボックスで、SharePoint データ サービスに接続します。SharePoint サーバーをポイントします。  これには、SharePoint の SDK が必要です。  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)

