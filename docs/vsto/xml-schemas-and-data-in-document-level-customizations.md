---
title: ドキュメント レベルのカスタマイズにおける XML スキーマとデータ
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d2959707048cb3223b6866c3c8aa4c04cc146077
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875452"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>ドキュメント レベルのカスタマイズにおける XML スキーマとデータ
  **重要な**に関する Microsoft Word には、このトピックでまとめられている情報が提示の特典および個人や組織のユーザーは、米国およびその担当地域外部にあるまたはを使用しているユーザーの使用専用、または開発上で実行されるプログラム、Microsoft が特定の機能の実装を削除する場合、2010 年 1 月の前に、Microsoft によってライセンスされた Microsoft Word の製品に関連するカスタム XML から Microsoft Word です。 Microsoft Word に関するこの情報が読み取りまたは個人または組織、米国またはその区域を使用して、または、2010 年 1 月 10 日後に Microsoft によってライセンス供与された Microsoft Word の製品で実行されるプログラムの開発で使用しない可能性があります。;これらの製品では、その日付より前にライセンスまたは購入を米国外の使用ライセンスの製品と同じ動作はしません。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Microsoft Office Excel および Microsoft Office Word 文書にスキーマをマップする機能を提供します。 この機能は、インポートとエクスポート、ドキュメントの XML データに簡略化できます。

 Visual Studio の公開では、プログラミング モデル内のコントロールとしてドキュメント レベルのカスタマイズ内のスキーマ要素が割り当てられます。 For Excel では、Visual Studio は、データベース、Web サービス、およびオブジェクトのデータにコントロールをバインドするためのサポートを追加します。 Word および Excel の場合は、Visual Studio には、スキーマ マップ ドキュメントで、ソリューションの強化されたエンド ユーザー エクスペリエンスを作成するために使用する操作ウィンドウのサポートが追加されます。 詳細については、次を参照してください。[操作ウィンドウの概要](../vsto/actions-pane-overview.md)します。

> [!NOTE]
>  Excel ソリューションでは、マルチパートの XML スキーマを使用できません。

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>スキーマは、Excel ブックに関連付けられているときに作成されたオブジェクト
 ブックにスキーマをアタッチするときに Visual Studio は自動的にいくつかのオブジェクトを作成し、プロジェクトに追加します。 これらのオブジェクトは削除できません Visual Studio のツールを使用して Excel で管理されているため。 それらを削除するには、ワークシートからマップされた要素を削除または Excel ツールを使用してスキーマを削除します。

 これには 2 つの主要なオブジェクトがあります。

-   XML スキーマ (XSD ファイル) です。 ブック内のすべてのスキーマには、Visual Studio は、プロジェクトにスキーマを追加します。 XSD の拡張機能のプロジェクト アイテムとして表示されます**ソリューション エクスプ ローラー**します。

-   型指定された <xref:System.Data.DataSet> クラス。 このクラスは、スキーマに基づいて作成されます。 このデータセット クラスがで表示される**クラス ビュー**します。

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Excel ワークシートにスキーマ要素がマップされるときに作成されたオブジェクト
 スキーマ要素をマップすると、 **XML ソース**をワークシートに、Visual Studio の作業ウィンドウは自動的に複数のオブジェクトを作成し、プロジェクトに追加します。

-   コントロール ブック内のすべてのマップされたオブジェクトに対して、 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> (非繰り返しスキーマ要素) のコントロールまたは<xref:Microsoft.Office.Tools.Excel.ListObject>コントロール (繰り返しスキーマ要素) のプログラミング モデルに作成されます。 <xref:Microsoft.Office.Tools.Excel.ListObject>コントロールは、ブックからのマッピングとマップされたオブジェクトを削除することによってのみ削除できます。 コントロールの詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。

