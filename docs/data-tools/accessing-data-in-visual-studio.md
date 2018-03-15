---
title: "Visual Studio でのデータにアクセスする |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: article
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e7c4c9aada390259d4abd57484c20d25728ef91f
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="accessing-data-in-visual-studio"></a>Visual Studio でのデータにアクセスします。

Visual Studio で、ほぼすべてのデータベース製品または任意の形式で、任意の場所のサービスのデータに接続するアプリケーションを作成することができます、ローカル コンピューターのローカル エリア ネットワーク、またはパブリック、プライベート、またはハイブリッド クラウド。

JavaScript、Python、PHP、Ruby、または C++ では、アプリケーションのデータに接続するには、何でもしてライブラリを取得するコードの記述と同じようにします。 .NET アプリケーションの場合は、Visual Studio は、データ ソースの探索を格納し、メモリ内のデータを操作およびユーザー インターフェイスにデータをバインドするオブジェクト モデルを作成し、使用できるツールを提供します。 Microsoft Azure は、Azure ストレージに接続するため、.NET、Java、Node.js、PHP、Python、Ruby、およびモバイル アプリ、および Visual Studio のツールの Sdk を提供します。

次の表は、Visual Studio から使用できる多くのデータベースと記憶域システムの一部だけを示します。 [Microsoft Azure](https://azure.microsoft.com/)内容はデータなどのサービスのすべてのプロビジョニングと、基になるデータ ストアの管理。  [Azure Tools for Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx)オプションのコンポーネントであり、Visual Studio から直接 Azure データ ストアを操作することができます。 ほとんど他の SQL、NoSQL データベース製品は、ここに記載されているは、ローカル コンピューター、ローカル ネットワーク上または Microsoft Azure で仮想マシン上でホストできます。 このシナリオでは、データベース自体の管理を担当すます。

**Microsoft Azure**

||||
|-|-|-|
|SQL Database|DocumentDB|ストレージ (blob、テーブル、キュー、ファイル)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

その他

**SQL**

||||
|-|-|-|
|SQL Server 2005-2016 Express LocalDB など|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

その他

**NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

その他

多くのデータベース ベンダーやサード パーティは、NuGet パッケージによって Visual Studio の統合をサポートします。 Nuget.org または Visual Studio で NuGet パッケージ マネージャーで、内容を調べることができます (**ツール** > **NuGet Package Manager** > **NuGet の管理Packages for Solution**)。 他のデータベース製品は、拡張機能として、Visual Studio と統合します。 移動して、Visual Studio Marketplace でこれらの製品を表示できる**ツール**、**拡張機能と更新**を選択し**オンライン**の左側のウィンドウで、ダイアログ ボックス。 詳細については、次を参照してください。 [for Visual Studio の互換性のあるデータベース システム](../data-tools/installing-database-systems-tools-and-samples.md)です。

> [!NOTE]
> SQL Server 2005 の延長サポートは 2016 年 4 月 12 日に終了しました。 データ ツールの Visual Studio 2015 以降では引き続きこの日後、SQL Server 2005 で動作する保証はありません。 詳細については、次を参照してください。、 [SQL Server 2005 のサポートの終了の発表](https://www.microsoft.com/sql-server/sql-server-2005)です。

## <a name="net-languages"></a>.NET 言語

.NET Core を含む、すべての .NET データ アクセスは、ADO.NET、任意の種類のデータ ソース、リレーショナルおよび非リレーショナルの両方にアクセスするためのインターフェイスを定義する一連のクラスに基づいています。 Visual Studio がいくつかのツールとデザイナーを使用すると、データベースに接続するように ADO.NET を使用するデータを操作およびユーザーにデータを表示します。 このセクションのドキュメントでは、これらのツールを使用する方法について説明します。 また、ADO.NET コマンド オブジェクトに対して直接プログラミングすることができます。 ADO.NET Api を直接呼び出すの詳細については、次を参照してください。 [ADO.NET](/dotnet/framework/data/adonet/index)です。

データ アクセスのドキュメントが ASP.NET に関連する具体的には、次を参照してください。[データを扱う](http://www.asp.net/web-forms/overview/presenting-and-managing-data)ASP.NET サイトです。 ASP.NET MVC で Entity Framework の使用に関するチュートリアルは、次を参照してください。 [Entity Framework 6 の Code First MVC 5 を使用すると作業の開始](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)です。

C# または Visual Basic でのユニバーサル Windows プラットフォーム (UWP) アプリは、Microsoft Azure SDK for .NET を使用して、Azure Storage や他の Azure サービスにアクセスすることができます。 Windows.Web.HttpClient クラスには、任意の RESTful サービスとの通信ができるようにします。 詳細については、次を参照してください。 [Windows.Web.Http を使用して HTTP サーバーに接続する方法](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx)です。

ローカル コンピューター上のデータ記憶域、SQLite は、アプリと同じプロセスで実行するために使用することをお勧めします。 オブジェクト リレーショナル マッピング (ORM) レイヤーが必要な場合は、Entity Framework を使用することができます。 詳細については、次を参照してください。[データ アクセス](/windows/uwp/data-access/index)Windows デベロッパー センターにします。

Azure サービスに接続する場合、最新のダウンロードを必ず[Azure SDK tools](https://azure.microsoft.com/downloads/)です。

### <a name="data-providers"></a>データ プロバイダー

ADO.NET で使用できるようにするデータベースの場合があります、カスタム*ADO.NET データ プロバイダー*またはそれ以外の場合、ODBC または OLE DB インターフェイスを公開する必要があります。 マイクロソフトが提供、 [ADO.NET データ プロバイダーの一覧](https://msdn.microsoft.com/data/dd363565)ODBC および OLE DB プロバイダーと同様に SQL Server の製品です。

### <a name="data-modeling"></a>データ モデリング

.NET には、モデリングおよびそのデータ ソースから取得した後、メモリ内のデータを操作するための 3 つの選択肢があります。

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)推奨される Microsoft ORM テクノロジです。 リレーショナル データをプログラミングするファースト クラスの .NET オブジェクトとして使用することができます。 新しいアプリケーションの場合、モデルが必要な場合に最初の既定の選択肢をことがします。 これには、基になる ADO.NET プロバイダーからカスタムのサポートが必要です。

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)以前生成オブジェクト リレーショナル マッパーです。 小さい複雑なシナリオに適してが、アクティブな開発ではなくなった。

[データセット](../data-tools/dataset-tools-in-visual-studio.md)3 種類のモデリング テクノロジの中で最も古いします。 主にすることがなく大量のデータの処理、複雑なクエリや変換を実行する「フォーム オーバー データ」アプリケーションの迅速な開発されています。 DataSet オブジェクトは、論理的に .NET オブジェクトよりはるかに多くの SQL データベース オブジェクトのように DataTable と DataRow のオブジェクトで構成されます。 比較的単純なアプリケーションの SQL データ ソースに基づいた、データセットに、適切な選択可能性があります。

これらのテクノロジのいずれかを使用する必要はありません。 一部のシナリオでパフォーマンスは重要では、特にできる単にオブジェクトを使用する DataReader、データベースから読み取るし、リストなどのコレクション オブジェクトに必要な値をコピーする\<T > です。

## <a name="native-c"></a>ネイティブ C++

SQL Server に接続する C++ アプリケーションを使用する必要があります、 [SQL Server 用 Microsoft® ODBC Driver 13.1](https://www.microsoft.com/download/details.aspx?id=53339)ほとんどの場合。 OLE DB が必要とするためのサーバーをリンクしている場合を使用、 [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)です。 使用して他のデータベースにアクセスできます[ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx)または OLE DB ドライバー直接です。 ODBC は、現在の標準的なデータベース インターフェイスが、ほとんどのデータベース システムが ODBC インターフェイス経由でアクセスできないカスタムの機能を提供します。 OLE DB は、レガシ COM データ アクセス テクノロジではまだサポートされていますが、新しいアプリケーションをお勧めしません。 詳細については、次を参照してください。 [Visual c でのデータ アクセス](/cpp/data/data-access-in-cpp)です。

REST サービスを使用する C++ プログラムで使用できます、 [C++ REST SDK](https://github.com/Microsoft/cpprestsdk)です。

Microsoft Azure Storage を使用する C++ プログラムで使用できます、 [Microsoft Azure ストレージ クライアント](http://www.nuget.org/packages/wastorage)です。

データ モデリング&mdash;Visual Studio は C++ を ORM レイヤーを提供しません。 [ODB](http://www.codesynthesis.com/products/odb/) C++ の一般的なオープン ソース ORM がします。

C++ アプリからデータベースへの接続に関する詳細についてを参照してください。 [C++ 用の Visual Studio data tools](../data-tools/visual-studio-data-tools-for-cpp.md)です。 レガシの Visual C のデータ アクセス テクノロジの詳細については、次を参照してください。[データ アクセス](/cpp/data/data-access-in-cpp)です。

## <a name="javascript"></a>JavaScript

[Visual Studio での JavaScript の](/scripting/javascript/javascript-language-reference)クロスプラット フォーム アプリ、UWP アプリ、クラウド サービス、web サイト、および web アプリケーションを構築するためのファースト クラスの言語です。 お気に入りの JavaScript ライブラリとデータベースの製品をインストールするのに、Bower、Grunt、Gulp、npm、および Visual Studio 内から NuGet を使用できます。 Azure のストレージおよびサービスに接続から Sdk をダウンロードして、 [Azure web サイト](https://azure.microsoft.com/)です。 Edge.js は、サーバー側 JavaScript (Node.js) を ADO.NET データ ソースに接続しているライブラリです。

## <a name="python"></a>Python

インストール[Visual Studio での Python サポート](../python/python-in-visual-studio.md)Python アプリケーションを作成します。 Azure のドキュメントでは、データは、次のように接続するいくつかのチュートリアルがあります。

- [Django、Azure 上の SQL データベース](/azure/app-service/app-service-web-get-started-python)
- [Django、Azure の MySQL](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- 扱う[blob](/azure/storage/blobs/storage-quickstart-blobs-python)、[ファイル](/azure/storage/files/storage-python-how-to-use-file-storage)、[キュー](/azure/storage/queues/storage-python-how-to-use-queue-storage)、および[テーブル (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)です。

## <a name="related-topics"></a>関連トピック

[Microsoft AI プラットフォーム](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;Cortana Analytics Suite、モ ノのインターネットのサポートなど、マイクロソフトのインテリジェントなクラウドの概要について説明します。

[Microsoft Azure Storage](/azure/storage/)&mdash;Azure ストレージの説明、および Azure blob、テーブル、キュー、およびファイルを使用してアプリケーションを作成する方法です。

[Azure SQL Database](/azure/sql-database/)&mdash;Azure SQL データベース、サービスとしてのリレーショナル データベースに接続する方法について説明します。

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;をデザイン、探索、テスト、およびデータベースやデータに接続しているアプリケーションの展開を簡略化するツールについて説明します。

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;ADO.NET アーキテクチャおよび ADO.NET クラスを使用してアプリケーション データを管理し、データ ソースおよび XML と対話する方法について説明します。

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)&mdash;開発者がリレーショナル データベースに対して直接の代わりに、概念モデルに対してプログラムを使用できるデータ アプリケーションを作成する方法について説明します。

[WCF データ サービス 4.5](/dotnet/framework/data/wcf/index)&mdash;を使用する方法について説明[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]を実装する web またはイントラネット上のデータ サービスを展開する、 [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204)です。

[Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)&mdash;Office ソリューションでデータを操作する方法を説明するトピックへのリンクが含まれています。 スキーマ指向プログラミング、データ キャッシュ、およびサーバー側データ アクセスに関する説明が含まれます。

[クエリ (LINQ: Language-Integrated)](/dotnet/csharp/linq/)&mdash;c# および Visual Basic、およびリレーショナル データベース、XML ドキュメント、データセット、およびインメモリ コレクションを照会するための共通のモデルに組み込まれたクエリ機能について説明します。

[Visual Studio での XML ツール](../xml-tools/xml-tools-in-visual-studio.md)&mdash;操作、XML データ、XSLT のデバッグ、.NET Framework XML の機能、および XML Query のアーキテクチャについて説明します。

[XML ドキュメントとデータ](/dotnet/standard/data/xml/index)&mdash;を包括的な統合された一連の XML ドキュメントおよび .NET Framework でのデータを処理するクラスについて概説します。