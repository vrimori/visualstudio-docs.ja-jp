---
title: データセットの作成と構成
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- data-storage
ms.openlocfilehash: 23837bcfb1d3761f8ebf23020c15e901833d63b3
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305223"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Visual Studio でデータセットを作成および構成する

データセットは、一連のデータベースからデータをメモリに格納され、有効にする変更の追跡をサポートするオブジェクトを作成、読み取り、更新、および削除 (CRUD) 操作でそのデータを常に、データベースに接続する必要はありません。 データセットは、単純な用に設計された*フォーム オーバー データ*ビジネス アプリケーション。 新しいアプリケーションで、Entity Framework を使用して、保存してメモリ内のデータをモデル化を検討してください。 データセットを使用するには、データベースの概念の基本的な知識があります。

型指定された作成<xref:System.Data.DataSet>を使用してデザイン時に Visual Studio でクラス、**データ ソース構成ウィザード**します。 プログラムでデータセットを作成する方法の詳細については、次を参照してください。[データセット (ADO.NET) を作成する](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset)します。

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>データ ソース構成ウィザードを使用して、新しいデータセットを作成します。

1. Visual Studio でプロジェクトを開いて**プロジェクト** > **新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**します。

2. 接続する先のデータ ソースの種類を選択します。

     ![データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)

3. 以上のデータセットのデータ ソースとなるデータベースを選択します。

     ![データ ソースの接続を選択します。](../data-tools/media/data-source-choose-a-connection.png)

4. テーブル (または個々 の列) ストアド プロシージャ、関数、およびデータセットで表現するためのデータベースからビューを選択します。

     ![データベース オブジェクトの選択](../data-tools/media/raddata-chose-objects.png)

5. **[完了]** をクリックします。

   内のノードで、データセットが表示されます**ソリューション エクスプ ローラー**します。

   ![ソリューション エクスプ ローラーでデータセット](../data-tools/media/dataset-in-solution-explorer.png)

6. データセット ノードをクリックします**ソリューション エクスプ ローラー**でデータセットを開きます、**データセット デザイナー**します。 データセット内の各テーブルが関連付けられている`TableAdapter`下部で表されるオブジェクト。 テーブル アダプターは、データセットを作成して、必要に応じて、データベースにコマンドを送信に使用されます。

   ![データセット デザイナー](../data-tools/media/dataset-designer.png)

7. テーブルを接続するリレーションシップの線は、データベースで定義されているテーブルのリレーションシップを表します。 既定では、データベース内の foreign key 制約は、更新プログラムのみ、リレーションシップとして表されを none に設定された規則を削除します。 通常、対象です。 ただし、表示する行をクリックして、**関係**ダイアログ ボックスで、階層的な更新プログラムの動作を変更することができます。 詳細については、次を参照してください。[データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)と[階層更新](../data-tools/hierarchical-update.md)します。

     ![データセットのリレーションシップ ダイアログ](../data-tools/media/raddata-relation-dialog.png)

8. そのプロパティを表示するテーブル、テーブル アダプター、またはテーブル内の列名をクリックして、**プロパティ**ウィンドウ。 ここで値の一部を変更できます。 ソース データベースではなく、データセットを変更することを忘れないでください。

     ![データセットの列プロパティ](../data-tools/media/dataset-column-properties.png)

9. データセットに新しいテーブルまたはテーブル アダプターを追加または既存のテーブル アダプターの新しいクエリを追加またはからこれらの項目をドラッグして、テーブル間の新しいリレーションの指定、**ツールボックス**タブ。このタブに表示されるときに、**データセット デザイナー**にフォーカスが移動します。

     ![データセットのツールボックス](../data-tools/media/raddata-dataset-toolbox.png)

次に、データを含むデータセットを作成する方法を指定する場合があります。 そのため、使用する、 **TableAdapter 構成ウィザード**します。 詳細については、次を参照してください。 [Tableadapter を使用してデータセットを入力](../data-tools/fill-datasets-by-using-tableadapters.md)します。

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>既存のデータセットをデータベース テーブルまたは他のオブジェクトを追加します。

この手順では、まずデータセットを作成するために使用するのと同じデータベースからテーブルを追加する方法を示します。

1. データセット ノードをクリックします**ソリューション エクスプ ローラー**させる、**データセット デザイナー**にフォーカスが移ります。

2. をクリックして、**データ ソース** タブで、Visual Studio、または型の左余白**データ ソース**で、**クイック起動**ボックス。

3. データセット ノードを右クリックして**ウィザードを使用してデータ ソースの構成**します。

     ![データ ソースのコンテキスト メニュー](../data-tools/media/data-source-context-menu.png)

4. ウィザードを使用して、追加するテーブル、ストアド プロシージャ、またはデータセットに追加するには、その他のデータベース オブジェクトを指定します。

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>データセットにスタンドアロン データ テーブルを追加します。

1. データセット デザイナー**でデータセットを開きます。

2. ドラッグ、<xref:System.Data.DataTable>クラスから、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**します。

3. 列を追加してデータ テーブルを定義します。 テーブルを右クリックし、選択**追加** > **列**します。 使用して、**プロパティ**必要に応じて、列とキーのデータ型を設定するウィンドウ。

スタンドアロン テーブルを実装する必要があります`Fill`ロジックを独立したテーブルにデータを入力するようにします。 スタンドアロンのデータ テーブルの入力方法の詳細については、次を参照してください。 [DataAdapter からの Dataset](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)します。

## <a name="see-also"></a>関連項目

- [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)
- [データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)
- [階層更新](../data-tools/hierarchical-update.md)
- [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)