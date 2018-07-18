---
title: DataRelation を使用して、データセット間のリレーションシップを作成するには
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b3b101d251167a646b66568f7aacc005d7c792d7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927205"
---
# <a name="create-relationships-between-datasets"></a>データセット間のリレーションシップを作成します。
関連データを含むデータセット テーブルを使用して<xref:System.Data.DataRelation>をいずれかの別の関連するレコードを返すと、テーブル間の親/子リレーションシップを表すオブジェクト。 使用してデータセットの関連テーブルの追加、**データ ソース構成ウィザード**、または**データセット デザイナー**が作成され、構成、<xref:System.Data.DataRelation>オブジェクト。

<xref:System.Data.DataRelation>オブジェクトは 2 つの関数を実行します。

-   利用できるように使用しているレコードに関連するレコード。 子レコードを提供する、親レコードである場合 (<xref:System.Data.DataRow.GetChildRows%2A>) と子レコードを使用している場合は、親レコード (<xref:System.Data.DataRow.GetParentRow%2A>)。

-   親レコードを削除すると、関連する子レコードを削除するなど、参照整合性の制約を強制できます。

真の結合との機能の違いを理解することが重要な<xref:System.Data.DataRelation>オブジェクト。 真の結合レコードは親と子テーブルから取得され、フラットで 1 つのレコード セットに格納します。 使用すると、<xref:System.Data.DataRelation>オブジェクト、新しいレコード セットは作成されません。 代わりに、datarelation を使用では、テーブル間リレーションシップを追跡し、親と子レコードの同期を維持します。

## <a name="datarelation-objects-and-constraints"></a>DataRelation オブジェクトと制約
A<xref:System.Data.DataRelation>オブジェクトは作成し、次の制約を実施にも使用します。

-   Unique 制約をテーブル内の列に重複が含まれないことを保証します。

-   データセット内の親と子テーブル間に参照整合性を維持するために使用できる foreign key 制約。

指定した制約、<xref:System.Data.DataRelation>オブジェクトが自動的に適切なオブジェクトを作成するか、プロパティを設定して実装されます。 使用して foreign key 制約を作成するかどうか、<xref:System.Data.DataRelation>オブジェクト、インスタンスの<xref:System.Data.ForeignKeyConstraint>クラスに追加されて、<xref:System.Data.DataRelation>オブジェクトの<xref:System.Data.DataRelation.ChildKeyConstraint%2A>プロパティです。

Unique 制約が実装された単に設定するか、<xref:System.Data.DataColumn.Unique%2A>するデータ列のプロパティ`true`またはのインスタンスを追加することで、<xref:System.Data.UniqueConstraint>クラスを<xref:System.Data.DataRelation>オブジェクトの<xref:System.Data.DataRelation.ParentKeyConstraint%2A>プロパティです。 データセット内の制約を中断する方法の詳細については、次を参照してください。[データセットの読み込み中に制約をオフに](../data-tools/turn-off-constraints-while-filling-a-dataset.md)です。

### <a name="referential-integrity-rules"></a>参照整合性の規則
Foreign key 制約の一部として、3 つの点で適用されている参照整合性の規則を指定できます。

-   親レコードが更新されたとき

-   親レコードが削除されたとき

-   変更が受理されるか拒否されました。

指定することができます、ルール、<xref:System.Data.Rule>列挙型とは、次の表に一覧表示します。

|外部キー制約の規則|アクション|
|----------------------------------|------------|
|<xref:System.Data.Rule.Cascade>|親レコードに加えられた変更 (更新または削除) が子テーブルの関連レコードも作成されます。|
|<xref:System.Data.Rule.SetNull>|子レコードは削除されませんが、子レコード内の外部キーに設定されている<xref:System.DBNull>です。 この設定では、子レコードにしておく「孤立したもの」として、つまりがあるない親レコードとの関係。 **注:** 子テーブル内の無効なデータになりますこの規則を使用します。|
|<xref:System.Data.Rule.SetDefault>|既定値に関連する子レコードの外部キーを設定 (列のによって設定される<xref:System.Data.DataColumn.DefaultValue%2A>プロパティ)。|
|<xref:System.Data.Rule.None>|関連する子レコードは変更されません。 この設定は、子レコードは無効な親レコードへの参照を含めることができます。|

