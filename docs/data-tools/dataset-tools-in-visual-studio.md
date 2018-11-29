---
title: データセットのツール
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- data-storage
ms.openlocfilehash: 3a8a1ac0f2ac4e4b147fbe11dba8d88ccea4c255
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304988"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio のデータセット ツール

> [!NOTE]
> データセットと関連するクラスは、アプリケーションがデータベースから切断されていても、メモリ内のデータを使用するアプリケーションを実現する 2000 年の初めから従来の .NET テクノロジが。 データを変更し、変更を元のデータベースに保持するユーザーを有効にするアプリケーションに特に便利です。 データセットの非常に効果的なテクノロジとなることがわかっていますが、新しい .NET アプリケーションが Entity Framework を使用することをお勧めします。 Entity Framework はオブジェクト モデルと表形式のデータを操作する方法がより自然を示しより単純なプログラミング インターフェイスがあります。

A`DataSet`オブジェクトは基本的にミニ データベースであるメモリ内オブジェクトです。 含まれている`DataTable`、 `DataColumn`、および`DataRow`オブジェクトを格納し、開いている接続を管理することがなく 1 つまたは複数のデータベースからデータを変更します。 データセットは、更新プログラムを追跡し、アプリケーションが再接続されたときに、データベースに送信されるように、そのデータへの変更に関する情報を保持します。

データセットと関連するクラスがで定義されている、 <xref:System.Data?displayProperty=fullName> .NET Framework クラス ライブラリで名前空間。 作成して ADO.NET を使用してコードで動的にデータセットを変更します。 このセクションのドキュメントでは、Visual Studio のデザイナーを使用してデータセットを操作する方法を示します。 デザイナーを使用して作成されたデータセットで**TableAdapter**データベースと対話するオブジェクト。 プログラムで作成されたデータセットを使用して、 **DataAdapter**オブジェクト。 プログラムでデータセットを作成する方法の詳細については、次を参照してください。 [Dataadapter と Datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)します。

使用してパフォーマンスを向上させるを通常取得場合は、アプリケーションは、追加すると、または削除するのみ、データベースからデータを読み取るし、しない更新プログラムを実行する必要があります、`DataReader`ジェネリックにデータを取得するオブジェクト`List`オブジェクトまたは別のコレクション オブジェクト。 データを表示する場合はデータにバインドするユーザー インターフェイスをコレクションにします。

## <a name="dataset-workflow"></a>データセットのワークフロー

Visual Studio には、データセットの操作を簡略化するツールが用意されています。 基本的なエンド ツー エンドのワークフローは次のとおりです。

- 使用して、[データ ソース ウィンドウ](add-new-data-sources.md#data-sources-window)を 1 つまたは複数のデータ ソースから新しいデータセットを作成します。 使用して、**データセット デザイナー**データセットを構成し、そのプロパティを設定します。 たとえば、含めるには、データ ソースからどのテーブルとそれぞれのテーブルから列を指定する必要があります。 データセットが必要とするメモリの量を節約するには、慎重に選択します。 詳細については、[データセットの作成と構成](../data-tools/create-and-configure-datasets-in-visual-studio.md)に関するページを参照してください。

- 外部キーが正しく処理されるように、テーブル間のリレーションシップを指定します。 詳細については、次を参照してください。 [Tableadapter を使用してデータセットを入力](../data-tools/fill-datasets-by-using-tableadapters.md)します。

- 使用して、 **TableAdapter 構成ウィザード**クエリや、データセットを作成するストアド プロシージャを指定し、どのようなデータベース操作 (更新、削除、およびなど) を実装します。 詳細については、次のトピックを参照してください。

    - [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)

    - [データセットのデータの編集](../data-tools/edit-data-in-datasets.md)

    - [データセットのデータの検証](../data-tools/validate-data-in-datasets.md)

    - [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)

- クエリを実行し、データセットで、データを検索します。 詳細については、次を参照してください。[データセットを照会](../data-tools/query-datasets.md)します。 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] により、 [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)内のデータを<xref:System.Data.DataSet>オブジェクト。 詳細については、「[LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)」を参照してください。

- 使用して、**データソース**ウィンドウ ユーザー インターフェイス コントロールをデータセットまたはその個々 の列にバインドして、ユーザーが編集可能な列を指定します。 詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。

## <a name="datasets-and-n-tier-architecture"></a>データセットと N 層アーキテクチャ

N 層アプリケーションでのデータセットについては、次を参照してください。 [n 層アプリケーションでデータセットを操作](../data-tools/work-with-datasets-in-n-tier-applications.md)します。

## <a name="datasets-and-xml"></a>データセットおよび XML

XML との間に、データセットを変換する方法の詳細については、次を参照してください。[データセットにデータを読み取り XML](../data-tools/read-xml-data-into-a-dataset.md)と[データセットを XML として保存](../data-tools/save-a-dataset-as-xml.md)します。

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)