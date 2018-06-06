---
title: Visual Studio でデータセットを作成および構成する
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b47df77b9666b46f24665e9c99cbf9a0c52593cd
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746573"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Visual Studio でデータセットを作成および構成する

A*データセット*をデータベースからデータをメモリに格納し、変更の追跡を有効にするをサポートするオブジェクトのセットは、作成、読み取り、更新、およびそのデータを常に、データベースに接続する必要はありません (CRUD) 操作を削除します。 データセットは、単純な用に設計された*フォーム オーバー データ*ビジネス アプリケーション。 新しいアプリケーションは、Entity Framework を格納およびメモリのデータをモデルに使用を検討してください。 データセットを使用するには、データベースの概念に関する基本的な知識が必要です。

型指定されたを作成する<xref:System.Data.DataSet>を使用してデザイン時に Visual Studio でのクラス、**データ ソース構成ウィザード**です。 データセットをプログラムで作成する方法については、次を参照してください。[データセット (ADO.NET) を作成する](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset)です。

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>データ ソース構成ウィザードを使用して、新しいデータセットを作成します。

1.  **プロジェクト** メニューのをクリックして**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**です。

2.  接続するデータ ソースの種類を選択します。

     ![データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)

3.  データベースの場合は、データベースまたはデータセットのデータ ソースとなるデータベースを選択します。

     ![データ ソースの接続を選択します。](../data-tools/media/data-source-choose-a-connection.png)

4.  テーブル (または個々 の列) ストアド プロシージャ、関数、およびデータセットで表現するデータベースからビューを選択します。

     ![データベース オブジェクトを選択します。](../data-tools/media/raddata-chose-objects.png)

5.  **[完了]** をクリックします。

6.  内のノードとして表示されます、データセット**ソリューション エクスプ ローラー**:

     ![ソリューション エクスプ ローラーでデータセット](../data-tools/media/dataset-in-solution-explorer.png)

     そのノードをクリックしてにデータセットが表示されます、**データセット デザイナー**です。 データセット内の各テーブルが下部に表される、関連付けられた TableAdapter オブジェクトを持つことに注意してください。 テーブル アダプターは、データセットを作成して、必要に応じてコマンドを送信するデータベースに使用されます。

     ![データセット デザイナー](../data-tools/media/dataset-designer.png)

7.  テーブルを接続するリレーションシップの線は、データベースで定義されているテーブルのリレーションシップを表します。 既定は、データベース内の foreign key 制約は、更新プログラムでリレーションシップのみとして表され、[なし] に設定されているルールを削除します。 通常は、対象です。 ただし、表示する行をクリックして、**関係**ダイアログ ボックスで、階層的な更新プログラムの動作を変更することができます。 詳細については、次を参照してください。[データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)と[階層更新](../data-tools/hierarchical-update.md)です。

     ![データセットのリレーション ダイアログ](../data-tools/media/raddata-relation-dialog.png)

8.  プロパティを表示するテーブル、テーブル アダプター、またはテーブル内の列名をクリックして、**プロパティ**ウィンドウです。 ここで値の一部を変更することができます。 ソース データベースではなく、データセットを変更することを忘れないでください。

     ![データセットの列のプロパティ](../data-tools/media/dataset-column-properties.png)

9. データセットに新しいテーブルまたはテーブル アダプターを追加または既存のテーブル アダプターの新しいクエリを追加またはからこれらの項目をドラッグして、テーブル間のリレーションの新しいを指定できます、**ツールボックス**タブです。このタブを表示するには**データセット デザイナー**フォーカスが移動します。

     ![データセット [ツールボックス]](../data-tools/media/raddata-dataset-toolbox.png)

10. 次に、データを含むデータセットを作成する方法を指定する可能性があります。 そのため、使用する、 **TableAdapter 構成ウィザード**です。 詳細については、次を参照してください。 [Tableadapter を使用してデータセットを入力](../data-tools/fill-datasets-by-using-tableadapters.md)です。

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>既存のデータセットに、データベース テーブルまたはその他のオブジェクトを追加します。

この手順では、まずデータセットを作成するために使用するのと同じデータベースからテーブルを追加する方法を示します。

1.  データセット ノードをクリックして**ソリューション エクスプ ローラー**をデータセット デザイナーにフォーカスが移ります。

2.  クリックして、**データ ソース** タブで、Visual Studio の左余白または入力`Data Sources`で**クイック起動**です。

3.  データセット ノードを右クリックし **ウィザードを使用してデータ ソースの構成**です。

     ![データ ソースのコンテキスト メニュー](../data-tools/media/data-source-context-menu.png)

4.  ウィザードを使用してする追加のテーブル、ストアド プロシージャ、またはデータセットに追加するその他のデータベース オブジェクトを指定します。

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>データセットにスタンドアロンのデータ テーブルを追加します。

1.  データセットを開き、**データセット デザイナー**です。

2.  ドラッグ、<xref:System.Data.DataTable>クラス、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**です。

3.  列を追加してデータ テーブルを定義します。 テーブルを右クリックし、選択**追加 > 列**です。 使用して、**プロパティ**を必要に応じて、列およびキーのデータ型を設定するウィンドウです。

4.  独立したテーブルを実装する必要があります`Fill`ロジック独立したテーブルでデータを入力するようにします。 スタンドアロンのデータ テーブルの入力方法の詳細については、次を参照してください。 [DataAdapter からの DataSet の読み込み](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)です。

## <a name="see-also"></a>関連項目

- [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)