---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
タイトル:"をデータ バインド Windows フォーム コントロール |Microsoft ドキュメント"ms.custom:""ms.date::「11/04/2016」ms.reviewer:""ms.suite:""ms.tgt_pltfrm:""ms.topic:: helpviewer_keywords を「記事」。 
  - 「Windows フォーム コントロールのデータを表示するには、」
  - 「Windows フォーム、データを表示する」
  - 「データ ソースを表示する」
  - 「データ [Windows フォーム]、表示する」ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision: 28 作成者:"gewarren"ms.author:"gewarren"マネージャー: ghogen ms.technology::「vs データ ツール」
---
# <a name="bind-windows-forms-controls-to-data"></a>Windows フォーム コントロールをデータにバインドします。
オブジェクトをドラッグしてコントロールをデータ ソースをバインドすることができます、**データソース**ウィンドウまたはフォーム上の既存のコントロール上に Windows フォームにします。 項目をドラッグすると、前にバインドするコントロールの種類を設定することができます。 自体、または個々 の列にテーブルを選択するかどうかに応じて異なる値が表示されます。  カスタム値を設定することもできます。 表については、"Details"は各列が個別のコントロールにバインドされていることを意味します。  

![データ ソースをバインドする DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "DataGridView を raddata バインド データ ソース")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>DataGridView コントロール内のデータにバインドします。  
DataGridView でのテーブル全体は、その 1 つのコントロールにバインドされます。 レコードを移動するためのツールがストリップ DataGridView をフォームにドラッグすると、(<xref:System.Windows.Forms.BindingNavigator>) も表示されます。 A[データセット](../data-tools/dataset-tools-in-visual-studio.md)、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。 次の図では、Customers テーブルには、Orders テーブルにリレーションシップが含まれているために場合にも、TableAdapterManager が追加されます。 これらの変数は、すべての自動生成されたコードとして宣言フォーム クラスのプライベート メンバー。 DataGridView を塗りつぶすときの自動生成されたコードは、form_load イベント ハンドラーに格納されます。 データベースを更新するデータを保存するためのコードは、BindingNavigator の保存のイベント ハンドラーに格納されます。 移動したり、必要に応じてこのコードを変更することができます。  
  
 ![BindingNavigator GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata BindingNavigator GridView")  
  
 それぞれの右上隅のスマート タグをクリックして、DataGridView コントロールと BindingNavigator の動作をカスタマイズできます。  
  
 ![DataGridView コントロールとバインドのナビゲーターのスマート タグ](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView とバインドのナビゲーターのスマート タグ")  
  
 コントロール、アプリケーションが必要がない場合内から使用可能、**データ ソース**ウィンドウ、コントロールを追加することができます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)です。  
  
 項目をドラッグすることも、**データ ソース**ウィンドウからコントロールをデータにバインドするためのフォームにコントロールにします。 データに既にバインドされているコントロールには、そのデータを最も最近ドラッグされた項目にバインドがリセットがあります。 有効なドロップ ターゲットにするのには、コントロールを基になるのデータ型からの上にドラッグした項目を表示することにする必要があります、**データソース**ウィンドウです。 たとえば、これが無効のデータ型を持つ項目をドラッグし<xref:System.DateTime>上に、<xref:System.Windows.Forms.CheckBox>であるため、<xref:System.Windows.Forms.CheckBox>日付を表示することはできません。  
  
## <a name="bind-to--data-in-individual-controls"></a>個々 のコントロールにデータにバインドします。  
 「詳細」をデータ ソースをバインドすると、データセット内の各列は個別のコントロールにバインドされます。  
  
 ![詳細をデータ ソースをバインド](../data-tools/media/raddata-bind-data-source-to-details.png "raddata バインド データ ソースの詳細")  
  
> [!IMPORTANT]
>  前の図に、Orders テーブルからではなく、Customers テーブルの注文プロパティからドラッグしてください。 Customer.Orders プロパティへのバインド、によって、DataGridView に加えられたナビゲーション コマンドに直ちに反映されます詳細コントロール。 Orders テーブルからドラッグした場合、データセットに、コントロールをバインドする、まだけれども、これらがないと同期できません DataGridView  
  
 次の図はで、既定値に、Customers テーブルに注文プロパティを「詳細」をバインドした後に、フォームに追加のデータ バインド コントロールを示します、**データソース**ウィンドウです。  
  
 ![Orders テーブルの詳細にバインドされて](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders テーブルの詳細にバインド")  
  
 各コントロールがスマート タグを持つことにも注意してください。 このタグは、そのコントロールのみに適用されるカスタマイズを使用できます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)