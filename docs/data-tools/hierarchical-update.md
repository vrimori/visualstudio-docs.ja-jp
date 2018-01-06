---
title: "階層更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b02ef945136297287d18c2b29ea2d3afab1b3683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hierarchical-update"></a>階層更新
*階層更新*参照整合性を維持しながらをデータベースに戻す (2 つ以上の関連するテーブルを含むデータセット) から更新されたデータを保存するプロセスを指します。 *参照整合性*はデータベース内の挿入、更新、および関連するレコードの削除の動作を制御する制約によって定義される一貫性規則を参照します。 たとえば、その顧客の注文を作成できないを許可する前に、顧客レコードの作成を強制する参照整合性を勧めします。  データセットのリレーションシップの詳細については、次を参照してください[データセットのリレーションシップ。](../data-tools/relationships-in-datasets.md)  
  
 階層更新機能を使用して、`TableAdapterManager`を管理する、`TableAdapter`に型指定された dataset の s。 `TableAdapterManager`コンポーネントは、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-されないようにするために生成されたクラスの一部、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。 データ ソース ウィンドウから Windows フォームや WPF ページにテーブルをドラッグするときに、Visual Studio は、フォームまたはページで、TableAdapterManager の型の変数を追加し、コンポーネント トレイに、デザイナーに表示します。 詳細については、`TableAdapterManager`クラスの TableAdapterManager リファレンスのセクションを参照してください[Tableadapter](../data-tools/create-and-configure-tableadapters.md)です。  
  
 既定では、データセットは、外部キー制約を適用しないことを意味する「リレーションのみ、」として関連テーブルを扱います。 データセット デザイナーを使用して、デザイン時にその設定を変更できます。 呼び出すことの 2 つのテーブル間のリレーションの行を選択、**関係** ダイアログ ボックス。 TableAdapterManager の動作時に、ここで変更したが決定がデータベースに関連するテーブルに、変更も送信します。  
  
## <a name="enable-hierarchical-update-in-a-dataset"></a>データセット内の階層の更新を有効にします。  
 プロジェクトで追加または作成されたすべての新しいデータセットでは、階層更新が既定で有効になっています。 階層更新をオンまたはオフを設定して、**階層更新**データセットで指定されたデータセットのプロパティ**True**または**False**:  
  
 ![階層更新設定](../data-tools/media/hierarchical-update-setting.png "階層的な更新プログラムの設定")  
  
## <a name="create-a-new-relation-between-tables"></a>テーブル間に新しいリレーションシップを作成します。  
 2 つのテーブル間に新しいリレーションシップを作成する、データセット デザイナーで各テーブルのタイトル バーを選択を右クリックし、選択**関係の追加**です。  
  
 ![階層更新の追加リレーションシップ メニュー](../data-tools/media/hierarchical-update-add-relation-menu.png "階層更新 メニューの関係を追加します。")  
  
## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Foreign key 制約、カスケード更新、および削除を理解します。  
 どの foreign key 制約を理解することが重要と、生成されたデータセット コードで作成されるデータベースの連鎖動作します。  
  
 既定では、データセットのデータ テーブルは、データベースでのリレーションシップと一致するリレーションシップ (<xref:System.Data.DataRelation>) が設定された状態で生成されます。 ただし、データセットでのリレーションシップは、外部キー制約としては生成されません。 <xref:System.Data.DataRelation>として構成されて**関係だけ**せず<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>または<xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>有効にします。  
  
 連鎖更新と連鎖削除は、データベースのリレーションシップで連鎖更新や連鎖削除が有効になっている場合でも、既定で無効になっています。 たとえば、新しい顧客と新しい注文を作成し、データを保存しようは、データベースで定義されている外部キー制約で、競合を発生することができます。 詳細については、次を参照してください。[データセットの読み込み中に制約をオフに](turn-off-constraints-while-filling-a-dataset.md)です。  
  
## <a name="set-the-order-to-perform-updates"></a>更新プログラムを実行する順序を設定します。  
 更新を実行する順序を設定するデータセットのすべてのテーブルで変更されたすべてのデータを保存する、個々 の注文を挿入、更新、および削除したセットが必要です。 階層更新を有効にすると、挿入が最初に、実行し、更新、およびが削除されます。 `TableAdapterManager`提供、`UpdateOrder`プロパティに最初に、更新プログラムを実行し、挿入、および削除があります。  
  
