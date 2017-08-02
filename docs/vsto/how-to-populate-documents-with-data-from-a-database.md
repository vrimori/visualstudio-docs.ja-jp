---
title: "方法 : データベースからドキュメントにデータを読み込む"
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
  - "データ, 追加 (ドキュメントに)"
  - "ドキュメント, 読み込み (データを)"
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 方法 : データベースからドキュメントにデータを読み込む
  Microsoft Office のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトでデータにアクセスする場合と同じようにデータにアクセスできます。  同じツールとコードを使用してデータベースからソリューションにデータを読み込むことができ、Windows フォーム コントロールを使用してデータを表示できます。  
  
 また、ホスト コントロールを使用してデータを表示することもできます。  ホスト コントロールは、イベントおよびデータ バインディングの機能が強化された Microsoft Office Word のネイティブ オブジェクトです。  詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 次の例は、デザイナーを使用してドキュメント レベルのプロジェクトにデータ バインド コントロールを追加する方法を示しています。  実行時に VSTO アドイン プロジェクトにデータ バインド コントロールを追加する方法の例については、「[チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)」を参照してください。  
  
 ![ビデオへのリンク](~/docs/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[Visual Studio Tools for the Office System \(3.0\) を使用した Word 2007 コンテンツ コントロールへのデータのバインディング](http://go.microsoft.com/fwlink/?LinkId=136785)」をご覧ください。  
  
## デザイン時にドキュメントにコントロールを追加する  
  
#### データベースからドキュメントにデータを読み込むには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で Word のドキュメント レベルのプロジェクトを開き、ドキュメントをデザイナーで開きます。  
  
2.  **\[データ ソース\]** ウィンドウを開き、データベースからデータ ソースを作成します。  詳細については、「[方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)」を参照してください。  
  
3.  目的のフィールドを **\[データ ソース\]** ウィンドウからドキュメントにドラッグします。  
  
 コンテンツ コントロールが文書に追加されます。  コンテンツ コントロールの種類は、選択したフィールドのデータ型によって異なります。  詳細については、「[コンテンツ コントロール](../vsto/content-controls.md)」を参照してください。  
  
 別のコントロールを追加するには、\[**データ ソース**\] ウィンドウでデータ フィールドを選択し、ドロップダウン リストで別のコントロールを選択します。  
  
## プロジェクト内のオブジェクト  
 プロジェクトには、コントロールに加えて、データに関連する以下のオブジェクトも自動的に追加されます。  
  
-   データベース内の接続したデータ テーブルをカプセル化する型指定されたデータセット。  詳細については、「[Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)」を参照してください。  
  
-   コントロールを型指定されたデータセットに接続する <xref:System.Windows.Forms.BindingSource>。  詳細については、「[BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)」を参照してください。  
  
-   型指定されたデータセットをデータベースに接続する TableAdapter。  詳細については、「[TableAdapter の概要](/visual-studio/data-tools/tableadapter-overview)」を参照してください。  
  
-   データセット内の複数のテーブル アダプターを調整することによって階層更新を可能にするために使用される TableAdapterManager。  詳細については、「[階層更新](../data-tools/hierarchical-update.md)」と「[TableAdapterManager の概要](../Topic/TableAdapterManager%20Overview.md)」を参照してください。  
  
 プロジェクトを実行すると、データ ソースの先頭のレコードがコントロールに表示されます。  <xref:System.Windows.Forms.BindingSource> を使用すると、ユーザーがレコードをスクロールできるようになります。  
  
#### レコードをスクロールするには  
  
-   <xref:System.Windows.Forms.BindingSource.MoveNext%2A> や <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> など、<xref:System.Windows.Forms.BindingSource> のメソッドを使用します。  
  
 型指定されたデータセットやデータベースに更新を送信する方法の詳細については、「[方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)」を参照してください。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [方法 : オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Office ソリューションにおけるローカル データベース使用の概要](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Windows フォーム アプリケーションでのデータへの接続](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)  
  
  