---
title: データベースの互換性
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 064e6042e734b5564c1f7270ef41a1747919b877
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880326"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Visual Studio 向けの互換性のあるデータベース システム

Visual Studio でのデータに接続されたアプリケーションを開発するには、通常、ローカル開発用コンピューター、データベース システムをインストールし、アプリケーションとデータベースに展開、運用環境の準備ができたら。 Visual Studio では、コンピューターに SQL Server Express LocalDB をインストールの一部として、**データ ストレージと処理**ワークロード。 LocalDB インスタンスは、迅速かつ簡単にデータに接続されたアプリケーションを開発するために便利です。

.NET アプリケーションからアクセスできるようにして、Visual Studio データ ツールのウィンドウに表示されるデータベース システムは、ADO.NET データ プロバイダーが必要です。 プロバイダーは、.NET アプリケーションでエンティティ データ モデルを使用する場合、Entity Framework をサポート具体的にする必要があります。 NuGet パッケージ マネージャーを使用または Visual Studio Marketplace を通じて、多くのプロバイダーが提供されます。

Azure storage Api を使用している場合、運用環境にデプロイする準備ができるまでに料金を回避するために、ローカル コンピューターで開発中の Azure ストレージ エミュレーターをインストールします。 詳細については、次を参照してください。[開発およびテスト用の Azure ストレージ エミュレーターを使用して](/azure/storage/common/storage-use-emulator)します。

次の一覧には、Visual Studio プロジェクトで使用できる最も一般的なデータベース システムの一部が含まれます。 一覧は完全ではありません。 Visual Studio のツールとの統合を有効にする ADO.NET データ プロバイダーを提供しているサード パーティ ベンダーの一覧は、次を参照してください。 [ADO.NET データ プロバイダー](/dotnet/framework/data/adonet/data-providers)します。

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server は、マイクロソフトの主力データベースを提供します。 SQL Server 2016 では、常識を覆すパフォーマンス、高度なセキュリティは、豊富で統合されたレポートと分析を提供します。 さまざま方法で使用できるように設計されたさまざまなエディションで出荷: 拡張性の高い、高パフォーマンスのビジネス分析は、1 台のコンピューターで使用するからです。 SQL Server Express は、再配布と埋め込み用に調整されている SQL Server の完全版です。  LocalDB は、簡略化された構成は必要ありませんし、アプリケーションのプロセスで実行している SQL Server Express のエディションです。 いずれかまたは両方の製品をダウンロードすることができます、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)します。 このセクションでは SQL の例の多くは、SQL Server LocalDB を使用します。 SQL Server Management Studio (SSMS) とは、Visual Studio の SQL Server Object Explorer で提供されているものより多くの機能を含むスタンドアロンのデータベース管理アプリケーションです。 SSMS は、前のリンクから取得できます。

## <a name="oracle"></a>Oracle

Oracle データベースからの有料版または無料版をダウンロードすることができます、 [Oracle テクノロジ ネットワーク](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html)ページ。 Entity Framework と Tableadapter、デザイン時サポートが必要になります、 [Oracle Developer tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html)します。 他の公式の Oracle 製品などの Oracle Instant Client では、NuGet パッケージ マネージャーを使用することができます。 Oracle サンプル スキーマをダウンロードするには次の手順で、 [Oracle のオンライン ドキュメント](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)します。

## <a name="mysql"></a>MySQL

MySQL は、企業および web サイトで広く使用されている一般的なオープン ソース データベース システムです。 MySQL のダウンロードは、Visual Studio、および関連する製品の MySQL は[Windows での MySQL](http://www.mysql.com/why-mysql/windows/)します。 サード パーティでは、さまざまな Visual Studio 拡張機能と MySQL 用のスタンドアロンの管理アプリケーションを提供します。 NuGet パッケージ マネージャーでのオファリングを参照することができます (**ツール** > **NuGet パッケージ マネージャー** > **ソリューションの NuGet パッケージの管理**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL は、無料のオープン ソースのオブジェクト リレーショナル データベース システムです。 Windows のインストールからダウンロードできます、 [PostgreSQL ダウンロード ページ](http://www.postgresql.org/download/windows/)します。 ソース コードから PostgreSQL を作成することもできます。 PostgreSQL コアのシステムには、C 言語のインターフェイスが含まれています。 多くのサード パーティは、.NET アプリケーションから PostgreSQL を使用するための NuGet パッケージを提供します。 NuGet パッケージ マネージャーでのオファリングを参照することができます (**ツール** > **NuGet パッケージ マネージャー** > **ソリューションの NuGet パッケージの管理**). おそらく、最も人気のあるパッケージは、によって提供される[npgsql.org](http://www.npgsql.org)します。

## <a name="sqlite"></a>SQLite

SQLite は、アプリケーションのプロセスで実行されている埋め込みの SQL データベース エンジンです。 ダウンロードすることができます、 [SQLite ダウンロード ページ](http://www.sqlite.org/download.html)します。 SQLite の多くのサード パーティ製 NuGet パッケージも使用できます。 NuGet パッケージ マネージャーでのオファリングを参照することができます (**ツール** > **NuGet パッケージ マネージャー** > **ソリューションの NuGet パッケージの管理**).

## <a name="firebird"></a>Firebird

Firebird は、オープン ソースの SQL データベースのシステムです。 ダウンロードすることができます、 [Firebird ダウンロード ページ](http://firebirdsql.org/en/downloads/)します。 ADO.NET データ プロバイダーでは、NuGet パッケージ マネージャーを使用することができます。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
- [SQL Server とそのコンポーネントのバージョンとエディションを確認する方法](http://support.microsoft.com/kb/321185)