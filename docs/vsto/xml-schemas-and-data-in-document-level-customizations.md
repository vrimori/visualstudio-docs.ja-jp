---
title: "ドキュメント レベルのカスタマイズにおける XML スキーマとデータ"
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
  - "Visual Studio での Office 開発, XML"
  - "スキーマ [Visual Studio での Office 開発]"
  - "XML [Visual Studio での Office 開発], XML スキーマ"
  - "XML スキーマ [Visual Studio での Office 開発]"
  - "XML スキーマ [Visual Studio での Office 開発], XML スキーマとデータの概要"
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# ドキュメント レベルのカスタマイズにおける XML スキーマとデータ
  **重要** は、マイクロソフトが米国カスタムにある場合や、実行用のプログラム、2010年1月1日の前のMicrosoftによってライセンスMicrosoft Word製品使用している個々の利点のためにMicrosoft Wordに関するこのトピックに記載されているMicrosoft情報がMicrosoft WordからカスタムXMLに関連する特定の機能の実装を削除したときに、使用、および組織。  ここに記載されている Microsoft Word に関する情報を、2010 年 1 月以降にマイクロソフトがライセンスを供与した Microsoft Word 製品上で実行されるプログラムを使用または開発する、米国およびその領土内の個人または組織が参照および使用することはお勧めしません。これに該当する製品は、この日付以前にライセンスが供与された製品、および米国外での使用を目的として購入またはライセンスが供与された製品と同様には動作しません。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel および Microsoft Office Word には、ドキュメントにスキーマを割り当てる機能があります。  この機能により、ドキュメントへの XML データのインポートや、ドキュメントからの XML データのエクスポートを簡単に行うことができます。  
  
 Visual Studio では、ドキュメント レベルのカスタマイズにある割り当てられたスキーマ要素を、プログラミング モデル内でコントロールとして公開します。  さらに、Excel では、データベースのデータ、Web サービス、およびオブジェクトに、このコントロールをバインドできます。  また、Word および Excel では、操作ウィンドウもサポートされており、スキーマが割り当てられたドキュメントと併せて使用することにより、エンド ユーザーによるソリューションの操作性を向上させることができます。  詳細については、「[操作ウィンドウの概要](../vsto/actions-pane-overview.md)」を参照してください。  
  
> [!NOTE]  
>  Excel ソリューションでは、マルチパート XML スキーマは使用できません。  
  
## Excel のブックにスキーマを割り当てるときに作成されるオブジェクト  
 ブックにスキーマを割り当てると、Visual Studio によっていくつかのオブジェクトが自動的に作成され、プロジェクトに追加されます。  こうしたオブジェクトは Excel で管理されるので、Visual Studio ツールを使って削除しないようにします。  これらのオブジェクトを削除するには、割り当てられている要素をワークシートから削除するか、Excel ツールを使用してスキーマを削除します。  
  
 次に挙げる 2 つの主要なオブジェクトがあります。  
  
-   XML スキーマ \(XSD ファイル\)。  Visual Studio により、ブック内のスキーマごとにプロジェクトにもスキーマが追加されます。  **ソリューション エクスプローラー**では、各スキーマが拡張子 XSD を持つプロジェクト項目として表されます。  
  
-   型指定された <xref:System.Data.DataSet> クラス。  このクラスは、スキーマに基づいて作成されます。  このデータセット クラスは **\[クラス ビュー\]** で表示可能です。  
  
## スキーマ要素が Excel ワークシートに割り当てられるときに作成されたオブジェクト  
 **\[XML ソース\]** 作業ウィンドウのスキーマ要素をワークシートに割り当てると、Visual Studio では、自動的に複数のオブジェクトが作成され、プロジェクトに追加されます。  
  
