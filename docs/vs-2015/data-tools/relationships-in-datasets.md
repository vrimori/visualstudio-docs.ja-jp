---
title: データセットのリレーションシップ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b138b9ad49a0fd1a406e698aafd121478e95f4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935407"
---
# <a name="relationships-in-datasets"></a>データセットのリレーションシップ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
関連データを含むデータセット テーブルを使用して<xref:System.Data.DataRelation>を 1 つ別の関連レコードを返すと、テーブル間の親/子リレーションシップを表すオブジェクト。 使用してデータセットの関連テーブルの追加、**データ ソース構成ウィザード**、または**データセット デザイナー**を作成し、構成、<xref:System.Data.DataRelation>オブジェクト。  
  
 <xref:System.Data.DataRelation>オブジェクトが 2 つの関数を実行します。  
  
- 利用できるように使用しているレコードに関連するレコード。 親レコードの場合は、子レコードを提供します (<xref:System.Data.DataRow.GetChildRows%2A>) と子レコードを使用している場合は、親レコード (<xref:System.Data.DataRow.GetParentRow%2A>)。  
  
- 親レコードを削除すると、関連する子レコードの削除などの参照整合性制約を適用します。  
  
  True の結合との関数の違いを理解することが重要な<xref:System.Data.DataRelation>オブジェクト。 真の結合レコードが親と子テーブルから取得され、フラットで 1 つのレコード セットに配置。 使用すると、<xref:System.Data.DataRelation>オブジェクトの新しいレコード セットは作成されません。 代わりに、datarelation を使用では、テーブル間の関係を追跡し、親と子レコードの同期を保ちます。  
  
## <a name="datarelation-objects-and-constraints"></a>DataRelation オブジェクトと制約  
 A<xref:System.Data.DataRelation>オブジェクトは作成して、次の制約の適用にも使用されます。  
  
- Unique 制約をテーブルの列に重複が含まれないことが保証されます。  
  
- データセット内の親と子テーブル間に参照整合性を維持するために使用できる foreign key 制約。  
  
  指定した制約を<xref:System.Data.DataRelation>オブジェクトが自動的に適切なオブジェクトを作成するか、プロパティを設定して実装されます。 使用して foreign key 制約を作成するかどうか、<xref:System.Data.DataRelation>オブジェクト、インスタンスの<xref:System.Data.ForeignKeyConstraint>クラスに追加されて、<xref:System.Data.DataRelation>オブジェクトの<xref:System.Data.DataRelation.ChildKeyConstraint%2A>プロパティ。  
  
  Unique 制約が実装されているいずれかを設定するだけで、<xref:System.Data.DataColumn.Unique%2A>するデータ列のプロパティ`true`またはのインスタンスを追加することで、<xref:System.Data.UniqueConstraint>クラスを<xref:System.Data.DataRelation>オブジェクトの<xref:System.Data.DataRelation.ParentKeyConstraint%2A>プロパティ。 データセット内の制約を中断する方法の詳細については、次を参照してください。[データセットの読み込み中に制約を無効に](../data-tools/turn-off-constraints-while-filling-a-dataset.md)します。  
  
### <a name="referential-integrity-rules"></a>参照整合性の規則  
 Foreign key 制約の一部として、次の 3 つの時点で適用される参照整合性規則を指定できます。  
  
- 親レコードが更新されたとき  
  
- 親レコードが削除されたとき  
  
- 変更が受け入れられるか拒否されます。  
  
  行うことができる規則が指定されて、<xref:System.Data.Rule>列挙およびは次の表に記載します。  
  
|外部キー制約の規則|アクション|  
|----------------------------------|------------|  
|<xref:System.Data.Rule>|親レコードに加えられた変更 (更新または削除) は、子テーブル内の関連レコードでも作成します。|  
|<xref:System.Data.Rule>|子レコードは削除されませんが、子レコードの外部キーに設定されて<xref:System.DBNull>します。 この設定では、子レコードを「孤立」のまま残してかまいません: 親レコードとの関係あるありませんは、します。 **注:** 子テーブルに無効なデータによりこの規則を使用します。|  
|<xref:System.Data.Rule>|関連する子レコードの外部キーが既定値に設定 (列のによって確立されると、<xref:System.Data.DataColumn.DefaultValue%2A>プロパティ)。|  
|<xref:System.Data.Rule>|関連する子レコードは変更されません。 この設定では、子レコードが無効な親レコードへの参照を含めることができます。|  
  
 データセットのテーブルで更新プログラムの詳細については、次を参照してください。[データをデータベースに保存](../data-tools/save-data-back-to-the-database.md)します。  
  
