---
title: Microsoft Office Excel キーボード、Microsoft Office Keyboard 設定オプション ダイアログ ボックス |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
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
ms.openlocfilehash: 1f052ef4774fe4d5cd4c119eaaf09ed715a2fdbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
  