> [!NOTE]
>  更新順序はすべてを含んでいることを理解しておく必要があります。 つまり、更新プログラムが実行されると、挿入、および、削除は、データセット内のすべてのテーブルに対して実行されます。  
  
 設定する、`UpdateOrder`から項目をドラッグした後、プロパティ、[データ ソース ウィンドウ](add-new-data-sources.md)、フォームに次のように選択します、`TableAdapterManager`コンポーネント トレイ、および設定で、`UpdateOrder`プロパティに、 **のプロパティ。**ウィンドウです。 
  
## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>階層更新を実行する前に、データセットのバックアップ コピーを作成します。  
 データを保存すると (`TableAdapterManager.UpdateAll()` メソッドを呼び出すことにより)、`TableAdapterManager` は単一のトランザクションで各テーブルのデータの更新を試みます。 任意のテーブルの更新時に、なんらかが失敗した場合、トランザクション全体がロールバックされます。 ほとんどの状況では、ロールバックは、元の状態をアプリケーションを返します。  
  
 ただし、バックアップ コピーからデータセットを復元することもできます。 一例は、自動インクリメント値を使用しているときに発生する可能性があります。 たとえば、保存操作が成功しなかった、データセットの自動インクリメント値はリセットされませんし、データセットを自動インクリメント値を作成します。これにより、アプリケーションで許容されることができない可能性がある番号の途切れが残ります。 これが問題となる状況では、`TableAdapterManager` に備わっている `BackupDataSetBeforeUpdate` プロパティを使用して、トランザクションが失敗した場合に既存のデータセットをバックアップ コピーと置き換えることができます。  
  
> [!NOTE]
>  バックアップ コピーは、中にメモリ内にのみ、`TableAdapterManager.UpdateAll`メソッドが実行されています。 したがってはこのバックアップ データセットにプログラムでアクセス元のデータセットを置き換えるかがスコープ外に出るためとすぐに、`TableAdapterManager.UpdateAll`メソッドの実行が完了します。  
  
## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>階層更新を実行するコードを保存、生成された変更します。  
 データセットでの関連データ テーブルへの変更をデータベースに保存するには、`TableAdapterManager.UpdateAll` メソッドを呼び出し、関連テーブルが含まれるデータセットの名前を渡します。 たとえば、NorthwindDataset 内のすべてのテーブルの更新をバックエンドのデータベースに送信するには、`TableAdapterManager.UpdateAll(NorthwindDataset)` メソッドを実行します。  
  
 項目を削除した後、**データソース**ウィンドウで、コードが自動的に追加する、`Form_Load`各テーブルを作成するイベント (、`TableAdapter.Fill`メソッド)。 コードにも追加、**保存**ボタン クリックしてイベントの<xref:System.Windows.Forms.BindingNavigator>データセットからデータベースにデータを保存する (、`TableAdapterManager.UpdateAll`メソッド)。  
  
 生成された保存コードには、`CustomersBindingSource.EndEdit` メソッドを呼び出すコード行も含まれています。 具体的には、呼び出し、<xref:System.Windows.Forms.BindingSource.EndEdit%2A>最初のメソッド<xref:System.Windows.Forms.BindingSource>ですが、フォームに追加します。 言い換えると、このコードはからドラッグされた最初のテーブルの生成のみ、**データソース**ウィンドウからフォームにします。 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼び出しは、現在編集中のデータ バインド コントロールで実行されている変更をコミットします。 そのため、データ バインド コントロールがあるフォーカス クリックして、**保存** ボタン、保留中のすべての編集コントロールは、実際の保存前にコミットされます。 その (、`TableAdapterManager.UpdateAll`メソッド)。  
  
> [!NOTE]
>  データセット デザイナーのみを追加、`BindingSource.EndEdit`フォーム上にドロップされた最初のテーブルのコード。 したがって、フォーム上の各関連テーブルに対して、`BindingSource.EndEdit` メソッドを呼び出すコード行を手動で追加する必要があります。 つまり、このチュートリアルでも、`OrdersBindingSource.EndEdit` メソッドの呼び出しを追加する必要があります。  
  
#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>保存前に、関連テーブルへの変更をコミットするコードを更新するには  
  
