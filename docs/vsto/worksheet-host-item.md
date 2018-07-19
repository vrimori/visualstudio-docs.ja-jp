---
title: Worksheet ホスト項目
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4052e7d9b096d9bae6671834369ece6d31bee4a0
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258919"
---
# <a name="worksheet-host-item"></a>Worksheet ホスト項目
  <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目は、Excel のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Excel.Worksheet> 型を拡張する型です。 <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目は <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトと同一のプロパティ、メソッド、イベントをすべて提供します。また、追加のイベントも公開し、ホスト コントロールおよび Windows フォーム コントロールのコンテナーとしても機能します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトでは、デザイン時に <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目をプロジェクトに追加できます。 VSTO アドイン プロジェクトで生成できる<xref:Microsoft.Office.Tools.Excel.Worksheet>実行時に項目をホストします。  
  
## <a name="understand-worksheet-host-items-in-document-level-projects"></a>ドキュメント レベルのプロジェクトのワークシート ホスト項目を理解します。  
 Excel のドキュメント レベルのプロジェクトを作成すると、Visual Studio によって 3 つの <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目がプロジェクト内に自動的に作成されます。 これらのワークシートの既定の名前は、 `Sheet1`、 `Sheet2`、 `Sheet3`です。 既存のブックに基づいてプロジェクトを作成する場合は、そのブック内のワークシートの数に応じてホスト項目の数が決まります。  
  
 これらのワークシート クラスによって、 <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目のメンバーにアクセスし、ワークシートのコンテンツを変更するなど、カスタマイズの基本的なタスクを実行できます。 また、ワークシートにコントロールを追加するには、これらのクラスを使用できます。 さまざまな種類のコントロールを組み合わせ、コードを記述することによって、コントロールのデータへのバインド、ユーザー情報の収集、およびユーザーの操作への応答を実行できます。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)します。  
  
 ワークシート クラスには、プロジェクトでコードの記述を開始できる場所が用意されています。 このクラスには、Excel のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されているため、これらのクラスを使用して Excel のオブジェクト モデルにアクセスすることもできます。 詳細については、次を参照してください。 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)します。  
  
 ドキュメント レベルのプロジェクトの場合は、デザイナーで新しいワークシートをブックに追加すると、デザイン時に追加の <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目をプロジェクトに追加できます。  
  
### <a name="rename-worksheets"></a>ワークシートの名前を変更します。  
 ドキュメント レベルのプロジェクトでは、Visual Studio デザイナーでワークシートの名前を変更できますが、この場合はワークシートの表示名だけが変わります。 ワークシートのプログラム上の名前は既定の名前のままです。 **[プロパティ]** ウィンドウでワークシートの名前を変更すると、プログラム上の名前だけが変更されます。  
  
### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>ドキュメント レベルのプロジェクトで、worksheet ホスト項目の制限事項  
 新規に作成することはできません<xref:Microsoft.Office.Tools.Excel.Worksheet>ドキュメント レベルのプロジェクトの実行時に項目をホストします。 実行時に新しい Excel ワークシートを作成する場合、型のことが<xref:Microsoft.Office.Interop.Excel.Worksheet>します。 これはホスト項目ではないため、ホスト コントロールや Windows フォーム コントロールを含めることはできません。 実行時にドキュメントを作成する方法の詳細については、次を参照してください。[方法: プログラムによって新しいワークシートをブックに追加](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)します。  
  
## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>VSTO アドイン プロジェクトのワークシート ホスト項目を理解します。  
 アプリケーション レベルのプロジェクトでは、Excel で開いている任意のワークシートの <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を実行時に生成できます。 <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を使用して、関連付けられたワークシートにコントロールを追加したり、 <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトで使用できないイベントを処理したりできます。  
  
 生成する、<xref:Microsoft.Office.Tools.Excel.Worksheet>ホスト項目を使用して、`GetVstoObject`メソッド。 詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Workbook ホスト項目](../vsto/workbook-host-item.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  