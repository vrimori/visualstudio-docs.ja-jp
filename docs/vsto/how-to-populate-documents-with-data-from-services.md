---
title: "方法 : サービスのデータをドキュメントに読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ドキュメント [Visual Studio での Office 開発]、データの読み込み"
  - "Web サービス [Visual Studio での Office 開発]、ドキュメントの読み込み"
  - "データ [Visual Studio での Office 開発]、ドキュメントへの追加"
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 方法 : サービスのデータをドキュメントに読み込む
  Microsoft Office のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトと同じ方法でデータにアクセスできます。 同じツールとコードを使用してソリューションにデータを取り込むことができ、Windows フォーム コントロールを使用してデータを表示できます。 さらに、ホスト コントロールと呼ばれるコントロールを利用できます。これは、Microsoft Office Excel および Microsoft Office Word のネイティブ オブジェクトであり、イベントやデータ バインディング機能が強化されています。 詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 次の例は、デザイン時にドキュメントにデータ バインド コントロールを追加する方法を示しています。 実行時に VSTO アドインでデータ バインド コントロールを追加する方法の例については、「[チュートリアル : VSTO アドイン プロジェクトでサービスのデータをバインドする](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md)」を参照してください。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.png "ビデオへのリンク") 関連するビデオ デモについては、「[方法: Microsoft Excel から Web サービスと対話する](http://go.microsoft.com/fwlink/?LinkID=130284)」を参照してください。  
  
### Web サービスからドキュメント レベルのプロジェクトにデータを読み込むには  
  
1.  **\[データ ソース\]** ウィンドウを開き、プロジェクトのサービス データ ソースを作成します。 詳細については、「[方法: サービスのデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Service.md)」を参照してください。  
  
2.  目的のテーブルまたはフィールドを **\[データ ソース\]** ウィンドウからドキュメントまでドラッグします。  
  
     コントロールがドキュメント内に作成され、<xref:System.Windows.Forms.BindingSource> が作成されてプロジェクト内のオブジェクトのクラスにバインドされ、サービスのクラスが生成されます。  
  
3.  手順 1 で接続した Web サービス クラスのインスタンスをコード内に作成します。  
  
4.  Web サービスとの通信に必要なプロパティがある場合は、それらのプロパティのインスタンスを作成します。  
  
5.  Web サービスが公開しているメソッドと、手順 4 で作成したプロパティ インスタンスを使用し、データ要求を作成して送信します。  
  
     使用するメソッドは、Web サービスが提供する内容によって異なります。  
  
6.  Web サービスからのデータ応答を、<xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティに割り当てます。  
  
 プロジェクトを実行すると、データ ソースの先頭のレコードがコントロールに表示されます。 レコードのスクロールを有効にするには、<xref:System.Windows.Forms.BindingSource> のオブジェクトを使用して通貨のイベントを処理します。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [方法 : データベースのデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [方法 : オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法 : データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  