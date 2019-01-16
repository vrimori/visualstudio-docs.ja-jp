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
ms.workload:
- data-storage
ms.openlocfilehash: 38ed283a70716f0f282bdcdf60c18f0f38fc8bb2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822162"
---
# <a name="create-relationships-between-datasets"></a>データセット間にリレーションシップを作成する
関連データを含むデータセット テーブルを使用して<xref:System.Data.DataRelation>を 1 つ別の関連レコードを返すと、テーブル間の親/子リレーションシップを表すオブジェクト。 使用してデータセットの関連テーブルの追加、**データ ソース構成ウィザード**、または**データセット デザイナー**を作成し、構成、<xref:System.Data.DataRelation>オブジェクト。

<xref:System.Data.DataRelation>オブジェクトが 2 つの関数を実行します。

-   利用できるように使用しているレコードに関連するレコード。 親レコードの場合は、子レコードを提供します (<xref:System.Data.DataRow.GetChildRows%2A>) と子レコードを使用している場合は、親レコード (<xref:System.Data.DataRow.GetParentRow%2A>)。

-   親レコードを削除すると、関連する子レコードの削除などの参照整合性制約を適用します。

True の結合との関数の違いを理解することが重要な<xref:System.Data.DataRelation>オブジェクト。 真の結合レコードが親と子テーブルから取得され、フラットで 1 つのレコード セットに配置。 使用すると、<xref:System.Data.DataRelation>オブジェクトの新しいレコード セットは作成されません。 代わりに、datarelation を使用では、テーブル間の関係を追跡し、親と子レコードの同期を保ちます。

## <a name="datarelation-objects-and-constraints"></a>DataRelation オブジェクトと制約
A<xref:System.Data.DataRelation>オブジェクトは作成して、次の制約の適用にも使用されます。

-   Unique 制約をテーブルの列に重複が含まれないことが保証されます。

-   データセット内の親と子テーブル間に参照整合性を維持するために使用できる foreign key 制約。

指定した制約を<xref:System.Data.DataRelation>オブジェクトが自動的に適切なオブジェクトを作成するか、プロパティを設定して実装されます。 使用して foreign key 制約を作成するかどうか、<xref:System.Data.DataRelation>オブジェクト、インスタンスの<xref:System.Data.ForeignKeyConstraint>クラスに追加されて、<xref:System.Data.DataRelation>オブジェクトの<xref:System.Data.DataRelation.ChildKeyConstraint%2A>プロパティ。

Unique 制約が実装されているいずれかを設定するだけで、<xref:System.Data.DataColumn.Unique%2A>するデータ列のプロパティ`true`またはのインスタンスを追加することで、<xref:System.Data.UniqueConstraint>クラスを<xref:System.Data.DataRelation>オブジェクトの<xref:System.Data.DataRelation.ParentKeyConstraint%2A>プロパティ。 データセット内の制約を中断する方法の詳細については、次を参照してください。[データセットの読み込み中に制約を無効に](../data-tools/turn-off-constraints-while-filling-a-dataset.md)します。

### <a name="referential-integrity-rules"></a>参照整合性の規則
Foreign key 制約の一部として、次の 3 つの時点で適用される参照整合性規則を指定できます。

-   親レコードが更新されたとき

-   親レコードが削除されたとき

-   変更が受け入れられるか拒否されます。

行うことができる規則が指定されて、<xref:System.Data.Rule>列挙およびは次の表に記載します。

|外部キー制約の規則|アクション|
| - |------------|
|<xref:System.Data.Rule.Cascade>|親レコードに加えられた変更 (更新または削除) は、子テーブル内の関連レコードでも作成します。|
|<xref:System.Data.Rule.SetNull>|子レコードは削除されませんが、子レコードの外部キーに設定されて<xref:System.DBNull>します。 この設定では、子レコードを「孤立」のまま残してかまいません: 親レコードとの関係あるありませんは、します。 **注:** このルールを使用すると、子テーブル内の無効なデータがあります。|
|<xref:System.Data.Rule.SetDefault>|関連する子レコードの外部キーが既定値に設定 (列のによって確立されると、<xref:System.Data.DataColumn.DefaultValue%2A>プロパティ)。|
|<xref:System.Data.Rule.None>|関連する子レコードは変更されません。 この設定では、子レコードが無効な親レコードへの参照を含めることができます。|

