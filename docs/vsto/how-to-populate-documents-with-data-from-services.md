---
title: '方法: サービスからデータをドキュメントに読み込む'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: e935501e2e38c7e6c3abdb1c16e351342cf52a8a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838295"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>方法: サービスからデータをドキュメントに読み込む

Microsoft Office のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトと同じ方法でデータにアクセスできます。 同じツールとコードを使用してソリューションにデータを取り込むことができ、Windows フォーム コントロールを使用してデータを表示できます。 さらに、ホスト コントロールと呼ばれるコントロールを利用できます。これは、Microsoft Office Excel および Microsoft Office Word のネイティブ オブジェクトであり、イベントやデータ バインディング機能が強化されています。 詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

次の例は、デザイン時にドキュメントにデータ バインド コントロールを追加する方法を示しています。 VSTO アドインにおける実行時にデータ バインド コントロールを追加する方法の例は、次を参照してください。[チュートリアル。VSTO アドイン プロジェクトでサービスからのデータにバインド](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md)します。

![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How do i:。Microsoft Excel から web サービスと対話しますか。](http://go.microsoft.com/fwlink/?LinkID=130284).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Web サービスからデータをドキュメント レベルのプロジェクトを設定するには

1.  **[データ ソース]** ウィンドウを開き、プロジェクトのサービス データ ソースを作成します。 詳細については、「[新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)」を参照してください。

2.  目的のテーブルまたはフィールドを **[データ ソース]** ウィンドウからドキュメントまでドラッグします。

     コントロールがドキュメント内に作成され、 <xref:System.Windows.Forms.BindingSource> が作成されてプロジェクト内のオブジェクトのクラスにバインドされ、サービスのクラスが生成されます。

3.  コードでは、手順 1 で接続する web サービス クラスのインスタンスを作成します。

4.  Web サービスとの通信に必要なプロパティがある場合は、これらのプロパティのインスタンスを作成します。

5.  Web サービスが公開しているメソッドと、手順 4 で作成したプロパティ インスタンスを使用し、データ要求を作成して送信します。

     使用する方法は、web サービスの提供に依存します。

6.  Web サービスからデータ応答を割り当てる、<xref:System.Windows.Forms.BindingSource.DataSource%2A>のプロパティ、<xref:System.Windows.Forms.BindingSource>します。

プロジェクトを実行すると、データ ソースの先頭のレコードがコントロールに表示されます。 レコードのスクロールを有効にするには、 <xref:System.Windows.Forms.BindingSource>のオブジェクトを使用して通貨のイベントを処理します。

## <a name="see-also"></a>関連項目

- [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)
- [新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)
- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [方法: データベースからデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [方法: ホスト コントロールからのデータでデータ ソースを更新します。](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)