-   BindingSource します。 作成するとき、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>ワークシートを非繰り返しスキーマ要素をマップすることによって、<xref:System.Windows.Forms.BindingSource>が作成されると、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange>コントロールにバインドする、 <xref:System.Windows.Forms.BindingSource>。 バインドする必要があります、 <xref:System.Windows.Forms.BindingSource> 、型指定されたインスタンスなど、ドキュメントにマップするスキーマに一致するデータ ソースのインスタンスに<xref:System.Data.DataSet>作成されたクラスです。 設定して、バインドを作成、<xref:System.Windows.Forms.BindingSource.DataSource%2A>と<xref:System.Windows.Forms.BindingSource.DataMember%2A>プロパティで公開されている、**プロパティ**ウィンドウ。

    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource>は作成されません<xref:Microsoft.Office.Tools.Excel.ListObject>オブジェクト。 手動でバインドする必要があります、<xref:Microsoft.Office.Tools.Excel.ListObject>を設定して、データ ソースに、<xref:System.Windows.Forms.BindingSource.DataSource%2A>と<xref:System.Windows.Forms.BindingSource.DataMember%2A>プロパティで、**プロパティ**ウィンドウ。

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office はマッピング スキーマと、Visual Studio のデータ ソース ウィンドウ
 Office および Visual Studio の対応付けられたスキーマ機能**データソース**ウィンドウを使用して、レポート作成または編集するための Excel ワークシートにデータを表示できます。 どちらの場合は、Excel ワークシートにデータ要素をドラッグできます。 両方のメソッドを通じてバインドされたデータにあるコントロールの作成、<xref:System.Windows.Forms.BindingSource>などのデータ ソースに、<xref:System.Data.DataSet>または web サービス。

> [!NOTE]
>  ワークシートに繰り返されるスキーマ要素をマップするときに Visual Studio が作成、<xref:Microsoft.Office.Tools.Excel.ListObject>します。 <xref:Microsoft.Office.Tools.Excel.ListObject>を使用してデータに自動的にバインドされていない、<xref:System.Windows.Forms.BindingSource>します。 手動でバインドする必要があります、<xref:Microsoft.Office.Tools.Excel.ListObject>を設定して、データ ソースに、<xref:System.Windows.Forms.BindingSource.DataSource%2A>と<xref:System.Windows.Forms.BindingSource.DataMember%2A>プロパティで、**プロパティ**ウィンドウ。

 次の表では、2 つのメソッド間の違いの一部を示します。

|XML スキーマ|[データ ソース] ウィンドウ|
|----------------|-------------------------|
|Office インターフェイスを使用します。|使用して**データソース**Visual Studio のウィンドウ。|
|インポートおよび XML ファイルからデータをエクスポートするための Office の組み込み機能を有効にします。|インポートを指定して、エクスポート機能をプログラムでする必要があります。|
|データの生成されたコントロールを設定するコードを記述する必要があります。|追加されたコントロール、**データソース**ウィンドウに必要な接続文字列をデータベース サーバーを使用するときに入力して、自動的に生成されたコードがあります。|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>スキーマは、Word 文書に関連付けられているときの動作
 ドキュメント レベルの Office プロジェクトで使用されている Word 文書にスキーマをアタッチすると、データ オブジェクトは作成されません。 ただし、スキーマ要素をドキュメントにマップするときに、コントロールが作成されます。 コントロールの種類は; をマップする要素の種類によって異なります。要素の生成を繰り返し<xref:Microsoft.Office.Tools.Word.XMLNodes>コントロール、および非繰り返し要素が生成<xref:Microsoft.Office.Tools.Word.XMLNode>コントロール。 詳細については、次を参照してください。 [XMLNodes コントロール](../vsto/xmlnodes-control.md)と[XMLNode コントロール](../vsto/xmlnode-control.md)します。

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>XML スキーマを含むソリューションの配置
 ドキュメントにマップされている XML スキーマを使用するソリューションを配置するインストーラーを作成する必要があります。 インストーラーでは、ユーザーのコンピューター上のスキーマ ライブラリにスキーマを登録する必要があります。 スキーマを登録していない場合、ソリューションは Word ユーザーが開いたときに、ドキュメント内の要素に基づいて一時的なスキーマを生成するため、動作します。 ただし、ユーザーは、プロジェクトの作成に使用されたスキーマを保存またはに対して検証を実行することができません。 インストーラーの詳細については、次を参照してください。[アプリケーション、サービス、およびコンポーネントを展開](../deployment/deploying-applications-services-and-components.md)します。

 スキーマが、ライブラリと登録されているかどうかをチェックするプロジェクトにコードを追加することもできます。 そうでない場合は、ユーザーを警告することができます。

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>関連項目

- [方法: Visual Studio 内で Word 文書にスキーマを割り当てる](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [方法: Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
