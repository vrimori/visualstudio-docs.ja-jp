---
title: "方法: プログラムによって新しいドキュメントを作成 |Microsoft ドキュメント"
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
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 09e6f9e0e2bc6a001f6a2b67c733f11bfb725563
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-create-new-documents"></a>方法: プログラムによって新しい文書を作成する
  プログラムによって作成される新しい文書は、ネイティブの <xref:Microsoft.Office.Interop.Word.Document> オブジェクトです。 このオブジェクトは、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目のような付加的なイベントやデータ バインディング機能を備えていません。 詳細については、「 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)」を参照してください。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトを開発する場合、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目をプログラムによってプロジェクトに追加することはできません。 VSTO アドイン プロジェクトでは、実行時に任意の <xref:Microsoft.Office.Interop.Word.Document> オブジェクトを <xref:Microsoft.Office.Tools.Word.Document> ホスト項目に変換できます。 詳細については、「 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
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
  
## <a name="see-also"></a>参照  
 [方法: プログラムによって既存のドキュメントを開く](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  