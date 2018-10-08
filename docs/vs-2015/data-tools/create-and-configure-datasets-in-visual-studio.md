---
title: 作成し、Visual Studio でのデータセットの構成 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eddb8ffbe483d0c2d5396530333db2f7e7827d04
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547674"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Visual Studio でデータセットを作成および構成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[作成し、Visual Studio でのデータセットを構成](https://docs.microsoft.com/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)します。  
  
  
A*データセット*一連のデータベースからデータをメモリに格納され、有効にする変更の追跡をサポートするオブジェクトは、作成、読み取り、更新および削除 (CRUD) 操作でそのデータを常に、データベースに接続する必要はありません。 データセットは、単純な用に設計された*フォーム オーバー データ*ビジネス アプリケーション。 新しいアプリケーションで、Entity Framework を使用して、保存してメモリ内のデータをモデル化を検討してください。 データセットを使用するには、データベースの概念の基本的な知識があります。  
  
 型指定されたを作成する<xref:System.Data.DataSet>を使用してデザイン時に Visual Studio でクラス、**データ ソース構成ウィザード**します。 プログラムでデータセットを作成する方法の詳細については、次を参照してください。[データセットを作成する](http://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc)します。  
  
## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>データ ソース構成ウィザードを使用して、新しいデータセットを作成します。  
  
1.  **プロジェクト** メニューのをクリックして**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**します。  
  
2.  接続するデータ ソースの種類を選択します。  
  
     ![データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png "データ ソース構成ウィザード")  
  
3.  データベースの場合、またはデータセットのデータ ソースとなる複数のデータベースを選択します。  
  
     ![データ ソースの接続の選択](../data-tools/media/data-source-choose-a-connection.png "データ ソースの接続の選択")  
  
4.  テーブル (または個々 の列) ストアド プロシージャ、関数、およびデータセットで表現するためのデータベースからビューを選択します。  
  
     ![データベース オブジェクトの選択](../data-tools/media/raddata-chose-objects.png "raddata 選択オブジェクト")  
  
5.  **[完了]** をクリックします。  
  
6.  内のノードで、データセットが表示されます**ソリューション エクスプ ローラー**:  
  
     ![ソリューション エクスプ ローラーでデータセット](../data-tools/media/dataset-in-solution-explorer.png "ソリューション エクスプ ローラーでデータセット")  
  
     そのノードをクリックしに、データセットが表示されます、**データセット デザイナー**します。 データセット内の各テーブルが下部で表される、関連付けられた TableAdapter オブジェクトを持つことに注意してください。 テーブル アダプターは、データセットを作成して、必要に応じて、データベースにコマンドを送信に使用されます。  
  
     ![データセット デザイナー](../data-tools/media/dataset-designer.png "データセット デザイナー")  
  
7.  テーブルを接続するリレーションシップの線は、データベースで定義されているテーブルのリレーションシップを表します。 既定では、データベース内の foreign key 制約は、更新プログラムのみ、リレーションシップとして表されを none に設定された規則を削除します。 通常、対象です。 ただし、表示する行をクリックして、**関係**ダイアログ ボックスで、階層的な更新プログラムの動作を変更することができます。 詳細については、次を参照してください。[データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)と[階層更新](../data-tools/hierarchical-update.md)します。  
  
     ![Dataset リレーション ダイアログ](../data-tools/media/raddata-relation-dialog.png "raddata 関係ダイアログ")  
  
8.  そのプロパティを表示するテーブル、テーブル アダプター、またはテーブル内の列名をクリックして、**プロパティ**ウィンドウ。 ここで値の一部を変更できます。 ソース データベースではなく、データセットを変更することを忘れないでください。  
  
     ![データセットの列プロパティ](../data-tools/media/dataset-column-properties.png "データセット列のプロパティ")  
  
9. データセットに新しいテーブルまたはテーブル アダプターを追加または既存のテーブル アダプターの新しいクエリを追加またはからこれらの項目をドラッグして、テーブル間の新しいリレーションの指定、**ツールボックス**タブ。このタブに表示されるときに、**データセット デザイナー**にフォーカスが移動します。  
  
     ![データセットのツールボックス](../data-tools/media/raddata-dataset-toolbox.png "raddata データセット ツールボックス")  
  
10. 次に、おそらく、データセットにデータを設定する方法を指定します。 そのため、使用する、 **TableAdapter 構成ウィザード**します。 詳細については、次を参照してください。 [Tableadapter を使用してデータセットを入力](../data-tools/fill-datasets-by-using-tableadapters.md)します。  
  
## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>既存のデータセットをデータベース テーブルまたは他のオブジェクトを追加します。  
 この手順では、まずデータセットを作成するために使用するのと同じデータベースからテーブルを追加する方法を示します。  
  
1.  データセット ノードをクリックします**ソリューション エクスプ ローラー**データセット デザイナーにフォーカスをします。  
  
2.  をクリックして、**データ ソース** タブで、Visual Studio の左側の余白または入力`Data Sources`で**クイック起動**します。  
  
3.  データセット ノードを右クリックして**ウィザードを使用してデータ ソースの構成**します。  
  
     ![データ ソースのコンテキスト メニュー](../data-tools/media/data-source-context-menu.png "データ ソースのコンテキスト メニュー")  
  
4.  ウィザードを使用して、どの追加のテーブルまたはストアド プロシージャか、データセットに追加するその他のデータベース オブジェクトを指定します。  
  
## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>データセットにスタンドアロン データ テーブルを追加します。  
  
1.  データセットを開き、**データセット デザイナー**します。  
  
2.  ドラッグ、<xref:System.Data.DataTable>クラスから、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**します。  
  
3.  列を追加してデータ テーブルを定義します。 詳細については、次を参照してください。[方法: DataTable に列を追加](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)します。  
  
4.  スタンドアロン テーブルを実装する必要があります`Fill`ロジックを独立したテーブルにデータを入力するようにします。 スタンドアロンのデータ テーブルの入力方法の詳細については、次を参照してください。 [DataAdapter からの Dataset](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)します。

