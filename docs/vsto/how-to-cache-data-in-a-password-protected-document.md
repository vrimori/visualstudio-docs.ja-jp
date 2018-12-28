---
title: '方法: パスワードで保護されたドキュメント内のキャッシュ データ'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 21e2b0501b96a1c04cee72487678b3e909440fb4
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647292"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>方法: パスワードで保護されたドキュメント内のキャッシュ データ
  ドキュメントまたはパスワードで保護されているブック内のデータ キャッシュにデータを追加する場合、キャッシュされたデータへの変更は自動的に保存されません。 プロジェクト内の 2 つのメソッドをオーバーライドすることで、キャッシュされたデータに変更を保存できます。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Word 文書でのキャッシュ  
  
### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>パスワードで保護されている Word 文書でデータをキャッシュする  
  
1.  `ThisDocument`クラス、パブリック フィールドまたはキャッシュするプロパティをマークします。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。  
  
2.  上書き、<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>メソッドで、`ThisDocument`クラスし、ドキュメントから保護を削除します。  
  
     ドキュメントを保存するとき、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ドキュメントの保護を解除できるようにするには、このメソッドを呼び出します。 これにより、キャッシュされたデータを保存する変更ができます。  
  
3.  上書き、<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>メソッドで、`ThisDocument`クラスし、保護をドキュメントに再適用します。  
  
     ドキュメントを保存した後、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]保護ドキュメントを再適用する機会を提供するには、このメソッドを呼び出します。  
  
### <a name="example"></a>例  
 次のコード例では、パスワードで保護されている Word 文書内のデータをキャッシュする方法を示します。 コードの保護を削除する前に、<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>メソッド、現在保存<xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A>値で同じ種類の保護を再適用できるように、<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>メソッド。  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compile-the-code"></a>コードのコンパイル  
 このコードを追加、`ThisDocument`プロジェクト内のクラス。 このコードがという名前のフィールドにパスワードを保存することを前提と`securelyStoredPassword`します。  
  
## <a name="cache-in-excel-workbooks"></a>Excel ブック内のキャッシュします。  
 Excel プロジェクトでこの手順は、必要なパスワードを使用してブック全体を使用して保護する場合にのみ、<xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>メソッド。 この手順は、パスワードを使用して特定のワークシートのみを使用して保護する場合は必要ありません、<xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>メソッド。  
  
### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>パスワードで保護されている Excel ブックにデータをキャッシュする  
  
1.  `ThisWorkbook`クラスまたはそのいずれか、 `Sheet` *n*クラス、パブリック フィールドまたはキャッシュするプロパティをマークします。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。  
  
2.  上書き、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>メソッドで、`ThisWorkbook`クラスし、ブックの保護を解除します。  
  
     ブックを保存するとき、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ブックの保護を解除できるようにするには、このメソッドを呼び出します。 これにより、キャッシュされたデータを保存する変更ができます。  
  
3.  上書き、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>メソッドで、`ThisWorkbook`クラスし、保護をドキュメントに再適用します。  
  
     ブックが保存された後、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ブックに保護を再適用する機会を提供するには、このメソッドを呼び出します。  
  
### <a name="example"></a>例  
 次のコード例では、パスワードで保護されている Excel ブック内のデータをキャッシュする方法を示します。 コードの保護を削除する前に、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>メソッド、現在保存<xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A>と<xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A>で同じ種類の保護を再適用できるように、値、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>メソッド。  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compile-the-code"></a>コードのコンパイル  
 このコードを追加、`ThisWorkbook`プロジェクト内のクラス。 このコードがという名前のフィールドにパスワードを保存することを前提と`securelyStoredPassword`します。  
  
## <a name="see-also"></a>関連項目  
 [キャッシュ データ](../vsto/caching-data.md)   
 [方法: オフラインか、サーバーで使用するデータをキャッシュします。](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュします。](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  