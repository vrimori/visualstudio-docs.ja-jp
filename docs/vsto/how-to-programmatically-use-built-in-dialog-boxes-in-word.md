---
title: "方法: プログラムによって Word の組み込みダイアログ ボックスを使用して |Microsoft ドキュメント"
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
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 961f6ac2aa9852170ecce35aa18ce4c39d7a9983
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>方法: プログラムによって Word の組み込みダイアログ ボックスを使用する
  Microsoft Office Word を使用する場合は、ユーザー入力のダイアログ ボックスを表示する必要がある場合もがあります。 公開されている、Word の組み込みダイアログ ボックスを使用する方法を取る可能性がありますも作成できますが、自分、<xref:Microsoft.Office.Interop.Word.Dialogs>のコレクション、<xref:Microsoft.Office.Interop.Word.Application>オブジェクト。 これにより、200 以上の列挙型として表される組み込みダイアログ ボックスにアクセスすることができます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>ダイアログ ボックスを表示します。  
 ダイアログ ボックスを表示するには、値のいずれかの操作を使用して、<xref:Microsoft.Office.Interop.Word.WdWordDialog>列挙体を作成する、<xref:Microsoft.Office.Interop.Word.Dialog>を表示するダイアログ ボックスを表すオブジェクト。 次に、呼び出し、<xref:Microsoft.Office.Interop.Word.Dialog.Show%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Dialog>オブジェクト。  
  
 次のコード例を表示する方法を示しています、**ファイルを開く** ダイアログ ボックス。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`プロジェクト内のクラスです。  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>遅延バインディングで使用できるダイアログ ボックスのメンバーにアクセスします。  
 一部のプロパティと Word のダイアログ ボックスのメソッドは、遅延バインディングを介してのみ使用します。 Visual basic プロジェクト where **Option Strict**は、リフレクションを使用してこれらのメンバーにアクセスする必要があります。 詳細については、「 [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md)」を参照してください。  
  
 次のコード例を使用する方法を示しています、**名前**のプロパティ、**ファイルを開く** ダイアログ ボックスで、Visual Basic プロジェクト where **Option Strict** off または Visual c# では、対象とするプロジェクト、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]です。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`プロジェクト内のクラスです。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 次のコード例は、リフレクションを使用してアクセスする方法を示します、**名前**のプロパティ、**ファイルを開く** ダイアログ ボックスで、Visual Basic プロジェクト where **Option Strict**はします。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`プロジェクト内のクラスです。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>参照  
 [方法: プログラムによって Word のダイアログ ボックスを非表示モードで使用します。](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict ステートメント](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [リフレクション (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [リフレクション (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  