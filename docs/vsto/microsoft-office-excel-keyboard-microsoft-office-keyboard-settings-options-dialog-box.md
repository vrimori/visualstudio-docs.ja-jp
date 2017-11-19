---
title: "Microsoft Office Excel キーボード、Microsoft Office Keyboard 設定オプション ダイアログ ボックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords: keyboard shortcuts, Office development in Visual Studio
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 57e3edf9b8d3f81ebbed6a02f2ff3097321f8074
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>[Microsoft Office Excel Keyboard] ([オプション] ダイアログ ボックス - [Microsoft Office Keyboard 設定])
  Microsoft Office Excel および Visual Studio 両方のショートカット キーを処理します。 同じショートカット キーの組み合わせは、Excel では Visual Studio での異なるコマンドのスタンバイことができます。 Excel で開いている場合、ドキュメント レベルのプロジェクトを Visual Studio で、一度に 1 つだけのアプリケーションは、ショートカット キーのコマンドを受信します。 既定では、Visual Studio はすべてのショートカット キー コマンドを受け取りますが、Excel のドキュメントにフォーカスがある場合を選択して受信を行うことができます**ダイナミック キーボード スキーム**です。  
  
 ショートカット キーが処理されているアプリケーションでのコマンドに割り当てられているショートカット キーを使用する場合、その他のアプリケーションには、ショートカット キーは渡されます。  
  
 選択したオプションは、変更するまで Excel プロジェクトの有効になります。 選択範囲では Microsoft Office Word プロジェクト; 影響しませんMicrosoft Office Word キーボード オプションを使用して Word 用のすべての変更を行う必要があります。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **Visual Studio キーボード スキーム**  
 Visual Studio は、Excel にフォーカスがある場合でも、すべてのショートカット キー コマンドを受信します。 たとえば、Excel にフォーカスがあるときに、F5 キーを押すと、Visual Studio は、ソリューションのデバッグを開始します。  
  
 **動的なキーボード スキーム**  
 Visual Studio は、フォーカスがあるときにのみ、ショートカット キーのコマンドを受信します。 Excel にフォーカスがある場合は、Excel は、すべてのショートカット キーのコマンドを受信します。 たとえば、F5 キーをキーを押すと、Excel にフォーカスがある場合は、Excel が開かれ、**ジャンプ** ダイアログ ボックス。 Visual Studio にフォーカスがあるときに、f5 キーを押して、Visual Studio は、ソリューションのデバッグを開始します。  
  
## <a name="see-also"></a>関連項目  
 [[Microsoft Office Word Keyboard] ([オプション] ダイアログ ボックス - [Microsoft Office Keyboard 設定])](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  