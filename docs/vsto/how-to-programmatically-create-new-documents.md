---
title: '方法: プログラムによって新しいドキュメントを作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c07067614c47f56bc5f21456ebe70c74d6cf62b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-create-new-documents"></a>方法: プログラムによって新しい文書を作成する
  プログラムによって作成される新しい文書は、ネイティブの <xref:Microsoft.Office.Interop.Word.Document> オブジェクトです。 このオブジェクトは、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目のような付加的なイベントやデータ バインディング機能を備えていません。 詳細については、「 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)」を参照してください。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトを開発する場合、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目をプログラムによってプロジェクトに追加することはできません。 VSTO アドイン プロジェクトでは、実行時に任意の <xref:Microsoft.Office.Interop.Word.Document> オブジェクトを <xref:Microsoft.Office.Tools.Word.Document> ホスト項目に変換できます。 詳細については、「 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
### <a name="to-create-a-new-document-based-on-the-normal-template"></a>Normal テンプレートに基づいて新しい文書を作成するには  
  
-   <xref:Microsoft.Office.Interop.Word.Documents> コレクションの <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> メソッドを使用して、Normal テンプレートに基づく新しい文書を作成します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="using-custom-templates"></a>カスタム テンプレートの使用  
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A>メソッドには、省略可能な*テンプレート*Normal テンプレート以外のテンプレートに基づいて新しい文書を作成する引数。 テンプレートのファイル名と完全修飾パスを指定する必要があります。  
  
#### <a name="to-create-a-new-document-based-on-a-custom-template"></a>カスタム テンプレートに基づいて新しい文書を作成するには  
  
-   テンプレートのパスを指定して <xref:Microsoft.Office.Interop.Word.Documents> コレクションの <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> メソッドを呼び出します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって既存のドキュメントを開く](../vsto/how-to-programmatically-open-existing-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  