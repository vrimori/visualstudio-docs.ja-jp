---
title: "方法: 印刷時にワークシートのコントロールを非表示にする |Microsoft ドキュメント"
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
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 17ebd691120d1d5aba2623f8178d95c3fc142dee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>方法 : 印刷時にワークシートのコントロールを非表示にする
  Windows フォーム コントロールを含む Microsoft Office Excel ドキュメントを印刷する場合、コントロールは、印刷するワークシートに表示されます。 ワークシートを印刷する場合は、コントロールを非表示にすることができます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  など、データを表示するコントロールを非表示にするかどうか、<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>コントロール内のデータは、印刷するワークシートに表示されません。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>コントロールとワークシートを非表示には、印刷します。  
  
1.  作成または Visual Studio で Excel プロジェクトを開きをことを確認**Sheet1**デザイナーに表示されます。 プロジェクトを作成する方法の詳細については、次を参照してください。[する方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Excel.Controls.Button>でコントロールのセルを`Sheet1`です。  
  
3.  **プロパティ**ウィンドウで、設定、<xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A>プロパティを**False**です。  
  
## <a name="see-also"></a>参照  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [Windows フォームでコントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [方法: Windows フォーム コントロールの Office ドキュメントへの追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [方法: ワークシートのセル内のコントロールをサイズ変更する](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  