データセット テーブルで更新プログラムの詳細については、次を参照してください。[データをデータベースに保存](../data-tools/save-data-back-to-the-database.md)です。

### <a name="constraint-only-relations"></a>制約だけのリレーションシップ
作成するときに、<xref:System.Data.DataRelation>オブジェクトの制約を強制するだけの関係を使用することを指定するオプションがある-つまり、これはも使用されません関連レコードにアクセスします。 このオプションを使用すると、やや効率的であるし、関連レコードの機能よりも少数のメソッドを格納しているデータセットを生成します。 ただし、関連するレコードにアクセスすることはできません。 たとえば、制約のみのリレーションシップと子レコードを保持している親レコードを削除できなくなり、親を子レコードにアクセスすることはできません。

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>データセット デザイナーで、データのリレーションシップを手動で作成します。
Visual Studio でデータ デザイン ツールを使用してデータ テーブルを作成するときにリレーションシップが自動的に作成場合は、データのソースから情報を収集することができます。 データ テーブルを手動で追加する場合、**データセット**のタブ、**ツールボックス**リレーションシップを手動で作成する必要があります。 作成する方法について<xref:System.Data.DataRelation>オブジェクトはプログラムを参照してください[Datarelation の追加](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)です。

内の行として表示されるデータ テーブル間のリレーションシップ、**データセット デザイナー**リレーションシップの一対多の側面を表すキーと無限大グリフがあります。 既定では、リレーションシップの名前は、デザイン サーフェイスは表示されません。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>2 つのデータ テーブル間のリレーションシップを作成するには

1.  データセットを開き、**データセット デザイナー**です。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)です。

2.  ドラッグ、**関係**オブジェクトから、**データセット**ツールボックスからリレーションシップの子のデータ テーブルにします。

     **関係** ダイアログ ボックスが開き、作成、**子テーブル**ボックスにドラッグしたテーブル、**関係**上にオブジェクトします。

3.  親テーブルからを選択して、**親テーブル**ボックス。 親テーブルには、一対多リレーションシップの「一」側のレコードが含まれています。

4.  適切な子テーブルが表示されることを確認してください、**子テーブル**ボックス。 子テーブルには、一対多リレーションシップの「多」側にあるレコードが含まれています。

5.  リレーションシップの名前を入力、**名前**ボックス、または、選択したテーブルに基づく既定の名前のままにします。 これは、実際の名前<xref:System.Data.DataRelation>コード内のオブジェクト。

6.  内のテーブルを結合する列を選択して、**キー列**と**外部キー列**を一覧表示します。

7.  リレーションシップ、制約、またはその両方を作成するかどうかを選択します。

8.  オンまたはオフにして、**入れ子になったリレーションシップ**ボックス。 このオプションは設定を選択すると、<xref:System.Data.DataRelation.Nested%2A>プロパティを`true`と、これらの行の XML データとして書き込まれるまたはと同期されているときに、親列内で入れ子にするリレーションシップの行を子その<xref:System.Xml.XmlDataDocument>です。 詳細については、次を参照してください。 [Datarelation の入れ子](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations)です。

9. これらのテーブル内のレコードを変更しているときに適用する規則を設定します。 詳細については、「<xref:System.Data.Rule>」を参照してください。

10. をクリックして**OK**リレーションシップを作成します。 リレーションシップの線は、2 つのテーブル デザイナーに表示されます。

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>データセット デザイナーでリレーションシップ名を表示するには

1.  データセットを開き、**データセット デザイナー**です。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)です。

2.  **データ**メニューの 、**リレーションシップ ラベルを表示する**リレーションシップ名を表示するコマンド。 リレーションシップ名を非表示にするには、そのコマンドをオフにします。

## <a name="see-also"></a>関連項目

- [Visual Studio でデータセットを作成および構成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)