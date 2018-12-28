---
title: '方法: 印刷時にワークシートのコントロールを非表示にします。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 322c314a768545996f343526367de44c667ce89b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646800"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>方法: 印刷時にワークシートのコントロールを非表示にします。
  Windows フォーム コントロールを含む Microsoft Office Excel 文書を印刷する場合、コントロールは、印刷するワークシートに表示されます。 ワークシートを印刷する場合は、コントロールを非表示にすることができます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  など、データを表示するコントロールを非表示にするかどうか、<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>コントロールのデータは、印刷するワークシートに表示されません。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>コントロールとワークシートを非表示には、印刷します。  
  
1.  作成や Visual Studio で Excel プロジェクトを開くことを確認します**Sheet1**デザイナーに表示されます。 プロジェクトの作成方法の詳細については、次を参照してください。[方法。Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Excel.Controls.Button>でコントロールのセルを`Sheet1`します。  
  
3.  **プロパティ**ウィンドウで、設定、<xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A>プロパティを**False**します。  
  
## <a name="see-also"></a>関連項目  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [Office ドキュメントの概要での Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [方法: Office ドキュメントへの Windows フォーム コントロールを追加します。](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [方法: ワークシートのセル内のコントロールをサイズ変更します。](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  