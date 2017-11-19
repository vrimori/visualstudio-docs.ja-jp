---
title: "Visual Studio でのデータセット ツール |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.data.DataSet
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
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 6a7e5741b11263ef3c3730ddaa69e566cd7c2e24
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio でのデータセットのツール
> [!NOTE]
>  データセットと関連クラスは、アプリケーションがデータベースから切断されている間、メモリ内のデータを操作するアプリケーションを有効に 2000 年初めから従来の .NET テクノロジです。 これらは、ユーザーがデータを変更し、データベースへの変更を永続化を有効にするアプリケーションの特に役立ちます。 データセットの非常に成功したテクノロジをすることがわかっていますが、新しい .NET アプリケーションが Entity Framework を使用することをお勧めします。 Entity Framework は、オブジェクト モデルと表形式のデータを使用するより自然な方法を提供し、シンプルなプログラミング インターフェイスがあります。  
  
 DataSet オブジェクトは、ミニ データベースでは基本的には、メモリ内オブジェクトです。 DataTable と DataColumn、DataRow オブジェクト格納し、開いている接続を維持することがなく 1 つまたは複数のデータベースからデータを変更にはが含まれています。 データセットは、更新プログラムを追跡し、アプリケーションが再接続されたときに、データベースに送信できるように、そのデータへの変更に関する情報を保持します。  
  
 データセットと関連クラスは、.NET Framework クラス ライブラリ内の System.Data 名前空間で定義されます。 作成してコードで動的にデータセットを変更します。 実行する方法の詳細については、ADO.NET を参照してください。 このセクションのドキュメントでは、Visual Studio のデザイナーを使用してデータセットを操作する方法を示します。 1 つの点を知る: はプログラムによって行われたデータセット DataAdapter オブジェクトを使用して、デザイナーによって行われたデータセットが、データベースとやり取りする TableAdapter のオブジェクトを使用します。 データセットをプログラムで作成する方法の詳細については、次を参照してください。 [Dataadapter と Datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)です。  
  
 場合は、アプリケーションをのみをデータベースからデータの読み取りし、いない更新プログラムを実行する必要があります、追加、または削除、汎用の List オブジェクトまたは別のコレクション オブジェクトにデータを取得する DataReader オブジェクトを使用してパフォーマンスを向上させる通常取得できます。 データを表示する場合できますデータをバインドするユーザー インターフェイスのコレクション。  
  
## <a name="dataset-workflow"></a>データセットのワークフロー  
 Visual Studio では、多数のデータセットの操作が簡単にツールを提供します。 基本的なエンド ツー エンド ワークフローとは。  
  
-   使用して、**データ ソース**ウィンドウを 1 つまたは複数のデータ ソースから新しいデータセットを作成します。 使用して、**データセット デザイナー**データセットを構成し、そのプロパティを設定します。 たとえば、含めるには、データ ソースからどのテーブルと各テーブルから列を指定する必要があります。 データセットが必要になるメモリの量を節約するために慎重に選択します。 詳細については、[データセットの作成と構成](../data-tools/create-and-configure-datasets-in-visual-studio.md)に関するページを参照してください。  
  
-   外部キーが正しく処理されるように、テーブル間のリレーションシップを指定します。 詳細については、次を参照してください。 [Tableadapter を使用してデータセットを入力](../data-tools/fill-datasets-by-using-tableadapters.md)です。  
  
-   使用して、 **TableAdapter 構成ウィザード**クエリまたはデータセットを作成するストアド プロシージャを指定してどのようなデータベース操作 (update、delete、およびなど) を実装します。 詳細については、次のトピックを参照してください。  
  
    -   [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [データセットのデータの編集](../data-tools/edit-data-in-datasets.md)  
  
    -   [データセットのデータの検証](../data-tools/validate-data-in-datasets.md)  
  
    -   [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)  
  
-   クエリを実行し、データセット内のデータを検索します。 詳細については、次を参照してください。[クエリのデータセット](../data-tools/query-datasets.md)です。 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]により、[クエリ (LINQ: Language-Integrated)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)でデータを<xref:System.Data.DataSet>オブジェクト。 詳細については、「[LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset)」を参照してください。  
  
-   使用して、**データ ソース**ウィンドウのユーザー インターフェイス コントロールをデータセットまたはその個々 の列にバインドしてユーザーが編集できるのどの列を指定します。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)です。  
  
## <a name="datasets-and-n-tier-architecture"></a>データセットと N 層アーキテクチャ  
 N 層アプリケーションでデータセットの概要については、次を参照してください。 [n 層アプリケーションでデータセットを操作](../data-tools/work-with-datasets-in-n-tier-applications.md)です。  
  
## <a name="datasets-and-xml"></a>データセットおよび XML  
 Xml 形式からデータセットを変換する方法については、次を参照してください。[データセットにデータを読み取り XML](../data-tools/read-xml-data-into-a-dataset.md)と[データセットを XML として保存](../data-tools/save-a-dataset-as-xml.md)です。  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)