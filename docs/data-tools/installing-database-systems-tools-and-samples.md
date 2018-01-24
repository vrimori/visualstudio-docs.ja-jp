---
title: "Visual Studio のデータベース互換性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 8fbe818e233c8bbdaf4431c70b8962baf43a2ed2
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2018
---
# <a name="compatible-database-systems-for-visual-studio"></a>Visual Studio の互換性のあるデータベースのシステム

Visual Studio でのデータに接続しているアプリケーションを開発するには、通常、ローカルの開発用コンピューターにデータベース システムをインストールし、アプリケーションとデータベースを運用環境に配置の準備ができたら。 Visual Studio コンピューター上の SQL Server Express LocalDB のインストールの一部として、**データ ストレージと処理**ワークロード。 LocalDB インスタンスは迅速かつ簡単にデータに接続しているアプリケーションを開発するために役立ちます。

.NET アプリケーションからアクセスできるようにして、Visual Studio データ ツール ウィンドウで表示するデータベース システムは、ADO.NET データ プロバイダーが必要です。 .NET アプリケーションでエンティティ データ モデルを使用する場合は、Entity Framework プロバイダーをサポートすることが具体的にはあります。 多くのプロバイダーは、NuGet パッケージ マネージャーを使用または Visual Studio Marketplace を通じて提供されます。

Azure ストレージ Api を使用している場合、実稼働環境に展開する準備ができたら、料金を回避するために、ローカル コンピューターで開発中の Azure ストレージ エミュレーターをインストールします。 詳細については、次を参照してください。[開発とテストのため、Azure ストレージ エミュレーターを使用して](/azure/storage/common/storage-use-emulator)です。

次の一覧には、Visual Studio プロジェクトで使用できる最も一般的なデータベース システムの一部が含まれます。 一覧が完全ではありません。 Visual Studio のツールとの緊密な統合を有効にする ADO.NET データ プロバイダーを提供するサード パーティ ベンダーの一覧は、次を参照してください。 [ADO.NET データ プロバイダー](/dotnet/framework/data/adonet/data-providers)です。

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server は、Microsoft の主要データベースを提供します。 SQL Server 2016 では、画期的なパフォーマンス、高度なセキュリティ、および豊富な統合されたレポートと分析を提供します。 さまざまな用途向けに設計された各種エディションで出荷: 1 台のコンピューターで使用する、拡張性の高い、高パフォーマンスのビジネス分析からです。 SQL Server Express は、再配布と埋め込み向け SQL Server のフル機能エディションです。  LocalDB は、SQL Server Express の構成を必要とせず、アプリケーションのプロセスで実行を簡略化されたエディションです。 いずれかまたは両方の製品をダウンロードすることができます、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)です。 このセクションで SQL の例の多くは、SQL Server LocalDB を使用します。 SQL Server Management Studio (SSMS) とは、Visual Studio SQL Server オブジェクト エクスプ ローラーで提供されるよりも多くの機能を持つスタンドアロンのデータベース管理アプリケーションです。 SSMS は、前のリンクから取得できます。

## <a name="oracle"></a>Oracle

Oracle データベースの有料または無料のエディションをダウンロードすることができます、 [Oracle テクノロジ ネットワーク](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html)ページ。 Entity Framework と Tableadapter のデザイン時サポートが必要になります、 [Oracle Developer Tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html)です。 他の正式な Oracle を含む製品 Oracle Instant Client では、利用 NuGet パッケージ マネージャーを使用します。  Oracle サンプル スキーマをダウンロードするには、手順に従って、 [Oracle のオンライン マニュアル](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)です。

## <a name="mysql"></a>MySQL

MySQL は、企業および web サイトで広く使用されている一般的なオープン ソースのデータベース システムです。 MySQL のダウンロード、Visual Studio、および関連する製品の MySQL は[Windows 上の MySQL](http://www.mysql.com/why-mysql/windows/)です。  サード パーティでは、さまざまな Visual Studio 拡張機能と MySQL のスタンドアロンの管理アプリケーションを提供します。 NuGet Package Manager での内容を参照することができます (**ツール** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL は、無料、オープン ソースのオブジェクト リレーショナル データベース システムです。 これをインストールする windows からダウンロードできます、 [PostgreSQL ダウンロード ページ](http://www.postgresql.org/download/windows/)です。  ソース コードから PostgreSQL をビルドすることもできます。  PostgreSQL コア システムには、C 言語インターフェイスが含まれています。 多くのサード パーティは、.NET アプリケーションから PostgreSQL を使用するための NuGet パッケージを提供します。  NuGet Package Manager での内容を参照することができます (**ツール** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**). おそらく、最も人気のあるパッケージは、によって提供される[npgsql.org](http://www.npgsql.org)です。

## <a name="sqlite"></a>SQLite

SQLite は、埋め込まれた SQL データベース エンジン アプリケーションのプロセスで実行されています。 ダウンロードすることができます、 [SQLite ダウンロード ページ](http://www.sqlite.org/download.html)です。 SQLite のサード パーティ製 NuGet パッケージの多くも使用できます。 NuGet Package Manager での内容を参照することができます (**ツール** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**).

## <a name="firebird"></a>Firebird

Firebird は、オープン ソースの SQL データベースのシステムです。 ダウンロードすることができます、 [Firebird ダウンロード ページ](http://firebirdsql.org/en/downloads/)です。 ADO.NET データ プロバイダーでは、NuGet Package Manager を使用することができます。

## <a name="see-also"></a>関連項目

[Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)  
[バージョンおよびエディションの SQL Server とそのコンポーネントを確認する方法](http://support.microsoft.com/kb/321185)