1.  ダブルクリックして、**保存**のボタンでは、<xref:System.Windows.Forms.BindingNavigator>を開くには**Form1**コード エディターでします。  
  
2.  `OrdersBindingSource.EndEdit` メソッドを呼び出す行の後に、`CustomersBindingSource.EndEdit` メソッドを呼び出すコード行を追加します。 内のコード、**保存**ボタンのクリック イベントは、次のようになります。  
  
     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]  
  
データベースにデータを保存する前に関連子テーブルに対する変更をコミットするだけでなく、新しい子レコードをデータセットに追加する前に、新しく作成された親レコードをコミットすることが必要な場合もあります。 つまり、外部キー制約により、新しい子レコード (Orders) をデータセットに追加する前に、データセットに新しい親レコード (Customer) を追加することが必要な場合もあります。 この操作を行うには、子 `BindingSource.AddingNew` イベントを使用します。  
  
> [!NOTE]
>  新しい親レコードをコミットする必要があるかどうかは、データ ソースにバインドするために使用されるコントロールの種類によって異なります。 このチュートリアルでは、親テーブルにバインドする個別のコントロールを使用します。 これには、新しい親レコードをコミットするコードを追加が必要です。 親レコードは、複雑なバインド コントロールで代わりに表示されていた場合と同様に、 <xref:System.Windows.Forms.DataGridView>、この追加<xref:System.Windows.Forms.BindingSource.EndEdit%2A>呼び出しの親レコードは必要ありません。 これは、コントロールの基になるデータ バインディング機能によって、新しいレコードのコミットが行われるためです。  
  
#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>データセットで新しい子レコードを追加する前に親レコードをコミットするコードを追加するには  
  
1.  `OrdersBindingSource.AddingNew` イベントのイベント ハンドラーを作成します。  
  
    -   開いている**Form1**デザイン ビューで選択**OrdersBindingSource**コンポーネント トレイに次のように選択します**イベント**で、**プロパティ**ウィンドウ、および。ダブルクリックし、 **AddingNew**イベント。  
  
2.  呼び出すイベント ハンドラーにコードの行を追加、`CustomersBindingSource.EndEdit`メソッドです。 `OrdersBindingSource_AddingNew` イベント ハンドラー内のコードは、次のようになります。  
  
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]  
  
## <a name="tableadaptermanager-reference"></a>TableAdapterManager 参照  
 既定では、`TableAdapterManager`関連テーブルを含むデータセットを作成するときに、クラスを生成します。 クラスが生成されないようにするには、値を変更、`Hierarchical Update`を false にデータセットのプロパティです。 Windows フォームや WPF ページのデザイン サーフェイスに関係のあるテーブルをドラッグすると、Visual Studio は、クラスのメンバー変数を宣言します。 データ バインドを使用しない場合は、手動で変数を宣言する必要があります。  
  
 `TableAdapterManager`クラスは、の一部、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。 そのため、ドキュメントを参照することはできません。 デザイン時に、データセットの作成プロセスの一部として作成されます。  
  
 よく使用されるメソッドとプロパティの次のとおり、`TableAdapterManager`クラス。  
  
|メンバー|説明|  
|------------|-----------------|  
|`UpdateAll` メソッド|すべてのデータ テーブルからすべてのデータを保存します。|  
|`BackUpDataSetBeforeUpdate` プロパティ|実行する前に、データセットのバックアップ コピーを作成するかどうか、`TableAdapterManager.UpdateAll`メソッドです。ブール値。|  
|*tableName* `TableAdapter`プロパティ|表す、`TableAdapter`です。 生成された`TableAdapterManager`ごとにプロパティを含む`TableAdapter`を管理します。 Customers と Orders テーブルを含むデータセットが生成など、`TableAdapterManager`を格納している`CustomersTableAdapter`と`OrdersTableAdapter`プロパティです。|  
|`UpdateOrder` プロパティ|個々 の insert、update、および delete コマンドの順序を制御します。 この設定の値のいずれかに、`TableAdapterManager.UpdateOrderOption`列挙します。<br /><br /> 既定では、`UpdateOrder`に設定されている**InsertUpdateDelete**です。 つまり、挿入し、更新、および削除しは、データセット内のすべてのテーブルに対して実行されます。|  
  
## <a name="see-also"></a>参照  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)