---
title: '方法: プログラムでドキュメントにヘッダーとフッターを追加します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: e06c59fc61bff25268acc1ab70a90b68a1b9101d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848455"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>方法: プログラムでドキュメントにヘッダーとフッターを追加します。
  文書のヘッダーおよびフッターにテキストを追加するには、<xref:Microsoft.Office.Interop.Word.Section> の <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> プロパティおよび <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> プロパティを使用します。 文書の各セクションには、次の 3 つのヘッダーとフッターが含まれています。  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
  ドキュメント レベルのカスタマイズと VSTO アドインでは、手順が異なります。  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>ドキュメント レベルのカスタマイズ  
 次のコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
### <a name="to-add-text-to-footers-in-the-document"></a>文書のフッターにテキストを追加するには  
  
1.  文書の各セクションのプライマリ フッターに挿入するテキストのフォントを設定し、フッターにテキストを挿入するコード例を次に示します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
### <a name="to-add-text-to-headers-in-the-document"></a>文書のヘッダーにテキストを追加するには  
  
1.  文書の各ヘッダーにページ番号を表示するフィールドを追加し、ヘッダーのテキストが右揃えになるように段落の配置を設定するコード例を次に示します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>VSTO アドイン  
 次のコード例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
### <a name="to-add-text-to-footers-in-a-document"></a>文書のフッターにテキストを追加するには  
  
1.  文書の各セクションのプライマリ フッターに挿入するテキストのフォントを設定し、フッターにテキストを挿入するコード例を次に示します。 このコード例では作業中のドキュメントを使用します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
### <a name="to-add-text-to-headers-in-the-document"></a>文書のヘッダーにテキストを追加するには  
  
1.  文書の各ヘッダーにページ番号を表示するフィールドを追加し、ヘッダーのテキストが右揃えになるように段落の配置を設定するコード例を次に示します。 このコード例では作業中のドキュメントを使用します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムで新しいドキュメントを作成します。](../vsto/how-to-programmatically-create-new-documents.md)   
 [方法: プログラムによってドキュメント内の範囲を拡張します。](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [方法: プログラムによって文書で見つかった項目をループします。](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
