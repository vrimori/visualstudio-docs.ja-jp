---
title: "方法 : データベースのデータをワークシートに読み込む"
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
  - "データ [Visual Studio での Office 開発], 追加 (ワークシートに)"
  - "データベース [Visual Studio での Office 開発], 読み込み (ワークシートに)"
  - "ワークシート [Visual Studio での Office 開発], データの読み込み"
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 方法 : データベースのデータをワークシートに読み込む
  Windowsフォーム プロジェクトの場合、ドキュメント レベルのOfficeプロジェクトのデータを同じようにアクセスできます。  同じツールとコードを使用してソリューションにデータを読み込むことができ、また Windows フォーム コントロールを使用してデータを表示することもできます。  また、ホスト コントロールというコントロールを利用できます。ホスト コントロールは Microsoft Office Excel のネイティブ オブジェクトであり、イベントとデータ バインディング機能が拡張されています。  詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 次の例は、デザイナーを使用してドキュメント レベルのプロジェクトにデータ バインド コントロールを追加する方法を示しています。  実行時にアプリケーション レベルのプロジェクトにデータ バインド コントロールを追加する方法の例については、「[チュートリアル : VSTO アドイン プロジェクトでの複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)」を参照してください。  
  
 ![ビデオへのリンク](~/docs/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[How Do I: Transfer Data Into an Excel Worksheet? \(操作方法: Excel ワークシートにデータを転送する\)](http://go.microsoft.com/fwlink/?LinkID=130277)」および「[How Do I: Consume Database Data in Excel? \(Excel でデータベースのデータを使用する\)](http://go.microsoft.com/fwlink/?LinkID=130287)」を参照してください。  
  
## デザイン時のワークシートへのデータ バインド コントロールの追加  
  
#### データベースのデータをワークシートに読み込むには  
  
1.  Visual Studio で Excel のドキュメント レベルのプロジェクトを開き、デザイナーでワークシートを開きます。  
  
2.  **\[データ ソース\]** ウィンドウを開き、プロジェクトのデータ ソースを作成します。  詳細については、「[方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)」を参照してください。  
  
3.  **\[データ ソース\]** ウィンドウからワークシートに、フィールドまたはテーブルをドラッグします。  
  
 ワークシートに、次のいずれかのコントロールが作成されます。  
  
-   フィールドをドラッグした場合、ワークシートには <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールが作成されます。  詳細については、「[NamedRange コントロール](../vsto/namedrange-control.md)」を参照してください。  
  
-   テーブルをドラッグした場合、ワークシートには <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールが作成されます。  詳細については、「[ListObject コントロール](../vsto/listobject-control.md)」を参照してください。  
  
 別のコントロールを追加するには、**\[データ ソース\]** ウィンドウでテーブルまたはフィールドを選択し、ドロップダウン リストで別のコントロールを選択します。  
  
## プロジェクト内のオブジェクト  
 プロジェクトには、コントロールに加え、データに関連する以下のオブジェクトも自動的に追加されます。  
  
-   データベースで接続したデータ テーブルをカプセル化する型指定されたデータセット。  詳細については、「[Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)」を参照してください。  
  
-   コントロールを型指定されたデータセットに接続する <xref:System.Windows.Forms.BindingSource>。  詳細については、「[BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)」を参照してください。  
  
-   型指定されたデータセットをデータベースに接続する TableAdapter。  詳細については、「[TableAdapter の概要](/visual-studio/data-tools/tableadapter-overview)」を参照してください。  
  
-   データセット内のテーブル アダプターを調整することによって階層更新を可能にする TableAdapterManager。  詳細については、「[階層更新](../data-tools/hierarchical-update.md)」および「[TableAdapterManager の概要](../Topic/TableAdapterManager%20Overview.md)」を参照してください。  
  
 プロジェクトを実行すると、データ ソースの先頭のレコードがコントロールに表示されます。  <xref:System.Windows.Forms.BindingSource> を使用すると、ユーザーはレコードをスクロールできるようになります。  
  
#### レコード間をスクロールするには  
  
-   <xref:System.Windows.Forms.BindingSource.MoveNext%2A> や <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> などの <xref:System.Windows.Forms.BindingSource> メソッドを使用します。  
  
 型指定されたデータセットやデータベースに更新を送信する方法の詳細については、「[方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)」を参照してください。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [方法 : オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法 : データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法 : サービスのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [How Do I: Excelワークシートにデータを転送します](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [How Do I: Excelのデータベースのデータを実行します。](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  