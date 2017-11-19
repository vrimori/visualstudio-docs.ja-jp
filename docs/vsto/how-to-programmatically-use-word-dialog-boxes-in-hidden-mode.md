---
title: "方法: プログラムによって Word のダイアログ ボックスを非表示モードで使用して |Microsoft ドキュメント"
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
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: daf5cfb79c16a26b871e2c4d07ec304c17cb6a33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>方法: プログラムによって Word のダイアログ ボックスを非表示モードで使用する
  ユーザーに表示することがなく、Microsoft Office Word の組み込みダイアログ ボックスを呼び出すことによって、1 つのメソッドの呼び出しで複雑な操作を行うことができます。 使用してこれを行う、<xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Dialog>オブジェクトを呼び出さず、<xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>メソッドです。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>例  
 次のコード例を使用する方法を示します、**ページ セットアップ**プロパティを設定する複数のページのセットアップ ユーザー入力なしで非表示モードでのダイアログ ボックス。 例を使用して、<xref:Microsoft.Office.Interop.Word.Dialog>カスタム ページ サイズを構成するオブジェクト。 ページ設定 の上余白、下の余白などの特定の設定はの遅延バインディングのプロパティとして使用できます、<xref:Microsoft.Office.Interop.Word.Dialog>オブジェクト。 これらのプロパティは、実行時に Word によって動的に作成されます。  
  
 次の例は、Visual Basic プロジェクトでこのタスクを実行する方法を示します、 **Option Strict**は off および Visual c# プロジェクトで、対象とする、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]です。 これらのプロジェクトでは、Visual Basic および Visual c# コンパイラで遅延のバインド機能を使用できます。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`プロジェクト内のクラスです。  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 次の例は、Visual Basic プロジェクトでこのタスクを実行する方法を示します、 **Option Strict**にします。 これらのプロジェクトでは、リフレクションを使用して、遅延バインディングのプロパティにアクセスする必要があります。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`プロジェクト内のクラスです。  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって Word の組み込みダイアログ ボックスを使用](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Office ソリューションの遅延バインディング](../vsto/late-binding-in-office-solutions.md)   
 [リフレクション (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [リフレクション (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  