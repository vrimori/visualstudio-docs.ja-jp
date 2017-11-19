---
title: "方法: プログラムによって新しい Visio 図面を作成 |Microsoft ドキュメント"
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
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa4a4d021ee0610d4fdd80a1966df6a8280c9523
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>方法: プログラムによって新しい Visio 図面を作成する
  新しい Microsoft Office Visio 図面のドキュメントを作成するときに、開いている Visio 図面の Microsoft.Office.Interop.Visio.Documents コレクションに追加します。 その結果、Microsoft.Office.Interop.Visio.Documents.Add メソッドでは、新しい Visio 描画図面を作成します。 詳細については、 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="creating-new-blank-documents"></a>新しい空白の図面の作成  
  
#### <a name="to-create-a-new-document"></a>新しい図面を作成するには  
  
-   Microsoft.Office.Interop.Visio.Documents.Add メソッドを使用すると、テンプレートに基づかない新しい空白の文書を作成できます。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>既存の図面をコピーして図面を作成する  
 Microsoft.Office.Interop.Visio.Documents.Add メソッドには、既存の Visio 図面のコピーである新しいドキュメントを作成できます。 図のファイル名と完全修飾パスを指定する必要があります。  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>既存の図面をコピーして新しい図面を作成するには  
  
-   Microsoft.Office.Interop.Visio.Documents.Add メソッドを呼び出し、Visio 図面のパスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>既存のステンシルをコピーしてステンシルを作成する  
 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) メソッドは、既存の Visio ステンシルをコピーして新しいステンシルを作成できます。 ステンシルのファイル名と完全修飾パスを指定する必要があります。  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>既存のステンシルをコピーして新しいステンシルを作成するには  
  
-   Microsoft.Office.Interop.Visio.Documents.Add メソッドを呼び出し、ステンシルのパスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>既存のテンプレートに基づいて図面を作成する  
 Microsoft.Office.Interop.Visio.Documents.Add メソッドには、既存の Visio テンプレート (.vst ファイル) に基づく新しい文書 (.vsd ファイル) を作成できます。 このメソッドは、テンプレート ワークスペースの一部である、ステンシル、スタイル、および設定をコピーします。 テンプレートのファイル名と完全修飾パスを指定する必要があります。  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>既存のテンプレートに基づいて新しい図面を作成するには  
  
-   Microsoft.Office.Interop.Visio.Documents.Add メソッドを呼び出し、テンプレートのパスを指定します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   [マイ ドキュメント] フォルダー (Windows XP 以前の場合) または [ドキュメント] フォルダー (Windows Vista の場合) 内の `myDrawing.vsd` というディレクトリにある `Test` という名前の Visio 図面。  
  
-   [マイ ドキュメント] フォルダー (Windows XP 以前の場合) または [ドキュメント] フォルダー (Windows Vista の場合) 内の `myStencil.vss` というディレクトリにある `Test` という名前の Visio 図面。  
  
-   [マイ ドキュメント] フォルダー (Windows XP 以前の場合) または [ドキュメント] フォルダー (Windows Vista の場合) 内の `myTemplate.vst` というディレクトリにある `Test` という名前の Visio 図面。  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を保存](../vsto/how-to-programmatically-save-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷する](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  