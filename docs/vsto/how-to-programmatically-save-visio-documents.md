---
title: "方法: プログラムによって Visio 図面を保存 |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c255c481123ef4159d63ad87d9c8fa2ac97cbdae
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-visio-documents"></a>方法: プログラムによって Visio 図面を保存する
  Microsoft Office Visio 図面を保存するには、次のようないくつかの方法があります。  
  
-   既存の図面に変更を保存する。  
  
-   新しい図面を保存するか、または新しい名前を付けて図面を保存する。  
  
-   引数を指定して図面を保存する。  
  
 詳細については、 [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) メソッド、 [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) メソッド、および [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) メソッドの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="saving-an-existing-document"></a>既存の図面を保存する  
  
#### <a name="to-save-a-document"></a>図面を保存するには  
  
-   以前に保存されたドキュメントの Microsoft.Office.Tools.Visio.Document クラスの Microsoft.Office.Interop.Visio.Document.Save メソッドを呼び出します。  
  
     このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  Microsoft.Office.Interop.Visio.Document.Save メソッドは、新しい Visio ドキュメントが保存されていない場合に、例外をスローします。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>新しい名前を付けて図面を保存する  
 Microsoft.Office.Interop.Visio.Document.SaveAs メソッドを使用して、新しいドキュメント、または新しい名前を持つドキュメントを保存します。 このメソッドでは、新しいファイル名を指定する必要があります。  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>作業中の Visio 図面に新しい名前を付けて保存するには  
  
-   ファイル名を含む完全修飾パスを使用して、保存する Microsoft.Office.Tools.Visio.Document の Microsoft.Office.Interop.Visio.Document.SaveAs メソッドを呼び出します。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、そのファイルは警告なしで上書きされます。  
  
     このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>新しい名前および指定した引数を使用して図面を保存する  
 Microsoft.Office.Interop.Visio.Document.SaveAsEx メソッドを使用して、新しい名前を持つドキュメントを保存して、ドキュメントに適用する適用可能な引数を指定します。  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>新しい名前および指定した引数を使用して図面を保存するには  
  
-   ファイル名を含む完全修飾パスを使用して、保存する Microsoft.Office.Tools.Visio.Document の Microsoft.Office.Interop.Visio.Document.SaveAsEx メソッドを呼び出します。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、例外がスローされます。  
  
     次のコード例では、作業中の図面を新しい名前で保存し、その図面を読み取り専用としてマークし、[直前に使用] の図面一覧にその図面を表示しています。 このコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   図面に新しい名前を付けて保存するには、[マイ ドキュメント] フォルダー (Windows XP 以前の場合) または [ドキュメント] フォルダー (Windows Vista の場合) 内に `Test` という名前のディレクトリが存在している必要があります。  
  
## <a name="see-also"></a>参照  
 [Visio ソリューション](../vsto/visio-solutions.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [方法: プログラムによって新しい Visio 図面を作成します。](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [方法: プログラムによって Visio 図面を開く](../vsto/how-to-programmatically-open-visio-documents.md)   
 [方法: プログラムによって Visio 図面を閉じる](../vsto/how-to-programmatically-close-visio-documents.md)   
 [方法: プログラムによって Visio 図面を印刷する](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  