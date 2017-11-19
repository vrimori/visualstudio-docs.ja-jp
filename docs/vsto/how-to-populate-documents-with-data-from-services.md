---
title: "方法: サービスからデータをドキュメントに読み込む |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd71e73d205fb79199cb2b8847a856c97272b066
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-documents-with-data-from-services"></a>方法 : サービスのデータをドキュメントに読み込む
  Microsoft Office のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトと同じ方法でデータにアクセスできます。 同じツールとコードを使用してソリューションにデータを取り込むことができ、Windows フォーム コントロールを使用してデータを表示できます。 さらに、ホスト コントロールと呼ばれるコントロールを利用できます。これは、Microsoft Office Excel および Microsoft Office Word のネイティブ オブジェクトであり、イベントやデータ バインディング機能が強化されています。 詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 次の例は、デザイン時にドキュメントにデータ バインド コントロールを追加する方法を示しています。 実行時に VSTO アドインでのデータ バインド コントロールを追加する方法の例は、次を参照してください。[チュートリアル: VSTO でのサービスからのデータへのバインディングのアドイン プロジェクト](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md)です。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法は i: と対話する Microsoft Excel からの Web サービス?](http://go.microsoft.com/fwlink/?LinkID=130284)です。  
  
### <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Web サービスからドキュメント レベルのプロジェクトにデータを読み込むには  
  
1.  **[データ ソース]** ウィンドウを開き、プロジェクトのサービス データ ソースを作成します。 詳細については、「[新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)」を参照してください。  
  
2.  目的のテーブルまたはフィールドを **[データ ソース]** ウィンドウからドキュメントまでドラッグします。  
  
     コントロールがドキュメント内に作成され、 <xref:System.Windows.Forms.BindingSource> が作成されてプロジェクト内のオブジェクトのクラスにバインドされ、サービスのクラスが生成されます。  
  
3.  手順 1 で接続した Web サービス クラスのインスタンスをコード内に作成します。  
  
4.  Web サービスとの通信に必要なプロパティがある場合は、それらのプロパティのインスタンスを作成します。  
  
5.  Web サービスが公開しているメソッドと、手順 4 で作成したプロパティ インスタンスを使用し、データ要求を作成して送信します。  
  
     使用するメソッドは、Web サービスが提供する内容によって異なります。  
  
6.  Web サービスからのデータ応答を、 <xref:System.Windows.Forms.BindingSource.DataSource%2A> の <xref:System.Windows.Forms.BindingSource>プロパティに割り当てます。  
  
 プロジェクトを実行すると、データ ソースの先頭のレコードがコントロールに表示されます。 レコードのスクロールを有効にするには、 <xref:System.Windows.Forms.BindingSource>のオブジェクトを使用して通貨のイベントを処理します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [新しいデータ ソースを追加します。](/visualstudio/data-tools/add-new-data-sources)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [方法: データベースからデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法: ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  