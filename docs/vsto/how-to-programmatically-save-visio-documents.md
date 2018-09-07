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
ms.openlocfilehash: 4171f0237b7735748da567bd9482856c013759bc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673195"
---
# <a name="how-to-programmatically-save-visio-documents"></a>方法: プログラムによって Visio 図面を保存
  Microsoft Office Visio 図面を保存するには、次のようないくつかの方法があります。  
  
-   既存の図面に変更を保存する。  
  
-   新しい図面を保存するか、または新しい名前を付けて図面を保存する。  
  
-   引数を指定して図面を保存する。  
  
 詳細については、 [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) メソッド、 [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) メソッド、および [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="save-an-existing-document"></a>既存のドキュメントを保存します。  
  
### <a name="to-save-a-document"></a>図面を保存するには  
  
-   呼び出す、`Microsoft.Office.Interop.Visio.Document.Save`のメソッド、`Microsoft.Office.Tools.Visio.Document`以前に保存されたドキュメントのクラス。  
  
     このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  `Microsoft.Office.Interop.Visio.Document.Save`新しい Visio ドキュメントが保存されていない場合、メソッドが例外をスローします。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>新しい名前を持つドキュメントを保存します。  
 使用して、`Microsoft.Office.Interop.Visio.Document.SaveAs`メソッドを新しいドキュメント、または新しい名前を持つドキュメントを保存します。 このメソッドでは、新しいファイル名を指定する必要があります。  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>作業中の Visio 図面に新しい名前を付けて保存するには  
  
-   呼び出す、`Microsoft.Office.Interop.Visio.Document.SaveAs`のメソッド、`Microsoft.Office.Tools.Visio.Document`ファイル名を含む完全修飾パスを使用して、保存することです。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、そのファイルは警告なしで上書きされます。  
  
     このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>新しい名前および指定した引数で文書を保存します。  
 使用して、`Microsoft.Office.Interop.Visio.Document.SaveAsEx`メソッドを新しい名前を持つドキュメントを保存し、ドキュメントに適用する適用可能な引数を指定します。  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>新しい名前および指定した引数を使用して図面を保存するには  
  
-   呼び出す、`Microsoft.Office.Interop.Visio.Document.SaveAsEx`のメソッド、`Microsoft.Office.Tools.Visio.Document`ファイル名を含む完全修飾パスを使用して、保存することです。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、例外がスローされます。  
  
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
  
  