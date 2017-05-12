---
title: "方法 : オブジェクトのデータをドキュメントに読み込む"
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
  - "データ [Visual Studio での Office 開発]、ドキュメントへの追加"
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 方法 : オブジェクトのデータをドキュメントに読み込む
  Microsoft Office Word のドキュメント レベルのプロジェクトでは、Windows フォーム プロジェクトと同じ方法でデータ オブジェクトのデータにアクセスできます。 同じツールとコードを使用してオブジェクトからソリューションにデータを読み込むことができ、Windows フォーム コントロールを使用してデータを表示できます。 また、ホスト コントロールを使用してデータを表示することもできます。 ホスト コントロールは、イベントおよびデータ バインディングの機能が強化された Microsoft Office Word のネイティブ オブジェクトです。 詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 ドキュメントにオブジェクトのデータを読み込むには、次の 3 つの基本手順を実行する必要があります。  
  
-   データにバインドできるドキュメントにコントロールを追加する。  
  
-   データ オブジェクトをドキュメントに追加する。  
  
-   データ オブジェクトを BindingSource に接続する。  
  
## データ オブジェクトの追加  
  
#### データ オブジェクトを追加するには  
  
-   **\[データ ソース\]** ウィンドウを開き、オブジェクトからデータ ソースを作成します。 詳細については、「[方法: オブジェクトのデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)」を参照してください。  
  
## データ オブジェクトの BindingSource への接続  
 ドキュメント レベルのプロジェクトでは、デザイン時にコントロールを文書に追加し、そのコントロールをデータにバインドできます。  
  
 VSTO アドイン プロジェクトでは、コントロールを作成して、そのコントロールを実行時にバインドできます。  
  
### ドキュメント レベルのプロジェクト  
  
##### データ オブジェクトを BindingSource に接続するには  
  
1.  **\[データ ソース\]** ウィンドウから目的のデータ フィールドを文書にドラッグします これにより、コントロールが自動的に作成されます。  
  
2.  コードで、データ ソースとして選択したオブジェクトの種類のインスタンスを作成します。  
  
3.  このインスタンスを <xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティに割り当てます。  
  
### アプリケーション レベルのプロジェクト  
  
##### データ オブジェクトを BindingSource に接続するには  
  
1.  コード中に、データ ソースに関連付けられているオブジェクトの種類のインスタンスを作成します。  
  
2.  <xref:System.Windows.Forms.BindingSource> のインスタンスを作成します。  
  
3.  データ ソースのインスタンスを <xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティに割り当てます。  
  
4.  コントロールへのデータ バインディングとしてデータ ソースを追加します。  
  
## 参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [方法 : データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法 : ホスト コントロールからのデータでデータ ソースを更新する](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Windows フォーム アプリケーションでのデータへの接続](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource コンポーネントの概要](../Topic/BindingSource%20Component%20Overview.md)  
  
  