---
title: Visual Studio でのデータへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: eacf075a0ba8689ff0cb5ca822d5cc8ca2f7ad1e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233910"
---
# <a name="accessing-data-in-visual-studio"></a>Visual Studio でのデータにアクセスします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio では、事実上すべてのデータベース製品またはサービスで、任意の場所の形式でデータに接続するアプリケーションを作成することができます: ローカル コンピューターのローカル エリア ネットワーク、またはパブリック、プライベート、およびハイブリッド クラウドで。  
  
 JavaScript、Python、PHP、Ruby、または C++ でのアプリケーションでのデータに接続するライブラリを取得し、コードの記述によって、何も行うようにします。 .NET アプリケーションでは、Visual Studio には、データ ソースの探索、格納、メモリ内のデータを操作し、ユーザー インターフェイスにデータをバインドしてオブジェクト モデルの作成を使用できるツールが用意されています。     Microsoft Azure は、Azure Storage に接続するため、.NET、Java、Node.js、PHP、Python、Ruby、およびモバイル アプリ、および Visual Studio のツールの Sdk を提供します。  
  
 次の表は、Visual Studio から使用できる多くのデータベースとストレージ システムのほんの一部を示します。 [Microsoft Azure](https://azure.microsoft.com/en-us/)サービス/データはすべてのプロビジョニングと、基になるデータ ストアの管理を含むデータ サービス。  [Azure Tools for Visual Studio](https://www.visualstudio.com/en-us/features/azure-tools-vs.aspx)は Visual Studio から直接 Azure データ ストアを操作することができます、省略可能なコンポーネントです。 製品の大半の他の SQL および NoSQL データベースは、ここに記載されているローカル コンピューターで、ローカル ネットワーク、または Microsoft Azure で仮想マシンでホストできます。 このシナリオでは、データベース自体の管理を担当します。  
  
 **Microsoft Azure**  
  
||||  
|-|-|-|  
|SQL Database|DocumentDB|ストレージ (blob、テーブル、キュー、ファイル)|  
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|  
  
 その他  
  
 **SQL**  
  
||||  
|-|-|-|  
|SQL Server 2005 –、やなど 2016 Express LocalDB|Firebird|MariaDB|  
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
  
 多くのデータベース ベンダーやサード パーティは、NuGet パッケージによって Visual Studio の統合をサポートします。 Nuget.org または Visual Studio で NuGet パッケージ マネージャーを通じて、オファリングを調べることができます (**ツール** > **NuGet パッケージ マネージャー** > **NuGet の管理ソリューションのパッケージの**)。 他のデータベース製品は、拡張機能として、Visual Studio と統合します。   移動して、Visual Studio ギャラリーでこれらの製品を参照する**ツール** > **拡張機能と更新プログラム**し選択**オンライン**左にあります。ダイアログ ボックスのウィンドウです。  詳細については、次を参照してください。[データベース システム、ツール、およびサンプルをインストールする](../data-tools/installing-database-systems-tools-and-samples.md)します。  
  
> [!NOTE]
>  SQL Server 2005 の延長サポートは 2016 年 4 月 12 日に終了しました。   データ ツールの Visual Studio 2015 以降では引き続きこの日付より後の SQL Server 2005 で機能する保証はありません。 詳細については、次を参照してください。、 [for SQL Server 2005 サポート終了のお知らせ](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)します。  
  
### <a name="net-languages"></a>.NET 言語  
 .NET Core で含む、すべての .NET データ アクセスは、ADO.NET、任意の種類のデータ ソース、リレーショナルと非リレーショナルの両方にアクセスするためのインターフェイスを定義する一連のクラスに基づきます。 Visual Studio がいくつかのツールと、データベースに接続するための ADO.NET を使用するデザイナーがデータを操作およびユーザーにデータを表示します。 このセクションのドキュメントでは、これらのツールを使用する方法について説明します。 コマンドの ADO.NET オブジェクトに対して直接プログラムすることもできます。 ADO.NET の Api を直接呼び出すことの詳細については、次を参照してください。 [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) 、MSDN ライブラリ。  
  
 データ アクセスのドキュメントが ASP.NET に関連する具体的には、次を参照してください。[データを扱う](http://www.asp.net/web-forms/overview/presenting-and-managing-data)ASP.NET サイト。 ASP.NET MVC で Entity Framework の使用に関するチュートリアルについては、次を参照してください。 [Entity Framework 6 Code First MVC 5 の使用の概要](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)します。  
  
 C# または Visual Basic でのユニバーサル Windows プラットフォーム (UWP) アプリでは、Microsoft Azure SDK for .NET を使用して、Azure Storage と他の Azure サービスにアクセスします。 Windows.Web.HttpClient クラスは、任意の RESTful サービスとの通信を使用できます。 詳細については、次を参照してください[Windows.Web.Http を使用して HTTP サーバーに接続する方法。](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx.)  
  
 ローカル コンピューター上のデータ ストレージ、アプリと同じプロセスで実行される、SQLite を使用することをお勧めします。 オブジェクト リレーショナル マッピング (ORM) 層が必要な場合は、Entity Framework を使用することができます。 詳細については、次を参照してください。[データ アクセス](https://msdn.microsoft.com/windows/uwp/data-access/index)、Windows デベロッパー センターでします。  
  
 Azure サービスに接続する場合は、最新バージョンをダウンロードすることを確認する[Azure SDK tools](https://azure.microsoft.com/en-us/downloads/)します。  
  
#### <a name="data-providers"></a>データ プロバイダー  
 ADO.NET で使用できるようにするデータベースの場合、ユーザー設定が必要*ADO.NET データ プロバイダー*またはそれ以外の場合、ODBC または OLE DB インターフェイスを公開する必要があります。 Microsoft が提供、 [ADO.NET データ プロバイダーの一覧](https://msdn.microsoft.com/data/dd363565)ODBC および OLE DB プロバイダーと、SQL Server の製品です。  
  
#### <a name="data-modeling"></a>データ モデリング  
 .NET には、モデリングとデータ ソースから取得した後は、メモリ内のデータを操作する次の 3 つの選択肢があります。  
  
 Entity Framework  
 推奨される Microsoft の ORM テクノロジ。 リレーショナル データに対してプログラミングする最上位の .NET オブジェクトとして使用することができます。 新しいアプリケーションの場合、モデルが必要な場合に、最初の既定の選択肢が必要です。 これには、基になる ADO.NET プロバイダーからカスタムのサポートが必要です。  
  
 LINQ to SQL  
 前世代のオブジェクト リレーショナル マッパーです。 あまり複雑なシナリオに適してが開発中にないです。  
  
 データセット  
 次の 3 つのモデリング テクノロジの最も古い。 これをいない膨大な量のデータを処理する複雑なクエリや変換を実行する「フォーム オーバー データ」アプリケーションの迅速な開発を主に設計されています。 データセット オブジェクトは、論理的に .NET オブジェクトよりはるかに多くの SQL データベース オブジェクトのように DataTable と DataRow のオブジェクトで構成されます。 比較的単純なアプリケーションの SQL データ ソースに基づいた、データセットに、適切な選択可能性があります。  
  
 これらのテクノロジのいずれかを使用する必要はありません。 一部のシナリオでパフォーマンスが重要で、特にできる単にオブジェクトを使用する DataReader をデータベースから読み取ってリストなどのコレクション オブジェクトに必要な値をコピーする\<T >。  
  
### <a name="native-c"></a>ネイティブ C++  
 SQL Server に接続する C++ アプリケーションを使用する必要があります、 [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx)します。 使用して他のデータベースにアクセスできます[ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) OLE DB ドライバーを直接またはします。 ODBC は、現在の標準的なデータベースのインターフェイスが、ほとんどのデータベース システムは、ODBC インターフェイス経由でアクセスできないカスタムの機能を提供します。  OLE DB は、レガシ COM データ アクセス テクノロジが引き続きサポートされますが、新しいアプリケーションをお勧めしません。  詳細については、次を参照してください。[データ アクセス](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)します。  
  
 REST サービスを使用する C++ プログラムで使用できる、 [C++ REST SDK](https://github.com/Microsoft/cpprestsdk)します。  
  
 Microsoft Azure Storage を使用する C++ プログラムで使用できる、 [Microsoft Azure Storage クライアント](http://www.nuget.org/packages/wastorage)します。  
  
#### <a name="data-modeling"></a>データ モデリング  
 Visual Studio では、c++、ORM レイヤーは提供されません。  [ODB](http://www.codesynthesis.com/products/odb/) C++ の人気のあるオープン ソースの ORM が。  
  
 従来の Visual C のデータ アクセス テクノロジの詳細については、次を参照してください[データ アクセス。](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)  
  
### <a name="javascript"></a>JavaScript  
 [Visual Studio の JavaScript](https://msdn.microsoft.com/library/hh334522.aspx)クロス プラットフォーム アプリ、UWP アプリ、クラウド サービス、web サイト、および web アプリを構築するための第一級の言語です。 Bower、Grunt、Gulp、npm、および Visual Studio 内から NuGet を使用すると、データベース製品、好きな JavaScript ライブラリをインストールします。 Sdk をダウンロードすることによって Azure storage やサービスに接続、 [Azure web サイト](https://azure.microsoft.com/)します。  Edge.js は、サーバー側の JavaScript (Node.js) を ADO.NET データ ソースに接続するライブラリです。  
  
### <a name="python"></a>Python  
 インストール[Python Tools for Visual Studio](http://microsoft.github.io/PTVS/)と共に、好みの Python フレームワーク CPython や IronPython (.NET) のアプリケーションを作成します。  Python Tools for Visual Studio の web サイトがいくつかのチュートリアルを含む、データへの接続に関する[Django と SQL Database on Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure)、 [Django と MySQL を Azure に](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure)と[Bottle と MongoDB でAzure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データベース システム、ツール、およびサンプルをインストールする](../data-tools/installing-database-systems-tools-and-samples.md)  
 データベース製品と、Visual Studio 拡張機能や、それらをサポートするドライバーを取得する方法と実験と学習のためのサンプル データベースを検索する場所について説明します。  
  
 [.NET 用の Visual Studio データ ツール](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)  
 Visual Studio のツール ウィンドウを使用して、データ ソースに接続し、データセットや Entity Framework モデルでは、作成、ユーザー インターフェイス コントロールにデータをバインドする方法について説明します。  
  
## <a name="related-topics"></a>関連トピック  
 [データ、デバイス、および分析](https://msdn.microsoft.com/data-and-devices)  
 Cortana Analytics Suite やモ ノのインターネットのサポートなど、Microsoft のインテリジェント クラウドの概要を提供します。  
  
 [Microsoft Azure Storage](https://azure.microCsoft.com/en-us/documentation/services/storage/)  
 Azure Storage、および Azure blob、テーブル、キュー、およびファイルを使用してアプリケーションを作成する方法について説明します。  
  
 [Azure SQL Database](https://azure.microsoft.com/en-us/documentation/services/sql-database/)  
 Azure SQL データベース、サービスとしてのリレーショナル データベースに接続する方法について説明します。  
  
 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
 デザイン、探索、テスト、およびデータに接続されたアプリケーションとデータベースのデプロイを簡略化するツールについて説明します。  
  
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)  
 ADO.NET のアーキテクチャについて説明します。また、ADO.NET のクラスを使用してアプリケーション データを管理し、データ ソースおよび XML と対話する方法についても説明します。  
  
 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
 開発者がリレーショナル データベースに対して直接プログラミングするのではなく、概念モデルに対してプログラミングすることができるデータ アプリケーションを作成する方法について説明します。  
  
 [WCF Data Services 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a)  
 使用する方法について説明します[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]を実装する web またはイントラネット上のデータ サービスを展開する、 [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204)します。  
  
 [Office ソリューションにおけるデータ](http://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a)  
 Office ソリューションで、データが機能するしくみについて説明したトピックへのリンクを示します。 スキーマ指向プログラミング、データ キャッシュ、およびサーバー側データ アクセスに関する説明が含まれます。  
  
 [統合言語クエリ (LINQ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 C# および Visual Basic に組み込まれたクエリ機能と、リレーショナル データベース、XML ドキュメント、データセット、およびインメモリ コレクションを照会するための共通のモデルについて説明します。  
  
 [Visual Studio の XML ツール](../xml-tools/xml-tools-in-visual-studio.md)  
 XML データ、XSLT のデバッグ、.NET Framework の XML の機能の使用と XML クエリのアーキテクチャについて説明します。  
  
 [XML ドキュメントと XML データ](http://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380)  
 .NET Framework で XML ドキュメントおよびデータを処理するための、統合された包括的な一連のクラスについて概説します。

