---
title: '方法: プログラムによって Word のダイアログ ボックスを非表示モードでを使用して、'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0594bea01d8b6fb5cef993a2704beb658b513c48
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819628"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>方法: プログラムによって Word のダイアログ ボックスを非表示モードでを使用して、
  ユーザーに表示することがなく、Microsoft Office Word の組み込みダイアログ ボックスを呼び出すことによって、1 つのメソッドの呼び出しで複雑な操作を実行できます。 使用してこれを行う、<xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Dialog>呼び出さずにオブジェクト、<xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>メソッド。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>使用例  
 次のコード例を使用する方法を示します、**ページ セットアップ**ユーザー入力なしで複数のページ設定プロパティを設定する非表示モードでのダイアログ ボックス。 例を使用して、<xref:Microsoft.Office.Interop.Word.Dialog>カスタム ページのサイズを構成するオブジェクト。 ページ設定 の上余白、下の余白などの特定の設定がの遅延バインディング プロパティとして使用できますが、<xref:Microsoft.Office.Interop.Word.Dialog>オブジェクト。 これらのプロパティは、実行時に Word によって動的に作成されます。  
  
 次の例は、Visual Basic プロジェクトでこのタスクを実行する方法を示します、 **Option Strict**オフ、および Visual c# プロジェクトを対象とするが、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]します。 これらのプロジェクトでは、Visual Basic および Visual c# コンパイラで遅延バインディングの機能を使用できます。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`プロジェクト内のクラス。  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 次の例は、Visual Basic プロジェクトでこのタスクを実行する方法を示します、 **Option Strict**にします。 これらのプロジェクトでは、リフレクションを使用して、遅延バインディングのプロパティにアクセスする必要があります。 この例を使用する実行から、`ThisDocument`または`ThisAddIn`プロジェクト内のクラス。  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって Word の組み込みダイアログ ボックスを使用して、](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Office ソリューションの遅延バインディング](../vsto/late-binding-in-office-solutions.md)   
 [リフレクション (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [リフレクション (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
