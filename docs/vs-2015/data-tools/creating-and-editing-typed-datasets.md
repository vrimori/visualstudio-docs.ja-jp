---
title: 作成して、型指定されたデータセットの編集 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8c18717cd2a5c7e05b79dbe575d919ef0c8670dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225843"
---
# <a name="creating-and-editing-typed-datasets"></a>型指定されたデータセットの作成と編集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**データセット デザイナー**は型指定されたデータセットとそれに含まれる個々 のアイテム作成および編集に使用できるビジュアル ツールのセットです。  
  
 **データセット デザイナー**型指定されたデータセットに含まれるオブジェクトのビジュアル表現を提供します。 作成および変更する[Tableadapter](../data-tools/tableadapter-overview.md)、 [TableAdapter クエリ](../data-tools/how-to-create-tableadapter-queries.md)、 <xref:System.Data.DataTable>s、<xref:System.Data.DataColumn>秒、および<xref:System.Data.DataRelation>を**データセット デザイナー**します。  
  
 開くには、**データセット デザイナー**でデータセットをダブルクリック**ソリューション エクスプ ローラー**でデータセットを右クリックするか、**データ ソース**ウィンドウをクリックします**編集デザイナーで DataSet を**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。 新しい追加<xref:System.Data.DataSet>を持つ項目が、**新しい項目の追加**ダイアログ ボックスが開きます、**データセット デザイナー**で、空のデータセットの編集を開始します。  
  
> [!NOTE]
>  **データセット デザイナー**データセットの機能を拡張するために使用できます。 デザイン サーフェイスをダブルクリックまたは右クリックし **コードの表示**しない変更またはデザイナーによって削除されるデータセットにコードを追加する部分クラス ファイルを作成します。 TableAdapter の機能を拡張する方法の詳細については、次を参照してください。 [TableAdapter の機能を拡張](../data-tools/extend-the-functionality-of-a-tableadapter.md)します。  
  
 次の表で実行できる一般的なタスク、**データセット デザイナー**します。  
  
|終了|解決方法については、|  
|--------|---------|  
|TableAdapter の作成|[Tableadapter の作成および構成](../data-tools/create-and-configure-tableadapters.md)|  
|TableAdapter の編集|[方法: Tableadapter を編集します。](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|TableAdapter クエリの作成|[方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)|  
|TableAdapter クエリの編集|[方法 : TableAdapter クエリを編集する](../data-tools/how-to-edit-tableadapter-queries.md)|  
|<xref:System.Data.DataTable> の作成|[方法: データ テーブルを作成する](../data-tools/how-to-create-data-tables.md)|  
|<xref:System.Data.DataTable> の編集|[DataTable のデザイン](../data-tools/designing-datatables.md)|  
|<xref:System.Data.DataColumn> の作成|[方法: DataTable に列を追加](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|2 つの <xref:System.Data.DataTable> 間のリレーションシップの作成|[方法: データセット デザイナーで Datarelation を作成](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|データセットの機能の拡張|[方法: データセットの機能を拡張](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|データ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントへの検証の追加|[方法: 列の変更時にデータを検証](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|データ テーブルの <xref:System.Data.DataTable.RowChanging> イベントへの検証の追加|[方法: 行の変更時にデータを検証](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>デザイン サーフェイスでのオブジェクトの作成  
 データセットを構成する各オブジェクトを追加したり編集したりして、データセットを作成できます。 次の表に、さまざまなオブジェクトの説明を提供します、**データセット** タブで、**ツールボックス**デザイン サーフェイスにドラッグできます。  
  
|Object|説明|  
|------------|-----------------|  
|TableAdapter|基になるデータベースとの通信およびデータ テーブルへのデータの格納に使用する、データ コマンドのコレクションおよびデータ接続が含まれます。 詳細については、次を参照してください。 [TableAdapter の概要](../data-tools/tableadapter-overview.md)と[作成し、Tableadapter 構成](../data-tools/create-and-configure-tableadapters.md)します。|  
|クエリ|TableAdapter のクエリは、SQL ステートメントとストアド プロシージャを実行する、厳密に型指定されたメソッドです。 TableAdapter クエリを実行すると、データ テーブルにデータが格納されたり、他のデータベース タスクが実行されたりします。 詳細については、次を参照してください。[方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)です。 空の領域にクエリをドラッグした場合は、そのテーブルにクエリを追加、テーブルにクエリをドラッグ、**データセット デザイナー**グローバル クエリを作成します。 詳細については、次を参照してください。[方法: TableAdapter にグローバル クエリの追加](../data-tools/how-to-add-global-queries-to-a-tableadapter.md)します。|  
|<xref:System.Data.DataTable>|データベースから返された行のメモリ内コレクションを示します。|  
|リレーションシップ (<xref:System.Data.DataRelation>)|2 つの <xref:System.Data.DataTable> 間の親子のリレーションシップを表します。 詳細については、次を参照してください。 [DataRelation オブジェクトの概要](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)と[チュートリアル: データ テーブル間のリレーションシップを作成する](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)します。|  
  
> [!NOTE]
>  **データセット デザイナー**を基になるデータベースに接続するとき、データセットのみが作成されます。 デザイナーでは、データベースへの後続の変更を自動的に検出しません。 再実行して既存の .xsd を更新する、**構成ウィザード**します。 テーブルのリレーションシップが変更された場合は、.xsd に関連するテーブルを削除し、再度追加します。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] により、 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)内のデータを<xref:System.Data.DataSet>オブジェクト。 詳細については、「[LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: データセット デザイナーでデータセットを作成します。](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [チュートリアル: 複数のクエリによる TableAdapter の作成](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [チュートリアル: データセット デザイナーでの DataTable の作成](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [チュートリアル: データ テーブル間のリレーションシップの作成](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [[データ ソース] ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)