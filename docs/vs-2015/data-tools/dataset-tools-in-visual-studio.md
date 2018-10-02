---
title: Visual Studio でのデータセット ツール |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d01dd2de60285d669f5a36a2f6ddf7a08449dad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533680"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio でのデータセット ツール
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio でのデータセット ツール](https://docs.microsoft.com/visualstudio/data-tools/dataset-tools-in-visual-studio)します。  
  
  
注]
>  データセットと関連するクラスは、アプリケーションがデータベースから切断されていても、メモリ内のデータを使用するアプリケーションを実現する 2000 年の初めから従来の .NET テクノロジが。 データを変更し、変更を元のデータベースに保持するユーザーを有効にするアプリケーションに特に便利です。 データセットの非常に効果的なテクノロジとなることがわかっていますが、新しい .NET アプリケーションが Entity Framework を使用することをお勧めします。 Entity Framework はオブジェクト モデルと表形式のデータを操作する方法がより自然を示しより単純なプログラミング インターフェイスがあります。  
  
 データセット オブジェクトは、ミニ データベースでは基本的には、メモリ内オブジェクトです。 DataTable と DataColumn の場合、DataRow オブジェクト格納し、開いている接続を管理することがなく 1 つまたは複数のデータベースからデータを変更にはが含まれています。 データセットは、更新プログラムを追跡し、アプリケーションが再接続されたときに、データベースに送信されるように、そのデータへの変更に関する情報を保持します。  
  
 データセットと関連するクラスは、.NET Framework クラス ライブラリの System.Data 名前空間で定義されます。 作成してコードで動的にデータセットを変更します。 その方法の詳細については、ADO.NET を参照してください。 このセクションのドキュメントでは、Visual Studio のデザイナーを使用してデータセットを操作する方法を示します。 1 つです: プログラムによって行われたデータセットを使用して、DataAdapter オブジェクトは、デザイナーによって行われたデータセットが、データベースと対話する TableAdapter オブジェクトを使用します。 プログラムでデータセットを作成する方法の詳細については、次を参照してください。 [Dataadapter と Datareader](http://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74)します。  
  
 場合は、アプリケーションは、追加すると、または削除するのみ、データベースからデータを読み取るし、しない更新プログラムを実行する必要があります、汎用の List オブジェクトまたは別のコレクション オブジェクトにデータを取得する DataReader オブジェクトを使用して、通常はパフォーマンスが向上を取得できます。 データを表示する場合はデータにバインドするユーザー インターフェイスをコレクションにします。  
  
## <a name="dataset-workflow"></a>データセットのワークフロー  
 Visual Studio では、データセットの操作を簡略化するツールが多数用意されています。 基本的なエンド ツー エンドのワークフローは次のとおりです。  
  
-   使用して、**データ ソース**ウィンドウを 1 つまたは複数のデータ ソースから新しいデータセットを作成します。 使用して、**データセット デザイナー**データセットを構成し、そのプロパティを設定します。 たとえば、含めるには、データ ソースからどのテーブルとそれぞれのテーブルから列を指定する必要があります。 データセットが必要になるメモリの量を節約するために慎重に選択します。 詳細については、[データセットの作成と構成](../data-tools/create-and-configure-datasets-in-visual-studio.md)に関するページを参照してください。  
  
-   外部キーが正しく処理されるように、テーブル間のリレーションシップを指定します。 詳細については、次を参照してください。 [Tableadapter を使用してデータセットを入力](../data-tools/fill-datasets-by-using-tableadapters.md)します。  
  
-   使用して、 **TableAdapter 構成ウィザード**クエリや、データセットを作成するストアド プロシージャを指定し、どのようなデータベース操作 (更新、削除、およびなど) を実装します。 詳細については、次のトピックを参照してください。  
  
    -   [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [データセットのデータの編集](../data-tools/edit-data-in-datasets.md)  
  
    -   [データセットのデータの検証](../data-tools/validate-data-in-datasets.md)  
  
    -   [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)  
  
-   クエリを実行し、データセットで、データを検索します。 詳細については、次を参照してください。[データセットを照会](../data-tools/query-datasets.md)します。 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] により、 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)内のデータを<xref:System.Data.DataSet>オブジェクト。 詳細については、「[LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)」を参照してください。  
  
-   使用して、**データソース**ウィンドウ ユーザー インターフェイス コントロールをデータセットまたはその個々 の列にバインドして、ユーザーが編集可能な列を指定します。 詳細については、次を参照してください。 [Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。  
  
## <a name="datasets-and-n-tier-architecture"></a>データセットと N 層アーキテクチャ  
 N 層アプリケーションでのデータセットについては、次を参照してください。 [n 層アプリケーションでデータセットを操作](../data-tools/work-with-datasets-in-n-tier-applications.md)します。  
  
## <a name="datasets-and-xml"></a>データセットおよび XML  
 XML との間に、データセットを変換する方法の詳細については、次を参照してください。[データセットにデータを読み取り XML](../data-tools/read-xml-data-into-a-dataset.md)と[データセットを XML として保存](../data-tools/save-a-dataset-as-xml.md)します。  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)

