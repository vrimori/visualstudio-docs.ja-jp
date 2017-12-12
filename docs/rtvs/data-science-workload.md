---
title: "データ サイエンスと分析のアプリケーション ワークロード | Microsoft Docs"
ms.custom: 
ms.date: 9/5/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
- devlang-python
- devlang-fsharp
ms.tgt_pltfrm: 
ms.topic: landing-page
ms.assetid: 018069f3-6d1a-4143-a851-d86d2ff5fbfc
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 976bd73c7740e474e4fa7ea3e4cf89f880c7900c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="data-science-and-analytical-applications-workload"></a>データ サイエンスと分析のアプリケーション ワークロード

Visual Studio のデータ サイエンスと分析のアプリケーション ワークロードでは、次の 3 つの言語と、そのランタイム ディストリビューションを使用できます。

- [R および Microsoft R Client](../rtvs/index.md)
- [Python および Anaconda](../python/python-in-visual-studio.md)
- [.NET framework と F#](https://docs.microsoft.com/dotnet/fsharp/)

![Visual Studio インストーラーのデータ サイエンスと分析のアプリケーション ワークロード](media/data-science-workload.png)

R と Python は、データ サイエンスで使用される主要な 2 つのスクリプト言語です。 いずれの言語も学習が簡単で、パッケージの機能豊富なエコシステムのサポートがあります。 それらのパッケージは、データの取得、クリーンアップ、モデルのトレーニング、展開およびプロットなどの広範囲のシナリオに対応しています。 そして、F# は、さまざまなデータ処理タスクに適した機能第一の強力な .NET 言語です。

<!--Note link on the image because this one is large -->
[![R、Python および F# が使用されている Visual Studio のスクリーンショット](media/data-science-workload-screens.png)](media/data-science-workload-screens.png)

## <a name="workload-options"></a>ワークロード オプション

ワークロードは、既定で次のオプションをインストールします。これは、Visual Studio インストーラーのワークロードの [概要] セクションで変更できます。

- F# 言語サポート
- Python:
    - Python 言語サポート
    - Python Web サポート
    - [Anaconda3 64 ビット](https://www.continuum.io) (さまざまなデータ サイエンス ライブラリおよび Python インタープリターを含む Python ディストリビューションです。)
    - cookiecutter テンプレートのサポート
- R:
    - R 言語サポート    
    - [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started) (単一ノードまたはクラスターで高速に計算を実行するための ScaleR ライブラリを含む、Microsoft 社の完全互換のコミュニティでサポートされている R インタープリターです。 [CRAN](https://cran.r-project.org/) の任意の R も使用できます。)
    - R 開発ツールのランタイム サポート

> [!Note]
> F# はその他の多数のワークロードにも含まれており、Python には独自のワークロードがありますが、R は現在、データ サイエンスと分析のアプリケーション ワークロードのみに含まれています。ワークロードとは別に、3 つの R コンポーネントは、インストーラーの **[個別のコンポーネント]** タブから選択することも可能です。 **[開発作業]、[R 言語サポート]**、**[開発作業]、[Microsoft R Client]**、および **[コンパイラ、ビルド ツール、およびランタイム]、[R 開発ツールのランタイム サポート]** のオプションを選択します。

## <a name="sql-server-integration"></a>SQL Server の統合

SQL Server では、SQL Server 内で直接高度な分析を行うことが可能な R と Python の両方の使用をサポートしています。 R は SQL Server 2016 以降でサポートされており、Python は SQL Server 2017 CTP 2.0 以降でサポートされています。

データが既にあるところでコードを実行できることによる多数の利点があります。それらは次のとおりです。

- **データ移動が不要**: データをデータベースからアプリケーションまたはモデルに移動せずに、データベース内で R および Python アプリケーションをビルドすることができます。 この機能により、セキュリティ、コンプライアンス、ガバナンスおよび整合性の障壁が取り除かれ、大量のデータの移動に関係する同様の多数の問題もなくなります。 また、クライアントのマシンのメモリに入りきらないデータセットを使用することも可能になります。

- **導入が簡単**: R または Python モデルの準備ができたら、T-SQL スクリプトに単純に埋め込むことによって、それを本番に導入することができます。 任意の言語で記述された任意の SQL クライアント アプリケーションで、ストアド プロシージャ呼び出しを使用して、モデルおよびインテリジェンスを利用することができます。 R または Python の特定の統合を実行する必要はありません。

- **エンタープライズ レベルのパフォーマンスとスケール**: メモリ内テーブルと列のストア インデックスなどの SQL Server の高度な機能を、RevoScaleR パッケージおよび RevoScalePy パッケージの高性能な拡張性の高い API と共に使用できます。 データを移動する必要がなくなるということは、データが大きくなった場合や、アプリケーションのパフォーマンスを向上させる場合のクライアント メモリの制約を回避できることも意味します。

- **拡張性が高い**: SQL Server に任意の最新のオープン ソースの R または Python パッケージをインストールし実行して、SQL Server 内の大量のデータにディープ ラーニングおよび AI アプリケーションを構築できます。 SQL Server にパッケージをインストールすることは、ローカル マシンにパッケージをインストールするのと同じくらい簡単です。

- **追加コストなしで広範に利用可能**: R と Python は、Express Edition を含む SQL Server 2017 以降のすべてのエディションに統合できます。 (R は、SQL Server 2016 以降でサポートされています)。

SQL Server に統合することのメリットを最大限に得るには、**[SQL Server Data Tools]** オプションを使用して**データ ストレージと処理**ワークロードをインストールする必要もあります。 このオプションにより、SQL IntelliSense、構文の強調表示および展開が可能になります。

![データの保存と処理ワークロード](media/data-storage-workload.png) &nbsp;&nbsp; &nbsp;&nbsp; ![データの保存と処理ワークロード オプション](media/data-storage-workload-options.png)


詳細情報

- [SQL Server と R の使用](../rtvs/sql-server.md)
- [SQL Server 2016 での R を使用したデータベース内の高度な分析](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [SQL Server 2017 での Python: データベース内機械学習の強化](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>その他のサービスと SDK

データ サイエンスと分析のアプリケーション ワークロードに直接あるものに加え、Azure Notebook サービスと Azure SDK for Python もデータ サイエンスに役立ちます。

Azure SDK for Python を使用すると、Windows、Mac OSX、Linux で実行されているアプリケーションからの Microsoft Azure サービスの使用と管理が簡単になります。 詳細については、「[Azure SDK for Python](../python/azure-sdk-for-python.md)」を参照してください。

Azure Notebook (現在プレビュー中) を使用すると、クラウドで Microsoft Azure で実行されている Jupyter Notebook に自由にオンライン アクセスできます。 このサービスには、使用を開始できるように Python、R および F# のサンプル ノートブックが含まれています。 [notebooks.azure.com](https://notebooks.azure.com/) を参照してください。

<!--Note link on the image because this one is large -->
[![入門用の R のサンプルと Azure Notebook のスクリーンショット](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png)