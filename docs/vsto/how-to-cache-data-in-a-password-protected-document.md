---
title: '方法: パスワードで保護されたドキュメント内のデータをキャッシュ |Microsoft ドキュメント'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 71ce65cd253ea6473a07a98542449a1e47ae9d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>方法 : パスワードで保護されたドキュメント内のデータをキャッシュする
  ドキュメントまたはパスワードで保護されているブック内のデータ キャッシュにデータを追加する場合、キャッシュされたデータへの変更は自動的に保存されません。 プロジェクト内の 2 つのメソッドをオーバーライドすることで、キャッシュされたデータに変更を保存できます。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>Word 文書でのキャッシュ  
  
#### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>パスワードで保護されている Word 文書にデータをキャッシュする  
  
1.  `ThisDocument`クラス、パブリック フィールドまたはキャッシュするプロパティをマークします。 詳細については、「 [Caching Data](../vsto/caching-data.md)」を参照してください。  
  
2.  上書き、<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>メソッドで、`ThisDocument`クラスおよびドキュメントの保護を解除します。  
  
     ドキュメントを保存すると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ドキュメントの保護を解除する機会を提供するには、このメソッドを呼び出します。 これにより、キャッシュされたデータを保存するのには変更できます。  
  
3.  上書き、<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>メソッドで、`ThisDocument`クラスおよびドキュメントへの保護を再設定します。  
  
     ドキュメントの保存後、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]保護ドキュメントを再適用する機会を提供するには、このメソッドを呼び出します。  
  
### <a name="example"></a>例  
 次のコード例では、パスワードで保護されている Word 文書内のデータをキャッシュする方法を示します。 コードの保護を削除する前に、<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>メソッド、現在保存<xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A>値に設定することで、同じ種類の保護を再適用することができます、<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>メソッドです。  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compiling-the-code"></a>コードのコンパイル  
 このコードを追加、`ThisDocument`プロジェクト内のクラスです。 このコードは、パスワードがという名前のフィールドに格納される前提としています。`securelyStoredPassword`です。  
  
## <a name="caching-in-excel-workbooks"></a>Excel ブックでのキャッシュ  
 Excel プロジェクトでこの手順は、必要なを使用してパスワードを使用してブック全体を保護する場合にのみ、<xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>メソッドです。 この手順は、パスワードを使用して特定のワークシートのみを使用して保護する場合は必要ありません、<xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>メソッドです。  
  
#### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>パスワードで保護されている Excel ブックにデータをキャッシュする  
  
1.  `ThisWorkbook`クラスまたはのいずれか、 `Sheet` *n*クラス、パブリック フィールドまたはキャッシュするプロパティをマークします。 詳細については、「 [Caching Data](../vsto/caching-data.md)」を参照してください。  
  
2.  上書き、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>メソッドで、`ThisWorkbook`クラスし、ブックの保護を解除します。  
  
     ブックを保存すると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]ブックの保護を解除する機会を提供するには、このメソッドを呼び出します。 これにより、キャッシュされたデータを保存するのには変更できます。  
  
3.  上書き、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>メソッドで、`ThisWorkbook`クラスおよびドキュメントへの保護を再設定します。  
  
     ブックが保存された後、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]保護、ブックを再適用する機会を提供するには、このメソッドを呼び出します。  
  
### <a name="example"></a>例  
 次のコード例では、パスワードで保護されている Excel ブック内のデータをキャッシュする方法を示します。 コードの保護を削除する前に、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>メソッド、現在保存<xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A>と<xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A>で同じ種類の保護を再適用することができるように、値、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>メソッドです。  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compiling-the-code"></a>コードのコンパイル  
 このコードを追加、`ThisWorkbook`プロジェクト内のクラスです。 このコードは、パスワードがという名前のフィールドに格納される前提としています。`securelyStoredPassword`です。  
  
## <a name="see-also"></a>関連項目  
 [データのキャッシュ](../vsto/caching-data.md)   
 [方法: オフラインであるか、サーバーで使用するデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュする](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  