### <a name="constraint-only-relations"></a>制約だけのリレーションシップ  
 作成するときに、<xref:System.Data.DataRelation>オブジェクトの制約を適用するだけの関係を使用するように指定するオプションがあります: つまり、これはも使用されません関連レコードにアクセスします。 このオプションを使用すると、若干効率的ですが、関連レコードの機能よりも少ないメソッドを含むデータセットを生成します。 ただし、関連するレコードにアクセスすることはできません。 たとえば、制約のみのリレーションシップと子レコードを保持している親レコードを削除するできなくなり、親を子レコードにアクセスすることはできません。  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>データセット デザイナーで、データのリレーションシップを手動で作成します。  
 Visual Studio で、データ デザイン ツールを使用して、データ テーブルを作成するときにリレーションシップが自動的に作成、データのソースから情報を収集できます。 データ テーブルを手動で追加する場合、**データセット**のタブ、**ツールボックス**リレーションシップを手動で作成する必要があります。 詳細については<xref:System.Data.DataRelation>オブジェクトはプログラムを参照してください[Datarelation の追加](http://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4)します。  
  
 内の行として表示されるデータ テーブル間のリレーションシップ、**データセット デザイナー**リレーションシップの一対多の縦横比を表すキーと無限のグリフ。 既定で relationshipCommentEnd Id の名前 = '1c8c78e19b7fa441' は、デザイン サーフェイスに表示されません。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>2 つのデータ テーブル間のリレーションシップを作成するには  
  
1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  ドラッグ、**関係**オブジェクトから、**データセット**ツールボックス リレーションシップの子のデータ テーブル。  
  
     **関係** ダイアログ ボックスが開き、設定、**子テーブル**ボックスにドラッグしたテーブル、**関係**オブジェクトします。  
  
3.  親テーブルから選択、**親テーブル**ボックス。 親テーブルには、一対多リレーションシップの「一」側にあるレコードが含まれています。  
  
4.  適切な子テーブルが表示されていることを確認、**子テーブル**ボックス。 子テーブルには、一対多リレーションシップの「多」側にあるレコードが含まれています。  
  
5.  リレーションシップの名前を入力、**名前**ボックス、または、選択したテーブルに基づく既定の名前のままにします。 これは、実際の名前<xref:System.Data.DataRelation>コード内のオブジェクト。  
  
6.  内のテーブルを結合する列を選択して、**キー列**と**外部キー列を**を一覧表示します。  
  
7.  リレーションシップ、制約、またはその両方を作成するかどうかを選択します。 詳しくは、次を参照してください。 [DataRelation オブジェクトの概要](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)します。  
  
8.  オンまたはオフ、**入れ子になったリレーションシップ**ボックス。 このオプションの設定を選択すると、<xref:System.Data.DataRelation.Nested%2A>プロパティを`true`と、行が親列内で入れ子になったこれらの行の XML データとして書き込まれるまたはとの同期とのリレーションシップの子をその<xref:System.Xml.XmlDataDocument>します。 詳細については、次を参照してください。 [Datarelation の入れ子](http://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab)します。  
  
9. これらのテーブル内のレコードに変更を加えていない場合に適用する規則を設定します。 詳細については、「 <xref:System.Data.Rule> 」を参照してください。  
  
10. クリックして**OK**リレーションシップを作成します。 リレーションシップの線は、2 つのテーブル デザイナーに表示されます。  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>データセット デザイナーでリレーションシップ名を表示するには  
  
1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  **データ**メニューの 、**リレーションシップ ラベルを表示する**リレーションシップ名を表示するコマンド。 リレーションシップ名を非表示にするには、そのコマンドをオフにします。