-   コントロール。  ブック内で割り当てられているオブジェクトごとに、プログラミング モデル内に <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロール \(非繰り返しスキーマ要素の場合\) または <xref:Microsoft.Office.Tools.Excel.ListObject> コントロール \(繰り返しスキーマ要素の場合\) が作成されます。  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは、ブックから割り当て元および割り当て先のオブジェクトを削除することによってのみ削除できます。  コントロールの詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
-   BindingSource。  非繰り返しスキーマ要素をワークシートに割り当てて <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> を作成すると、<xref:System.Windows.Forms.BindingSource> が作成され、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールが <xref:System.Windows.Forms.BindingSource> にバインドされます。  <xref:System.Windows.Forms.BindingSource> は、型指定された <xref:System.Data.DataSet> クラスから作成されたインスタンスなど、ドキュメントに割り当てたスキーマと一致するデータ ソースのインスタンスにバインドする必要があります。  バインディングは、**\[プロパティ\]** ウィンドウで公開されている、<xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティと <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティを設定して作成します。  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> は、<xref:Microsoft.Office.Tools.Excel.ListObject> オブジェクトには作成されません。  **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティおよび <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティを設定して、手動で <xref:Microsoft.Office.Tools.Excel.ListObject> をデータ ソースにバインドする必要があります。  
  
### Office のスキーマ割り当てと Visual Studio の \[データ ソース\] ウィンドウ  
 Office のスキーマ割り当て機能と Visual Studio の **\[データ ソース\]** ウィンドウは、Excel ワークシートでレポートしたり編集したりするデータを表現するのに役立ちます。  どちらの場合も、Excel ワークシートにデータ要素をドラッグできます。  どちらの方法でも、<xref:System.Windows.Forms.BindingSource> から <xref:System.Data.DataSet> や Web サービスなどのデータ ソースにバインドするコントロールが作成されます。  
  
> [!NOTE]  
>  繰り返しスキーマ要素をワークシートに割り当てると、Visual Studio によって <xref:Microsoft.Office.Tools.Excel.ListObject> が作成されます。  <xref:Microsoft.Office.Tools.Excel.ListObject> は、<xref:System.Windows.Forms.BindingSource> を介して自動的にデータにバインドされることはありません。  **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティおよび <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティを設定して、手動で <xref:Microsoft.Office.Tools.Excel.ListObject> をデータ ソースにバインドする必要があります。  
  
 この 2 つの方法の相違点の一部を以下の表に示します。  
  
|XML スキーマ|\[データ ソース\] ウィンドウ|  
|--------------|-----------------------|  
|Office インターフェイスを使用する。|Visual Studio の **\[データ ソース\]** ウィンドウを使用する。|  
|XML ファイルのデータのインポートとエクスポートを行う Office の組み込みの機能を有効にする。|インポートとエクスポートの機能はプログラムによって行う必要がある。|  
|生成されたコントロールにデータを書き込むにはコードを記述する必要がある。|**\[データ ソース\]** ウィンドウから追加されたコントロールには、データを書き込むコード、およびデータベース サーバーを使用するときに必要な接続文字列が自動的に生成される。|  
  
## Word 文書にスキーマを割り当てた場合の動作  
 ドキュメント レベルの Office プロジェクトで使用する Word 文書にスキーマを割り当てた場合は、データ オブジェクトは作成されません。  ただし、文書にスキーマ要素を割り当てると、コントロールが作成されます。  どのタイプの要素を割り当てるかによって、コントロールの種類は異なります。繰り返し要素の場合は <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールが、非繰り返し要素の場合は <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールが作成されます。  詳細については、「[XMLNodes コントロール](../vsto/xmlnodes-control.md)」および「[XMLNode コントロール](../vsto/xmlnode-control.md)」を参照してください。  
  
## XML スキーマを含んだソリューションの配置  
 文書に割り当てられた XML スキーマを使用しているソリューションを配置するには、インストーラーを作成する必要があります。  そのインストーラーで、ユーザーのコンピューターのスキーマ ライブラリにスキーマを登録します。  スキーマを登録しなくても、ユーザーが文書を開いたときに、文書内の要素に基づいて Word で一時スキーマが生成されるため、ソリューションは動作します。  ただし、この場合、ユーザーは、プロジェクトの作成に使用されたスキーマの妥当性検査や保存を行うことができません。  インストーラーの詳細については、「[アプリケーション、サービス、およびコンポーネントの配置](../deployment/deploying-applications-services-and-components.md)」を参照してください。  
  
 コードをプロジェクトに追加して、スキーマがライブラリにあって登録されているかどうかを検査することもできます。  登録されていない場合には、ユーザーに警告できます。  
  
 [!code-csharp[Trin_VstcoreDataWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstcoreDataWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/VB/ThisDocument.vb#1)]  
  
## 参照  
 [方法 : Visual Studio 内で Word 文書にスキーマを割り当てる](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [方法 : Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  