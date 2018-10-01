---
title: Windows フォーム コントロールをデータにバインドします |。Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b3f454e1eb6e754327a50b22a4aefdc5e4afa0eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536986"
---
# <a name="bind-windows-forms-controls-to-data"></a>Windows フォーム コントロールをデータにバインドする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[バインド Windows フォーム コントロールのデータを](https://docs.microsoft.com/visualstudio/data-tools/bind-windows-forms-controls-to-data)します。  
  
  
オブジェクトをドラッグしてコントロールにデータ ソースをバインドすることができます、**データソース**Windows フォーム、または既存のコントロールをフォーム上のウィンドウ。 項目をドラッグする前にバインドするコントロールの種類を設定できます。 自体、または個々 の列にテーブルを選択するかどうかに応じて異なる値が表示されます。  カスタム値を設定することもできます。 テーブルの場合は、"Details"は、各列が個別のコントロールにバインドされているを意味します。  
  
 ![データ ソースをバインドする DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "DataGridView に raddata バインド データ ソース")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>DataGridView コントロールでデータをバインドします。  
 DataGridView は、テーブル全体がその 1 つのコントロールにバインドされます。 ツールがレコード間を移動のストリップをフォームに DataGridView をドラッグすると (<xref:System.Windows.Forms.BindingNavigator>) も表示されます。 A[データセット](../data-tools/dataset-tools-in-visual-studio.md)、 [TableAdapter](../data-tools/tableadapter-overview.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。 次の図に TableAdapterManager は Customers テーブルには、Orders テーブルにリレーションシップが含まれているためも追加されます。 これらの変数が宣言されたすべての自動生成されたコード フォーム クラスのプライベート メンバーとして。 DataGridView の塗りつぶしの自動生成されたコードは、form_load イベント ハンドラーにあります。 データベースを更新するデータを保存するためのコードは、BindingNavigator の保存のイベント ハンドラー内にあります。 移動したり、必要に応じてこのコードを変更します。  
  
 ![BindingNavigator を含む GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata BindingNavigator を含む GridView")  
  
 それぞれの右上隅のスマート タグをクリックして、DataGridView と BindingNavigator の動作をカスタマイズできます。  
  
 ![スマート タグの DataGridView コントロールとバインドのナビゲーター](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView とバインドのナビゲーターのスマート タグ")  
  
 コントロール、アプリケーション ニーズがない場合内から利用できる、**データソース**ウィンドウ、コントロールを追加することができます。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。  
  
 項目をドラッグすることも、**データ ソース**既にデータにコントロールをバインドするフォーム上のコントロールにウィンドウ。 データに既にバインドされているコントロールには、そのデータ バインドは、最も最近ドラッグされた項目にリセットがあります。 有効なドロップ ターゲットにするには、コントロールにから上にドラッグした項目の基になるデータ型を表示することは、**データソース**ウィンドウ。 などのデータ型を持つ項目のドラッグを有効ながない<xref:System.DateTime>上に、<xref:System.Windows.Forms.CheckBox>ため、<xref:System.Windows.Forms.CheckBox>日付を表示することはできません。  
  
## <a name="bind-to--data-in-individual-controls"></a>個々 のコントロールでデータをバインドします。  
 「詳細」をデータ ソースをバインドすると、データセット内の各列は、個別のコントロールにバインドされます。  
  
 ![データ ソースの詳細をバインド](../data-tools/media/raddata-bind-data-source-to-details.png "raddata バインド データ ソースの詳細")  
  
> [!IMPORTANT]
>  前の図に、Orders テーブルからではなく、Customers テーブルの Orders プロパティからドラッグしてください。 Customer.Orders プロパティにバインドして、DataGridView に行われたナビゲーション コマンドは詳細情報のコントロールに直ちに反映します。 Orders テーブルからドラッグした場合は、コントロールは、データセットにもバインドしますが、いないこの属性は、DataGridView と、しない同期は。  
  
 次の図はで、既定値に Customers テーブルに Orders プロパティが「詳細」をバインドした後に、フォームに追加するデータ バインド コントロールを示します、**データソース**ウィンドウ。  
  
 ![詳細を orders テーブルにバインドされている](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders テーブルの詳細にバインド")  
  
 各コントロールがスマート タグを持つことにも注意してください。 このタグは、そのコントロールのみに適用されるカスタマイズを使用できます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

