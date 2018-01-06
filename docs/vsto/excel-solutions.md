---
title: "Excel ソリューション |Microsoft ドキュメント"
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
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
ms.assetid: 34444d54-d7b6-479a-b5b7-a946267081e9
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f12823ecb3fdc8d90d9f7c3651c6e04e6b0f6635
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="excel-solutions"></a>Excel ソリューション
  Visual Studio には、Microsoft Office Excel のドキュメント レベルのカスタマイズおよび VSTO アドインの作成に使用できるプロジェクト テンプレートが用意されています。 これらのソリューションを使用して、Excel の自動化、Excel の機能拡張、Excel のユーザー インターフェイス (UI) のカスタマイズを行うことができます。 ドキュメント レベルのカスタマイズと VSTO アドインの違いの詳細については、次を参照してください。 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
 ここでは、次の情報について説明します。  
  
-   [Excel の自動化](#automating)。  
  
-   [Excel 用のドキュメント レベルのカスタマイズの開発](#doclevel)。  
  
-   [Excel 用の VSTO アドインの開発](#applevel)。  
  
-   [Excel のユーザー インターフェイスのカスタマイズ](#UI)。  
  
##  <a name="automating"></a> Excel の自動化  
 Excel オブジェクト モデルでは、Excel の自動化に使用できる型が多数公開されています。 たとえば、グラフの作成、ワークシートの書式設定、範囲やセルの値の設定をプログラムを使用して実行できます。 詳細については、「 [Excel Object Model Overview](../vsto/excel-object-model-overview.md)」を参照してください。  
  
 Visual Studio で Excel ソリューションを開発する場合、ソリューションで *ホスト項目* と *ホスト コントロール* も使用できます。 これらのオブジェクトは、Excel オブジェクト モデル内にある、 <xref:Microsoft.Office.Interop.Excel.Worksheet> や <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトなど、よく使用される特定のオブジェクトを拡張したオブジェクトです。 これらの拡張オブジェクトは、基になる Excel オブジェクトと同じように動作しますが、基のオブジェクトにはないイベントとデータ バインディング機能が追加されています。 詳細については、「 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)」を参照してください。  
  
##  <a name="doclevel"></a> Developing Document-Level Customizations for Excel  
 Microsoft Office Excel のドキュメント レベルのカスタマイズは、特定のブックに関連付けられたアセンブリで構成されます。 このアセンブリは、一般には UI のカスタマイズと Excel の自動化によってブックの機能を拡張します。 Excel 自体と関連付けられる VSTO アドインとは異なり、カスタマイズに実装した機能は、関連付けられたブックが Excel で開かれている場合にのみ利用できます。  
  
 Excel 用のドキュメント レベルのカスタマイズ プロジェクトを作成するには、Visual Studio の **[新しいプロジェクト]** ダイアログ ボックスで Excel ブックまたは Excel テンプレートのプロジェクト テンプレートを使用します。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
 ドキュメント レベルのカスタマイズが機能するしくみの詳細については、「 [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md)」を参照してください。  
  
### <a name="excel-customization-programming-model"></a>Excel カスタマイズのプログラミング モデル  
 Excel 用のドキュメント レベルのプロジェクトを作成すると、ソリューションの基礎となるクラス ( `ThisWorkbook`、 `Sheet1`、 `Sheet2`、および `Sheet3`) が Visual Studio によって生成されます。 これらのクラスはソリューションに関連付けられたブックおよびワークシートを表し、コードを記述するための開始点となります。  
  
 生成されたこれらのクラスおよびドキュメント レベルのプロジェクトで使用できる他の機能の詳細については、「 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)」を参照してください。  
  
##  <a name="applevel"></a> Excel 用の VSTO アドインの開発  
 Microsoft Office Excel の VSTO アドインは、Excel によって読み込まれるアセンブリで構成されます。 このアセンブリは、一般には UI のカスタマイズと Excel の自動化によって Excel の機能を拡張します。 特定のブックに関連付けられるドキュメント レベルのカスタマイズとは異なり、VSTO アドインに実装する機能の対象は 1 つのブックだけに制限されません。  
  
 Excel 用の VSTO アドイン プロジェクトを作成するには、Visual Studio の **[新しいプロジェクト]** ダイアログ ボックスで Excel ブックまたは Excel テンプレートのプロジェクト テンプレートを使用します。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
 VSTO アドインが機能するしくみの概要については、「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法は i: PowerPoint を自動化する Excel アドインを?](http://go.microsoft.com/fwlink/?LinkID=130300)です。  
  
### <a name="excel-add-in-programming-model"></a>Excel アドインのプログラミング モデル  
 Excel VSTO アドイン プロジェクトを作成すると、 `ThisAddIn`と呼ばれる、ソリューションの基礎となるクラスが Visual Studio によって生成されます。 このクラスは、コードを記述するための開始点となり、Excel のオブジェクト モデルを VSTO アドインに公開します。  
  
 詳細については、`ThisAddIn`クラスおよび VSTO アドインで使用できるその他の Visual Studio の機能を参照してください[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)です。  
  
##  <a name="UI"></a> Customizing the User Interface of Excel  
 Excel のユーザー インターフェイスをカスタマイズする方法はいくつかあります。 一部のオプションはすべてのプロジェクト タイプで使用できますが、VSTO アドインまたはドキュメント レベルのカスタマイズでのみ使用できるオプションもあります。  
  
### <a name="options-for-all-project-types"></a>すべてのプロジェクト タイプのオプション  
 ドキュメント レベルのカスタマイズと VSTO アドインの両方に使用できるカスタマイズ オプションを次の表に示します。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|リボンをカスタマイズする。|[リボンの概要](../vsto/ribbon-overview.md)|  
|Windows フォーム コントロールまたは拡張された Excel コントロールを、ドキュメント レベルのカスタマイズ用のカスタマイズされたブック内のワークシート、または VSTO アドイン用の任意の開いているブック内のワークシートに追加する。|[方法: Office ドキュメントに Windows フォーム コントロールを追加する](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [方法: ワークシートに Chart コントロールを追加する](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [方法: ワークシートに ListObject コントロールを追加する](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [方法: ワークシートに NamedRange コントロールを追加する](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-document-level-customizations"></a>ドキュメント レベルのカスタマイズのオプション  
 ドキュメント レベルのカスタマイズにのみ使用できるカスタマイズ オプションを次の表に示します。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|ブックに操作ウィンドウを追加する。|[操作ウィンドウの概要](../vsto/actions-pane-overview.md)<br /><br /> [方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|XML ノードにマップする拡張範囲コントロールをワークシートに追加する。|[方法: ワークシートに XmlMappedRange コントロールを追加する](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-vsto-add-ins"></a>VSTO アドインのオプション  
 VSTO アドインにのみ使用できるカスタマイズ オプションを次の表に示します。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Excel Object Model Overview](../vsto/excel-object-model-overview.md)|Excel オブジェクト モデルによって提供される主な型の概要について説明します。|  
|[Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)|Excel ソリューションで使用できる ( [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]によって提供される) 拡張オブジェクトについて説明します。|  
|[Excel ソリューションのグローバリゼーションとローカリゼーション](../vsto/globalization-and-localization-of-excel-solutions.md)|Windows が英語以外の言語に設定されているコンピューター上で実行される Excel ソリューションに関する特記事項について説明します。|  
|[Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)|Windows フォーム コントロールを Excel ワークシートに追加する方法について説明します。|  
|[チュートリアル: 初めての Excel 用ドキュメント レベルのカスタマイズの作成](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Excel 用の基本的なドキュメント レベルのカスタマイズを作成する方法を示します。|  
|[チュートリアル: 初めての Excel 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Excel 用の基本的な VSTO アドインを作成する方法を示します。|  
|[チュートリアル: 実行時における VSTO アドイン プロジェクトのワークシートへのコントロールの追加](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|VSTO アドインを使用して、実行時に Windows フォームのボタン、 <xref:Microsoft.Office.Tools.Excel.NamedRange>、および <xref:Microsoft.Office.Tools.Excel.ListObject> をワークシートに追加する方法を示します。|
|[共同作成とアドインの理解](./understanding-coauthoring-and-addins.md)|ソリューションに共同編集に対応させるために必要な場合があります調整をについて説明します。|  
|[Office 開発における Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199011)|Excel ソリューションの開発に関する記事およびリファレンス ドキュメントへのリンクを提供します。 Visual Studio を使用した Office 開発だけの情報ではありません。|  
  
  