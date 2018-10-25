---
title: '方法: プログラムによって検索後に選択内容を復元'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e714773ec000f2f46872f5c60429f313e1f6310
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891155"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>方法: プログラムによって検索後に選択内容を復元
  検索および、ドキュメント内のテキストを置換する場合、検索が完了した後に、ユーザーの元の選択を復元する場合があります。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 コード サンプルの手順で 2 つの利用<xref:Microsoft.Office.Interop.Word.Range>オブジェクト。 現在のストアをいずれか<xref:Microsoft.Office.Interop.Word.Selection>、および 1 つ検索範囲として使用するドキュメント全体を設定します。  
  
## <a name="to-restore-the-users-original-selection-after-a-search"></a>ユーザーの検索後に元の選択範囲を復元するには  
  
1. 作成、<xref:Microsoft.Office.Interop.Word.Range>ドキュメントと現在の選択範囲のオブジェクト。  
  
    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2. 検索を実行し、操作を置き換えます。  
  
    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3. ユーザーの元の選択範囲を復元する開始範囲を選択します。  
  
    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
   このメソッドを使ったサンプル コード全体を次に示します。  
  
## <a name="example"></a>例  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって検索し、文書内のテキストを置換](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [方法: プログラムによって Word の検索オプションを設定](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [方法: プログラムによって文書で見つかった項目をループ](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  