---
title: データ アクセスおよびツール
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 9a13efa2335cd0721b71dd61e270e5331d78dede
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936387"
---
# <a name="access-data-in-visual-studio"></a>Visual Studio でのデータへのアクセス

Visual Studio では、事実上すべてのデータベース製品またはサービスで、任意の場所の形式でデータに接続するアプリケーションを作成することができます: ローカル コンピューターのローカル エリア ネットワーク、またはパブリック、プライベート、およびハイブリッド クラウドで。

JavaScript、Python、PHP、Ruby、または C++ でのアプリケーションでのデータに接続するライブラリを取得し、コードの記述によって、何も行うようにします。 .NET アプリケーションでは、Visual Studio には、データ ソースの探索、格納、メモリ内のデータを操作し、ユーザー インターフェイスにデータをバインドしてオブジェクト モデルの作成を使用できるツールが用意されています。 Microsoft Azure は、Azure Storage に接続するため、.NET、Java、Node.js、PHP、Python、Ruby、およびモバイル アプリ、および Visual Studio のツールの Sdk を提供します。

次の表は、Visual Studio から使用できる多くのデータベースとストレージ システムのほんの一部を示します。 [Microsoft Azure](https://azure.microsoft.com/)サービス/データはすべてのプロビジョニングと、基になるデータ ストアの管理を含むデータ サービス。 **Azure 開発**ワークロード[Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) Visual Studio から直接 Azure データ ストアを操作することができます。

![Azure 開発ワークロード](media/azure-development-workload.png)

製品の大半の他の SQL および NoSQL データベースは、ここに記載されているローカル コンピューターで、ローカル ネットワーク、または Microsoft Azure で仮想マシンでホストできます。 Microsoft Azure の仮想マシンでデータベースをホストしている場合は、データベース自体を管理する責任を負いますできました。

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- ストレージ (blob、テーブル、キュー、ファイル)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- その他

**SQL**

- SQL Server 2005-2016 (Express、LocalDB を含む)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- その他

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB |
- RavenDB
- VelocityDB
- その他

多くのデータベース ベンダーやサード パーティは、NuGet パッケージによって Visual Studio の統合をサポートします。 Nuget.org または Visual Studio で NuGet パッケージ マネージャーを通じて、オファリングを調べることができます (**ツール** > **NuGet パッケージ マネージャー** > **NuGet の管理ソリューションのパッケージの**)。 他のデータベース製品は、拡張機能として、Visual Studio と統合します。 移動して、Visual Studio Marketplace でのこれらの製品を参照する**ツール**、**拡張機能と更新**し選択**オンライン**の左側のウィンドウで、ダイアログ ボックス。 詳細については、次を参照してください。 [for Visual Studio の互換性のあるデータベース システム](../data-tools/installing-database-systems-tools-and-samples.md)します。

> [!NOTE]
> SQL Server 2005 の延長サポートは 2016 年 4 月 12 日に終了しました。 データ ツールの Visual Studio 2015 以降では引き続きこの日付より後の SQL Server 2005 で機能する保証はありません。 詳細については、次を参照してください。、 [for SQL Server 2005 サポート終了のお知らせ](https://www.microsoft.com/sql-server/sql-server-2005)します。

## <a name="net-languages"></a>.NET 言語

.NET Core で含む、すべての .NET データ アクセスは、ADO.NET、任意の種類のデータ ソース、リレーショナルと非リレーショナルの両方にアクセスするためのインターフェイスを定義する一連のクラスに基づきます。 Visual Studio がいくつかのツールと、データベースに接続するための ADO.NET を使用するデザイナーがデータを操作およびユーザーにデータを表示します。 このセクションのドキュメントでは、これらのツールを使用する方法について説明します。 コマンドの ADO.NET オブジェクトに対して直接プログラムすることもできます。 ADO.NET の Api を直接呼び出すことの詳細については、次を参照してください。 [ADO.NET](/dotnet/framework/data/adonet/index)します。

データ アクセスのドキュメントが ASP.NET に関連する、次を参照してください。[データを扱う](https://www.asp.net/web-forms/overview/presenting-and-managing-data)ASP.NET サイト。 ASP.NET MVC で Entity Framework の使用に関するチュートリアルについては、次を参照してください。 [Entity Framework 6 Code First MVC 5 の使用の概要](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)します。

C# または Visual Basic でのユニバーサル Windows プラットフォーム (UWP) アプリでは、Microsoft Azure SDK for .NET を使用して、Azure Storage と他の Azure サービスにアクセスします。 Windows.Web.HttpClient クラスは、任意の RESTful サービスとの通信を使用できます。 詳細については、次を参照してください。 [Windows.Web.Http を使用して HTTP サーバーに接続する方法](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx)します。

ローカル コンピューター上のデータ ストレージ、アプリと同じプロセスで実行される、SQLite を使用することをお勧めします。 オブジェクト リレーショナル マッピング (ORM) 層が必要な場合は、Entity Framework を使用することができます。 詳細については、次を参照してください。[データ アクセス](/windows/uwp/data-access/index)、Windows デベロッパー センターでします。

Azure サービスに接続する場合は、最新バージョンをダウンロードすることを確認する[Azure SDK tools](https://azure.microsoft.com/downloads/)します。

### <a name="data-providers"></a>データ プロバイダー

ADO.NET で使用できるようにするデータベースの場合、ユーザー設定が必要*ADO.NET データ プロバイダー*またはそれ以外の場合、ODBC または OLE DB インターフェイスを公開する必要があります。 Microsoft が提供、 [ADO.NET データ プロバイダーの一覧](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview)ODBC および OLE DB プロバイダーと、SQL Server の製品です。

### <a name="data-modeling"></a>データ モデリング

.NET には、モデリングとデータ ソースから取得した後は、メモリ内のデータを操作する次の 3 つの選択肢があります。

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)お好みの Microsoft の ORM テクノロジ。 リレーショナル データに対してプログラミングする最上位の .NET オブジェクトとして使用することができます。 新しいアプリケーションの場合、モデルが必要な場合に、最初の既定の選択肢が必要です。 これには、基になる ADO.NET プロバイダーからカスタムのサポートが必要です。

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)前世代のオブジェクト リレーショナル マッパーです。 あまり複雑なシナリオに適してが開発中にないです。

[データセット](../data-tools/dataset-tools-in-visual-studio.md)3 つのモデリング テクノロジの最も古い。 これをいない膨大な量のデータを処理する複雑なクエリや変換を実行する「フォーム オーバー データ」アプリケーションの迅速な開発を主に設計されています。 データセット オブジェクトは、論理的に .NET オブジェクトよりはるかに多くの SQL データベース オブジェクトのように DataTable と DataRow のオブジェクトで構成されます。 比較的単純なアプリケーションの SQL データ ソースに基づいた、データセットに、適切な選択可能性があります。

これらのテクノロジのいずれかを使用する必要はありません。 一部のシナリオでパフォーマンスが重要で、特にできる単にオブジェクトを使用する DataReader をデータベースから読み取ってリストなどのコレクション オブジェクトに必要な値をコピーする\<T >。

## <a name="native-c"></a>ネイティブ C++

SQL Server に接続する C++ アプリケーションを使用する必要があります、 [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)ほとんどの場合。 使用する OLE DB では、必要に応じてとのサーバーをリンクしている場合、 [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)します。 使用して他のデータベースにアクセスできます[ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) OLE DB ドライバーを直接またはします。 ODBC は、現在の標準的なデータベースのインターフェイスが、ほとんどのデータベース システムは、ODBC インターフェイス経由でアクセスできないカスタムの機能を提供します。 OLE DB は、レガシ COM データ アクセス テクノロジが引き続きサポートされますが、新しいアプリケーションをお勧めしません。 詳細については、次を参照してください。 [Visual c でのデータ アクセス](/cpp/data/data-access-in-cpp)します。

REST サービスを使用する C++ プログラムで使用できる、 [C++ REST SDK](https://github.com/Microsoft/cpprestsdk)します。

Microsoft Azure Storage を使用する C++ プログラムで使用できる、 [Microsoft Azure Storage クライアント](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)します。

データ モデリング&mdash;Visual Studio は C++ の ORM レイヤーを提供できません。 [ODB](https://www.codesynthesis.com/products/odb/) C++ の人気のあるオープン ソースの ORM が。

C++ アプリからデータベースへの接続に関する詳細についてを参照してください。 [C++ 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-cpp.md)します。 従来の Visual C のデータ アクセス テクノロジの詳細については、次を参照してください。[データ アクセス](/cpp/data/data-access-in-cpp)します。

## <a name="javascript"></a>JavaScript

[Visual Studio の JavaScript](/scripting/javascript/javascript-language-reference)クロス プラットフォーム アプリ、UWP アプリ、クラウド サービス、web サイト、および web アプリを構築するための第一級の言語です。 Bower、Grunt、Gulp、npm、および Visual Studio 内から NuGet を使用すると、データベース製品、好きな JavaScript ライブラリをインストールします。 Sdk をダウンロードすることによって Azure storage やサービスに接続、 [Azure web サイト](https://azure.microsoft.com/)します。 Edge.js は、サーバー側の JavaScript (Node.js) を ADO.NET データ ソースに接続するライブラリです。

## <a name="python"></a>Python

インストール[Visual Studio での Python サポート](../python/overview-of-python-tools-for-visual-studio.md)Python アプリケーションを作成します。 Azure のドキュメントでは、次を含む、データへの接続に関するいくつかのチュートリアルがあります。

- [Django と SQL Database on Azure](/azure/app-service/app-service-web-get-started-python)
- [Django と MySQL を Azure に](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- 使用[blob](/azure/storage/blobs/storage-quickstart-blobs-python)、[ファイル](/azure/storage/files/storage-python-how-to-use-file-storage)、[キュー](/azure/storage/queues/storage-python-how-to-use-queue-storage)、および[テーブル (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)します。

## <a name="related-topics"></a>関連トピック

[Microsoft AI プラットフォーム](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;Cortana Analytics Suite やモ ノのインターネットのサポートなど、Microsoft のインテリジェント クラウドの概要について説明します。

[Microsoft Azure Storage](/azure/storage/)&mdash;Azure blob、テーブル、キュー、およびファイルを使用してアプリケーションを作成する方法と Azure Storage のについて説明します。

[Azure SQL Database](/azure/sql-database/)&mdash;サービスとしてのリレーショナル データベース、Azure SQL Database に接続する方法について説明します。

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;をデザイン、探索、テスト、およびデータに接続されたアプリケーションとデータベースのデプロイを簡略化するツールについて説明します。

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash; ADO.NET のアーキテクチャについて説明します。また、ADO.NET のクラスを使用してアプリケーション データを管理し、データ ソースおよび XML と対話する方法についても説明します。

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;開発者がリレーショナル データベースに対して直接の代わりに、概念モデルに対してプログラムを許可するデータ アプリケーションを作成する方法について説明します。

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index)&mdash;を使用する方法について説明します[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]を実装する web またはイントラネット上のデータ サービスを展開する、 [Open Data Protocol (OData)](https://www.odata.org/)します。

[Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)&mdash;Office ソリューションでデータを操作する方法を説明するトピックへのリンクが含まれています。 スキーマ指向プログラミング、データ キャッシュ、およびサーバー側データ アクセスに関する説明が含まれます。

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;c# と Visual Basic、およびリレーショナル データベース、XML ドキュメント、データセット、およびインメモリ コレクションを照会するための一般的なモデルに組み込まれたクエリ機能について説明します。

[Visual Studio での XML ツール](../xml-tools/xml-tools-in-visual-studio.md)&mdash;、XML データ、XSLT のデバッグ、.NET Framework の XML 機能の使用と XML クエリのアーキテクチャについて説明します。

[XML ドキュメントとデータ](/dotnet/standard/data/xml/index)&mdash;XML ドキュメントおよび .NET Framework でのデータを処理するクラスの包括的な統合セットを概要を説明します。
