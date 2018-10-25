---
title: データベース システム、ツール、およびサンプルをインストールする |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f18ace9a18eefd0758e581b83001b85c3f48a3da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244284"
---
# <a name="installing-database-systems-tools-and-samples"></a>データベース システム、ツール、およびサンプルをインストールします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio 自体では、すべてのデータベース システムで内部的に使用する以外は含まれません。 Visual Studio でのデータに接続されたアプリケーションを開発するには、通常、ローカル開発用コンピューター、データベース システムをインストールし、アプリケーションとデータベースに展開、運用環境の準備ができたら。 .NET アプリケーションからアクセスできるようにして、Visual Studio データ ツールのウィンドウに表示されるデータベース システムでは、ADO.NET データ プロバイダーが必要です。 プロバイダーは、.NET アプリケーションでエンティティ データ モデルを使用する場合、Entity Framework をサポート具体的にする必要があります。     NuGet パッケージ マネージャーを使用または Visual Studio ギャラリーを使って、多くのプロバイダーが提供されます。  
  
 SQL の開発用 Visual Studio にインストールされている SQL Server Data Tools があることを確認します。 をクリックして、**ビュー**メニュー。 SQL Server オブジェクト エクスプ ローラーが表示されない場合は、コントロール パネルに移動し、Visual Studio を変更します。 インストーラーで次のように選択します。 **Microsoft SQL Server Data Tools**します。  
  
 Azure Storage Api を使用している場合、運用環境にデプロイする準備ができるまでに料金を回避するために、ローカル コンピューターで開発中の Azure ストレージ エミュレーターをインストールします。 詳細については、次を参照してください。[開発とテストのため、Azure ストレージ エミュレーターを使用して](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/)します。  
  
 次の一覧には、Visual Studio プロジェクトで使用できる最も一般的なデータベース システムの一部が含まれます。 一覧は完全ではありません。 Visual Studio のツールとの統合を有効にする ADO.NET データ プロバイダーを提供しているサード パーティ ベンダーの一覧は、次を参照してください。 [ADO.NET データ プロバイダー](https://msdn.microsoft.com/library/dd363565.aspx)します。  
  
### <a name="microsoft-sql-server"></a>Microsoft SQL Server  
 SQL Server は、マイクロソフトの主力データベースを提供します。 SQL Server 2016 では、常識を覆すパフォーマンス、高度なセキュリティは、豊富で統合されたレポートと分析を提供します。 さまざま方法で使用できるように設計されたさまざまなエディションで出荷: 拡張性の高い、高パフォーマンスのビジネス分析は、1 台のコンピューターで使用するからです。 SQL Server Express は、再配布と埋め込み用に調整されている SQL Server の完全版です。  LocalDB は、簡略化された構成は必要ありませんし、アプリケーションのプロセスで実行している SQL Server Express のエディションです。 いずれかまたは両方の製品をダウンロードする[SQL Server Express のダウンロード ページ](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)します。    このセクションでは SQL の例の多くは、SQL Server LocalDB を使用します。 SQL Server Management Studio (SSMS) とは、Visual Studio の SQL Server Object Explorer で提供されているものより多くの機能を含むスタンドアロンのデータベース管理アプリケーションです。 SSMS は、前のリンクから取得できます。  
  
### <a name="oracle"></a>Oracle  
 Oracle データベースからの有料版または無料版をダウンロードすることができます、 [Oracle テクノロジ ネットワーク](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html)ページ。 Entity Framework と Tableadapter、デザイン時サポートが必要になります、 [Oracle Developer Tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html)します。 他の公式の Oracle 製品などの Oracle Instant Client では、NuGet パッケージ マネージャーを使用することができます。  Oracle サンプル スキーマをダウンロードするには次の手順で、 [Oracle のオンライン ドキュメント](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)します。  
  
### <a name="mysql"></a>MySQL  
 MySQL は、企業および web サイトで広く使用されている一般的なオープン ソース データベース システムです。 MySQL のダウンロードは、Visual Studio、および関連する製品の MySQL は[Windows での MySQL](http://www.mysql.com/why-mysql/windows/)します。  サード パーティでは、さまざまな Visual Studio 拡張機能と MySQL 用のスタンドアロンの管理アプリケーションを提供します。 NuGet パッケージ マネージャーでのオファリングを参照することができます (**ツール** > **NuGet パッケージ マネージャー** > **ソリューションの NuGet パッケージの管理**).  
  
### <a name="postgresql"></a>PostgreSQL  
 PostgreSQL は、無料のオープン ソースのオブジェクト リレーショナル データベース システムです。 Windows のインストールからダウンロードできます、 [PostgreSQL ダウンロード ページ](http://www.postgresql.org/download/windows/)します。  ソース コードから PostgreSQL を作成することもできます。  PostgreSQL コアのシステムには、C 言語のインターフェイスが含まれています。 多くのサード パーティは、.NET アプリケーションから PostgreSQL を使用するための NuGet パッケージを提供します。  NuGet パッケージ マネージャーでのオファリングを参照することができます (**ツール** > **NuGet パッケージ マネージャー** > **ソリューションの NuGet パッケージの管理**). おそらく、最も人気のあるパッケージは、によって提供される[npgsql.org](http://www.npgsql.org)します。  
  
### <a name="sqlite"></a>SQLite  
 SQLite は、アプリケーションのプロセスで実行されている埋め込みの SQL データベース エンジンです。 ダウンロードすることができます、 [SQLite ダウンロード ページ](http://www.sqlite.org/download.html)します。 SQLite の多くのサード パーティ製 NuGet パッケージも使用できます。 NuGet パッケージ マネージャーでのオファリングを参照することができます (**ツール** > **NuGet パッケージ マネージャー** > **ソリューションの NuGet パッケージの管理**).  
  
### <a name="firebird"></a>Firebird  
 Firebird は、オープン ソースの SQL データベースのシステムです。 ダウンロードすることができます、 [Firebird ダウンロード ページ](http://firebirdsql.org/en/downloads/)します。 ADO.NET データ プロバイダーでは、NuGet パッケージ マネージャーを使用することができます。  
  
## <a name="see-also"></a>関連項目  
 [バージョンとエディションの SQL Server とそのコンポーネントを確認する方法](http://support.microsoft.com/kb/321185)

