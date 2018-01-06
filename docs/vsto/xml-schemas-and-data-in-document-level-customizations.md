---
title: "XML スキーマとドキュメント レベルのカスタマイズでデータ |Microsoft ドキュメント"
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
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 80049a46659b4921da2fd2bb51c8ae1afc2dd76e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>ドキュメント レベルのカスタマイズにおける XML スキーマとデータ
  **重要な**Microsoft Word に関するこのトピックに設定された情報が、利点と個人ユーザーおよびユーザーは、米国およびその区域外部にあるまたはを使用しているユーザーは、組織の使用専用に示された、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月前に Microsoft によってライセンス供与された Microsoft Word 製品に関連するカスタムの XML から Microsoft Word。 Microsoft Word に関する情報はこの可能性がありますいない読み取りまたは個人または米国またはその区域、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word 製品上で実行されるプログラムの開発を使用して、ユーザーの組織で使用されます。;これらの製品では、その日付の前にライセンスまたは購入し、米国外の利用に対してライセンス供与の製品と同じ動作がしません。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel および Microsoft Office Word 文書にスキーマをマップする機能を提供します。 この機能は、インポートとエクスポート、ドキュメントの XML データに簡略化できます。  
  
 Visual Studio の公開は、プログラミング モデル内のコントロールとしてドキュメント レベルのカスタマイズ内のスキーマ要素をマップします。 Excel の場合は、Visual Studio は、データベース、Web サービス、およびオブジェクトでのデータへのコントロールのバインドのサポートを追加します。 Word と Excel の場合は、Visual Studio は、操作ウィンドウは、ソリューションの拡張のエンド ユーザー エクスペリエンスを作成するスキーマにマップされたドキュメントで使用できますのサポートを追加します。 詳細については、「 [Actions Pane Overview](../vsto/actions-pane-overview.md)」を参照してください。  
  
> [!NOTE]  
>  Excel ソリューションでマルチパートの XML スキーマを使用することはできません。  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>スキーマは、Excel ブックに関連付けられているときに作成されるオブジェクト  
 ブックにスキーマをアタッチする際に Visual Studio は自動的に複数のオブジェクトを作成して、それらをプロジェクトに追加します。 これらのオブジェクトは削除できません、Visual Studio ツールを使用 Excel で管理されているためです。 それらを削除するには、ワークシートからマップされた要素を削除または Excel ツールを使用してスキーマを削除します。  
  
 これには 2 つの主要なオブジェクトがあります。  
  
-   XML スキーマ (XSD ファイル) です。 ブックのすべてのスキーマでは、Visual Studio はプロジェクトにスキーマを追加します。 XSD の拡張機能のプロジェクト アイテムとして表示されます**ソリューション エクスプ ローラー**です。  
  
-   型指定された <xref:System.Data.DataSet> クラス。 このクラスは、スキーマに基づいて作成されます。 このデータセット クラスがで表示**クラス ビュー**です。  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Excel ワークシートにスキーマ要素がマップされているときに作成されるオブジェクト  
 スキーマ要素をマップすると、 **XML ソース**をワークシートに、Visual Studio の作業ウィンドウは自動的にいくつかのオブジェクトを作成し、プロジェクトに追加します。  
  
-   コントロール ブック内のすべてのマップされたオブジェクトに対して、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロール (用スキーマの非繰り返し要素) または<xref:Microsoft.Office.Tools.Excel.ListObject>コントロール (スキーマの要素を繰り返し) 用プログラミング モデルで作成します。 <xref:Microsoft.Office.Tools.Excel.ListObject>コントロールは、ブックから、マップおよびマップされたオブジェクトを削除することによってのみ削除できます。 コントロールの詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)です。  
  
