---
title: '方法: プログラムによって Visio 図面を保存'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a9f065a32fc26d372b97a31eb70836451b31fa00
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670729"
---
# <a name="how-to-programmatically-save-visio-documents"></a>方法: プログラムによって Visio 図面を保存
  Microsoft Office Visio 図面を保存するには、次のようないくつかの方法があります。  
  
- 既存の図面に変更を保存する。  
  
- 新しい図面を保存するか、または新しい名前を付けて図面を保存する。  
  
- 引数を指定して図面を保存する。  
  
  詳細については、 [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) メソッド、 [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) メソッド、および [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="save-an-existing-document"></a>既存のドキュメントを保存します。  
  
### <a name="to-save-a-document"></a>図面を保存するには  
  
-   前に保存した図面の `Microsoft.Office.Tools.Visio.Document` クラスの `Microsoft.Office.Interop.Visio.Document.Save` メソッドを呼び出します。  
  
     このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  新しい Visio 図面がまだ保存されていない場合、`Microsoft.Office.Interop.Visio.Document.Save` メソッドは例外をスローします。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>新しい名前を持つドキュメントを保存します。  
 新しい図面を保存するか、または新しい名前を付けて図面を保存するには、`Microsoft.Office.Interop.Visio.Document.SaveAs` メソッドを使用します。 このメソッドでは、新しいファイル名を指定する必要があります。  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>作業中の Visio 図面に新しい名前を付けて保存するには  
  
-   ファイル名を含む完全修飾パスを使用して、保存する `Microsoft.Office.Tools.Visio.Document` の `Microsoft.Office.Interop.Visio.Document.SaveAs` メソッドを呼び出します。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、そのファイルは警告なしで上書きされます。  
  
     このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>新しい名前および指定した引数で文書を保存します。  
 新しい名前を付けて図面を保存し、適用可能な引数を指定して図面に適用するには、`Microsoft.Office.Interop.Visio.Document.SaveAsEx` メソッドを使用します。  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>新しい名前および指定した引数を使用して図面を保存するには  
  
-   ファイル名を含む完全修飾パスを使用して、保存する `Microsoft.Office.Tools.Visio.Document` の `Microsoft.Office.Interop.Visio.Document.SaveAsEx` メソッドを呼び出します。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、例外がスローされます。  
  
     次のコード例では、作業中の図面を新しい名前で保存し、その図面を読み取り専用としてマークし、[直前に使用] の図面一覧にその図面を表示しています。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   新しい名前を持つドキュメントを保存するという名前のディレクトリ`Test`である必要があります、 *My Documents*フォルダー (Windows XP 以前) または*ドキュメント*フォルダー (Windows Vista)。  
  
## <a name="see-also"></a>関連項目  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷します。](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  