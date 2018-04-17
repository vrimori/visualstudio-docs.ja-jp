---
title: Microsoft Office Word キーボード、Microsoft Office Keyboard 設定オプション ダイアログ ボックス |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d8747485ced6309bf9e63ecf864c67a111ce6c47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>[Microsoft Office Word Keyboard] ([オプション] ダイアログ ボックス - [Microsoft Office Keyboard 設定])
  Microsoft Office Word および Visual Studio 両方のショートカット キーを処理します。 同じショートカット キーの組み合わせは、Word では Visual Studio での異なるコマンドのスタンバイことができます。 Word で開いている場合、ドキュメント レベルのプロジェクトを Visual Studio で、一度に 1 つだけのアプリケーションは、ショートカット キーのコマンドを受信します。 既定では、Visual Studio はすべてのショートカット キー コマンドを受け取りますが、Word のドキュメントにフォーカスがある場合を選択して受信を行うことができます**ダイナミック キーボード スキーム**です。  
  
 ショートカット キーが処理されているアプリケーションでのコマンドに割り当てられているショートカット キーを使用する場合、その他のアプリケーションには、ショートカット キーは渡されます。  
  
 選択したオプションは、変更するまで Word プロジェクトの有効になります。 選択範囲では Microsoft Office Excel プロジェクトには影響しませんMicrosoft Office Excel キーボード オプションを使用して Excel 用のすべての変更を行う必要があります。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **Visual Studio キーボード スキーム**  
 Visual Studio は、Word 文書にフォーカスがある場合でも、すべてのショートカット キー コマンドを受信します。 たとえば、ドキュメントにフォーカスがあるときに、F5 キーを押すと、Visual Studio は、ソリューションのデバッグを開始します。  
  
 **動的なキーボード スキーム**  
 Visual Studio は、フォーカスがあるときにのみ、ショートカット キーのコマンドを受信します。 Word 文書にフォーカスがある場合は、Word がショートカット キーのすべてのコマンドを受信します。 たとえば、Word 文書にフォーカスがあるときに、F5 キーを押すと、開かれます、**検索し、置換** ダイアログ ボックスで、**ジャンプ**タブを選択します。 Visual Studio にフォーカスがあるときに、f5 キーを押して、Visual Studio は、ソリューションのデバッグを開始します。  
  
## <a name="see-also"></a>関連項目  
 [[Microsoft Office Excel Keyboard] ([オプション] ダイアログ ボックス - [Microsoft Office Keyboard 設定])](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  