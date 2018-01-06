---
title: "方法: データベースからデータをワークシートに読み込む |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6efeccfdaa6b3377869fb20f9c66613960529daf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>方法 : データベースのデータをワークシートに読み込む
  Windows フォーム プロジェクトでのデータにアクセスすることと同様にドキュメント レベルの Office プロジェクトでのデータにアクセスすることができます。 同じツールとコードを使用してソリューションにデータを取り込むことができ、Windows フォーム コントロールを使用してデータを表示できます。 さらに、利用では、ホスト コントロールは、イベントやデータ バインディング機能が強化された Microsoft Office excel のネイティブのオブジェクトと呼ばれるようです。 詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 次の例は、デザイナーを使用してドキュメント レベルのプロジェクトにデータ バインド コントロールを追加する方法を示しています。 実行時にアプリケーション レベルのプロジェクトでのデータ バインド コントロールを追加する方法の例は、次を参照してください。[チュートリアル: VSTO での複合データ バインディング アドイン プロジェクト](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)です。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法は i: 転送データに、Excel ワークシート?](http://go.microsoft.com/fwlink/?LinkID=130277)、および[操作方法: 使用するデータベース データ Excel で?](http://go.microsoft.com/fwlink/?LinkID=130287)です。  
  
## <a name="adding-a-data-bound-control-to-a-worksheet-at-design-time"></a>デザイン時にワークシートにデータ バインド コントロールを追加します。  
  
#### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>データベースからデータを含むワークシートを作成するには  
  
1.  デザイナーでワークシートを開き、Visual Studio で Excel ドキュメント レベルのプロジェクトを開きます。  
  
2.  **[データ ソース]** ウィンドウを開いて、プロジェクトのデータ ソースを作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)です。  
  
3.  フィールドまたはから対象とするテーブルをドラッグして、**データソース**をワークシートにウィンドウです。  
  
 次のコントロールの 1 つは、ワークシートに作成されます。  
  
-   フィールドをドラッグする場合、<xref:Microsoft.Office.Tools.Excel.NamedRange>ワークシートにコントロールを作成します。 詳細については、次を参照してください。 [NamedRange コントロール](../vsto/namedrange-control.md)です。  
  
-   テーブルをドラッグする場合、<xref:Microsoft.Office.Tools.Excel.ListObject>ワークシートにコントロールを作成します。 詳細については、「 [ListObject Control](../vsto/listobject-control.md)」を参照してください。  
  
 テーブルを選択して別のコントロールを追加したり、フィールドに、**データソース**ウィンドウとドロップダウン リストから別のコントロールを選択します。  
  
## <a name="objects-in-the-project"></a>プロジェクト内のオブジェクト  
 プロジェクトには、コントロールに加えて、データに関連する以下のオブジェクトも自動的に追加されます。  
  
-   データベース内の接続したデータ テーブルをカプセル化する型指定されたデータセット。 詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](/visualstudio/data-tools/dataset-tools-in-visual-studio)です。  
  
-   コントロールを型指定されたデータセットに接続する <xref:System.Windows.Forms.BindingSource>。 詳細については、「 [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview)」を参照してください。  
  
-   型指定されたデータセットをデータベースに接続する TableAdapter。 詳細については、「 [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)」を参照してください。  
  
-   TableAdapterManager、階層更新を有効にする、データセット内のテーブル アダプターを調整するために使用します。 詳細については、次を参照してください。[階層更新](../data-tools/hierarchical-update.md)と[TableAdapterManager 参照](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)です。  
  
 プロジェクトを実行すると、データ ソースの先頭のレコードがコントロールに表示されます。 <xref:System.Windows.Forms.BindingSource> を使用すると、ユーザーがレコードをスクロールできるようになります。  
  
#### <a name="to-scroll-through-the-records"></a>レコードをスクロールするには  
  
-   <xref:System.Windows.Forms.BindingSource.MoveNext%2A> や <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> など、<xref:System.Windows.Forms.BindingSource> のメソッドを使用します。  
  
 型指定されたデータセットと、データベースに更新を送信する方法については、次を参照してください。[する方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)です。  
  
## <a name="see-also"></a>参照  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [新しいデータ ソースを追加します。](/visualstudio/data-tools/add-new-data-sources)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法: サービスからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [方法は i: 転送データを Excel ワークシートに](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [I: での Excel でデータベースのデータの使用方法](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  