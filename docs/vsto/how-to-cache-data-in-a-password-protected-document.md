---
title: "方法 : パスワードで保護されたドキュメント内のデータをキャッシュする"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "データ [Visual Studio での Office 開発], キャッシュ"
  - "データ キャッシュ [Visual Studio での Office 開発], 保護されたドキュメント"
  - "データセット [Visual Studio での Office 開発], キャッシュ"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 方法 : パスワードで保護されたドキュメント内のデータをキャッシュする
  パスワードで保護された文書またはブックのデータ キャッシュにデータを追加した場合、キャッシュされたデータへの変更は自動的に保存されません。  プロジェクトで 2 つのメソッドをオーバーライドすることによって、キャッシュされたデータへの変更を保存できます。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Word 文書のキャッシュ  
  
#### パスワードで保護された Word 文書内のデータをキャッシュするには  
  
1.  `ThisDocument` クラスで、キャッシュの対象とするパブリック フィールドまたはプロパティを指定します。  詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。  
  
2.  `ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> メソッドをオーバーライドし、文書の保護を解除します。  
  
     文書が保存されると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] はこのメソッドを呼び出し、ユーザーには文書の保護を解除する機会が与えられます。  これにより、キャッシュされたデータへの変更を保存できるようになります。  
  
3.  `ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> メソッドをオーバーライドし、文書に保護を再適用します。  
  
     文書が保存されると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] はこのメソッドを呼び出し、ユーザーには文書の保護を再適用する機会が与えられます。  
  
### 例  
 次のコード例は、パスワードで保護されている Word 文書のデータをキャッシュする方法を示しています。  コードでは、<xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> メソッドで保護を解除する前に、現在の <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> 値を保存します。こうして、<xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> メソッドを使用して同じ種類の保護を再適用できるようにします。  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/VB/ThisDocument.vb#1)]  
  
### コードのコンパイル  
 このコードをプロジェクトの `ThisDocument` クラスに追加します。  このコードでは、パスワードは `securelyStoredPassword` という名前のフィールドに格納されていることを前提としています。  
  
## Excel ブックのキャッシュ  
 Excel プロジェクトでこの手順が必要になるのは、<xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> メソッドを使用してブック全体をパスワードで保護している場合だけです。  <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> メソッドを使用して特定のワークシートだけをパスワードで保護している場合は、この手順は必要ありません。  
  
#### パスワードで保護された Excel ブック内のデータをキャッシュするには  
  
1.  `ThisWorkbook` クラスまたはいずれかの `Sheet`*n* クラスで、キャッシュの対象とするパブリック フィールドまたはプロパティを指定します。  詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。  
  
2.  `ThisWorkbook` クラスの <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> メソッドをオーバーライドし、ブックの保護を解除します。  
  
     ブックが保存されると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] はこのメソッドを呼び出し、ユーザーにはブックの保護を解除する機会が与えられます。  これにより、キャッシュされたデータへの変更を保存できるようになります。  
  
3.  `ThisWorkbook` クラスの <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> メソッドをオーバーライドし、文書に保護を再適用します。  
  
     ブックが保存されると、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] はこのメソッドを呼び出し、ユーザーにはブックの保護を再適用する機会が与えられます。  
  
### 例  
 次のコード例は、パスワードで保護されている Excel ブックのデータをキャッシュする方法を示しています。  コードでは、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> メソッドで保護を解除する前に、現在の <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> 値と <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> 値を保存します。こうして、<xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> メソッドを使用して同じ種類の保護を再適用できるようにします。  
  
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/VB/ThisWorkbook.vb#1)]  
  
### コードのコンパイル  
 このコードをプロジェクトの `ThisWorkbook` クラスに追加します。  このコードでは、パスワードは `securelyStoredPassword` という名前のフィールドに格納されていることを前提としています。  
  
## 参照  
 [キャッシュされたデータ](../vsto/caching-data.md)   
 [方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [方法 : Office ドキュメント内のデータ ソースをプログラムでキャッシュする](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  