-   BindingSource です。 作成するとき、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>ワークシートを非繰り返しスキーマ要素をマップすることによって、<xref:System.Windows.Forms.BindingSource>が作成され、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールにバインドする、<xref:System.Windows.Forms.BindingSource>です。 バインドする必要があります、<xref:System.Windows.Forms.BindingSource>の型指定されたインスタンスなど、ドキュメントにマップされているスキーマと一致するデータ ソースのインスタンスに<xref:System.Data.DataSet>作成されたクラスです。 設定して、バインディングを作成、<xref:System.Windows.Forms.BindingSource.DataSource%2A>と<xref:System.Windows.Forms.BindingSource.DataMember%2A>で公開されているプロパティ、**プロパティ**ウィンドウです。  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource>に対しては作成されません<xref:Microsoft.Office.Tools.Excel.ListObject>オブジェクト。 手動でバインドする必要があります、<xref:Microsoft.Office.Tools.Excel.ListObject>を設定して、データ ソースに、<xref:System.Windows.Forms.BindingSource.DataSource%2A>と<xref:System.Windows.Forms.BindingSource.DataMember%2A>プロパティで、**プロパティ**ウィンドウです。  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office マッピング スキーマとデータ ソースの Visual Studio ウィンドウ  
 Office アプリケーションおよび Visual Studio の対応付けられたスキーマ機能**データソース**ウィンドウを使用して、レポート作成または編集するための Excel ワークシートにデータを表示できます。 どちらの場合は、Excel ワークシートにデータ要素をドラッグできます。 両方のメソッドがデータを使用してバインドされるコントロールを作成、<xref:System.Windows.Forms.BindingSource>などのデータ ソースに、<xref:System.Data.DataSet>または Web サービスです。  
  
> [!NOTE]  
>  Visual Studio が作成、ワークシートに繰り返されるスキーマ要素をマップすると、<xref:Microsoft.Office.Tools.Excel.ListObject>です。 <xref:Microsoft.Office.Tools.Excel.ListObject>を使用してデータに自動的にバインドされていない、<xref:System.Windows.Forms.BindingSource>です。 手動でバインドする必要があります、<xref:Microsoft.Office.Tools.Excel.ListObject>を設定して、データ ソースに、<xref:System.Windows.Forms.BindingSource.DataSource%2A>と<xref:System.Windows.Forms.BindingSource.DataMember%2A>プロパティで、**プロパティ**ウィンドウです。  
  
 次の表は、2 つの方法の違いの一部を示します。  
  
|XML スキーマ|[データ ソース] ウィンドウ|  
|----------------|-------------------------|  
|Office のインターフェイスを使用します。|使用して**データソース**Visual Studio のウィンドウ。|  
|インポートして、XML ファイルからデータをエクスポートするのには、Office の組み込み機能を有効にします。|インポートし、エクスポート機能をプログラムで必要があります。|  
|データの生成されたコントロールを設定するコードを記述する必要があります。|追加されたコントロール、**データソース**ウィンドウに、データベース サーバーを使用するときに必要な接続文字列と共に自動的に生成されたコードがあります。|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Word 文書にスキーマを割り当てるときの動作  
 ドキュメント レベルの Office プロジェクトで使用されている Word 文書にスキーマをアタッチすると、データ オブジェクトは作成されません。 ただし、スキーマ要素をドキュメントにマップするときにコントロールを作成します。 コントロールの種類は、要素を割り当てるの種類によって異なります。要素の生成を繰り返し<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール、および非繰り返し要素が生成<xref:Microsoft.Office.Tools.Word.XMLNode>コントロール。 詳細については、次を参照してください。 [XMLNodes コントロール](../vsto/xmlnodes-control.md)と[XMLNode コントロール](../vsto/xmlnode-control.md)です。  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>XML スキーマを含むソリューションの配置  
 ドキュメントにマップされている XML スキーマを使用するソリューションを配置するインストーラーを作成する必要があります。 インストーラーでは、ユーザーのコンピューター上のスキーマ ライブラリにスキーマを登録する必要があります。 スキーマを登録しないと単語は、ユーザーによって開かれたときに、ドキュメントにある要素に基づく一時的なスキーマを生成するため、ソリューションは引き続き機能します。 ただし、ユーザーは妥当性検査や保存、プロジェクトの作成に使用されたスキーマを実行することができません。 インストーラーの詳細については、次を参照してください。[アプリケーション、サービス、および配置コンポーネント](/visualstudio/deployment/deploying-applications-services-and-components)です。  
  
 スキーマが、ライブラリではあり、登録されているかどうかを確認するようにプロジェクトにコードを追加することもできます。 そうでない場合、ユーザーに警告することができます。  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>参照  
 [方法: Visual Studio 内で Word 文書にスキーマをマップ](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [方法: Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  