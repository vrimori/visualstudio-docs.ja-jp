---
title: Windows フォーム アプリケーションでルックアップ テーブルを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 75035b12972299c0c9d4b9b515cb4cbd51308739
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows フォーム アプリケーションでルックアップ テーブルを作成します。
用語*ルックアップ テーブル*2 つの関連するデータ テーブルにバインドされているコントロールについて説明します。 この検索コントロールは、2 番目のテーブルで選択されている値に基づいて最初のテーブルからデータを表示します。  
  
 親テーブルの主ノードをドラッグして、ルックアップ テーブルを作成することができます (から、[データ ソース ウィンドウ](add-new-data-sources.md)) に関連する子テーブル内の列に既にバインドされている、フォーム上のコントロールです。  
  
 たとえば、販売データベースの `Orders` テーブルであれば、次のように使用されます。 内の各レコード、`Orders`テーブルが含まれています、 `CustomerID`、どの顧客が注文を示すです。 `CustomerID` は、`Customers` テーブルの顧客レコードを指す外部キーです。 このシナリオでは、拡張、`Orders`テーブルに、**データ ソース**ウィンドウにメインのノードを設定および**詳細**です。 設定して、`CustomerID`列を使用して、 <xref:System.Windows.Forms.ComboBox> (または検索バインドをサポートするその他のコントロール)、ドラッグ、`Orders`フォーム上にノードです。 最後に、ドラッグ、`Customers`ノードに関連する列にバインドされているコントロールに、ここでは、<xref:System.Windows.Forms.ComboBox>にバインドされている、`CustomerID`列です。  
  
## <a name="to-databind-a-lookup-control"></a>検索コントロールをデータバインドするには  
  
1.  開く、**データソース**ウィンドウです。  
  
    > [!NOTE]
    >  ルックアップ テーブルでは、2 つの関連するテーブルまたはオブジェクトがで使用できることが必要、**データソース**ウィンドウです。 詳細については、次を参照してください。[データセットのリレーションシップ](relationships-in-datasets.md)です。  
  
2.  内のノードを展開し、**データソース**ウィンドウが表示されるまで、親テーブルとすべての列、および関連する子テーブルとそのすべての列です。  
  
    > [!NOTE]
    >  子テーブルのノードは、展開可能な子ノードとして親テーブルに表示されます。  
  
3.  子テーブルのドロップ タイプを変更**詳細**を選択して**詳細**コントロールの一覧から、子テーブルのノードです。 詳細については、次を参照してください。[セットのデータ ソース ウィンドウからドラッグしたときに作成する制御](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)です。  
  
4.  2 つのテーブルを関連ノードを見つけます (、`CustomerID`前の例でのノード)。ドロップ タイプを変更、<xref:System.Windows.Forms.ComboBox>を選択して**ComboBox**コントロール リストからです。  
  
5.  主要な子テーブル ノードをドラッグして、**データ ソース**ウィンドウからフォームにします。  
  
     説明のラベルが付いたデータ バインド コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A[データセット](../data-tools/dataset-tools-in-visual-studio.md)、 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。  
  
6.  ここで、メインの親テーブルからノードをドラッグ、**データソース**検索コントロールに直接ウィンドウ (、 <xref:System.Windows.Forms.ComboBox>)。  
  
     これで検索バインドが確立されます。 コントロールに設定された個々のプロパティについては、次の表を参照してください。  
  
    |プロパティ|設定の説明|  
    |--------------|----------------------------|  
    |**DataSource**|Visual Studio は、このプロパティをコントロールにドラッグしたテーブルに対して作成された <xref:System.Windows.Forms.BindingSource> に設定します (コントロールの作成時に作成された <xref:System.Windows.Forms.BindingSource> とは異なります)。<br /><br /> 調整する必要がある場合は、これを表示する列を含むテーブルの <xref:System.Windows.Forms.BindingSource> に設定します。|  
    |**DisplayMember**|Visual Studio は、このプロパティをコントロールにドラッグするテーブルの主キーの後で、文字列データ型を含む最初の列に設定します。<br /><br /> 調整する必要がある場合は、これを表示する列の名前に設定します。|  
    |**ValueMember**|Visual Studio は、このプロパティを主キーに参加している最初の列、またはキーが定義されていない場合は、テーブルの最初の列に設定します。<br /><br /> 調整する必要がある場合は、これを表示する列を含むテーブルの主キーに設定します。|  
    |**SelectedValue**|Visual Studio では、このプロパティを設定からドロップした元の列に、**データソース**ウィンドウです。<br /><br /> 調整する必要がある場合は、これを関連付けられたテーブルの外部キー列に設定します。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)