データセットのテーブルで更新プログラムの詳細については、次を参照してください。[データをデータベースに保存](../data-tools/save-data-back-to-the-database.md)します。

### <a name="constraint-only-relations"></a>制約だけのリレーションシップ
作成するときに、<xref:System.Data.DataRelation>オブジェクトの制約を適用するだけの関係を使用するように指定するオプションがあります: つまり、これはも使用されません関連レコードにアクセスします。 このオプションを使用すると、若干効率的ですが、関連レコードの機能よりも少ないメソッドを含むデータセットを生成します。 ただし、関連するレコードにアクセスすることはできません。 たとえば、制約のみのリレーションシップと子レコードを保持している親レコードを削除するできなくなり、親を子レコードにアクセスすることはできません。

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>データセット デザイナーで、データのリレーションシップを手動で作成します。
Visual Studio で、データ デザイン ツールを使用して、データ テーブルを作成するときにリレーションシップが自動的に作成、データのソースから情報を収集できます。 データ テーブルを手動で追加する場合、**データセット**のタブ、**ツールボックス**リレーションシップを手動で作成する必要があります。 詳細については<xref:System.Data.DataRelation>オブジェクトはプログラムを参照してください[Datarelation の追加](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)します。

内の行として表示されるデータ テーブル間のリレーションシップ、**データセット デザイナー**リレーションシップの一対多の縦横比を表すキーと無限のグリフ。 既定では、リレーションシップの名前は、デザイン サーフェイスは表示されません。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>2 つのデータ テーブル間のリレーションシップを作成するには

1.  **データセット デザイナー**でご自分のデータセットを開きます。 詳細については、「[チュートリアル:データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)します。

2.  ドラッグ、**関係**オブジェクトから、**データセット**ツールボックス リレーションシップの子のデータ テーブル。

     **関係** ダイアログ ボックスが開き、設定、**子テーブル**ボックスにドラッグしたテーブル、**関係**オブジェクトします。

3.  親テーブルから選択、**親テーブル**ボックス。 親テーブルには、一対多リレーションシップの「一」側にあるレコードが含まれています。

4.  適切な子テーブルが表示されていることを確認、**子テーブル**ボックス。 子テーブルには、一対多リレーションシップの「多」側にあるレコードが含まれています。

5.  リレーションシップの名前を入力、**名前**ボックス、または、選択したテーブルに基づく既定の名前のままにします。 これは、実際の名前<xref:System.Data.DataRelation>コード内のオブジェクト。

6.  内のテーブルを結合する列を選択して、**キー列**と**外部キー列を**を一覧表示します。

7.  リレーションシップ、制約、またはその両方を作成するかどうかを選択します。

8.  オンまたはオフ、**入れ子になったリレーションシップ**ボックス。 このオプションの設定を選択すると、<xref:System.Data.DataRelation.Nested%2A>プロパティを`true`と、行が親列内で入れ子になったこれらの行の XML データとして書き込まれるまたはとの同期とのリレーションシップの子をその<xref:System.Xml.XmlDataDocument>します。 詳細については、次を参照してください。 [Datarelation の入れ子](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations)します。

9. これらのテーブル内のレコードに変更を加えていない場合に適用する規則を設定します。 詳細については、「<xref:System.Data.Rule>」を参照してください。

10. クリックして**OK**リレーションシップを作成します。 リレーションシップの線は、2 つのテーブル デザイナーに表示されます。

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>データセット デザイナーでリレーションシップ名を表示するには

1.  **データセット デザイナー**でご自分のデータセットを開きます。 詳細については、「[チュートリアル:データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)します。

2.  **データ**メニューの 、**リレーションシップ ラベルを表示する**リレーションシップ名を表示するコマンド。 リレーションシップ名を非表示にするには、そのコマンドをオフにします。

## <a name="see-also"></a>関連項目

- [Visual Studio でデータセットを作成および構成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)