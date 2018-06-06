---
title: Microsoft Office Excel Keyboard、Microsoft Office Keyboard 設定オプション ダイアログ ボックス
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
ms.openlocfilehash: fc71c699dfea11b8654791efdd52e4c0751a9762
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692448"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel Keyboard、Microsoft Office Keyboard 設定オプション ダイアログ ボックス
  Microsoft Office Excel および Visual Studio 両方のショートカット キーを処理します。 同じショートカット キーの組み合わせは、Excel では Visual Studio での異なるコマンドのスタンバイことができます。 Excel で開いている場合、ドキュメント レベルのプロジェクトを Visual Studio で、一度に 1 つだけのアプリケーションは、ショートカット キーのコマンドを受信します。 既定では、Visual Studio はすべてのショートカット キー コマンドを受け取りますが、Excel のドキュメントにフォーカスがある場合を選択して受信を行うことができます**ダイナミック キーボード スキーム**です。  
  
 ショートカット キーが処理されているアプリケーションでのコマンドに割り当てられているショートカット キーを使用する場合、その他のアプリケーションには、ショートカット キーは渡されます。  
  
 選択したオプションは、変更するまで Excel プロジェクトの有効になります。 選択範囲では Microsoft Office Word プロジェクト; 影響しませんMicrosoft Office Word キーボード オプションを使用して Word 用のすべての変更を行う必要があります。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **Visual Studio キーボード スキーム**  
 Visual Studio は、Excel にフォーカスがある場合でも、すべてのショートカット キー コマンドを受信します。 たとえば、ファンクション キーを押して**f5 キーを押して**がソリューションのデバッグ フォーカスを Excel には、Visual Studio を起動します。  
  
 **動的なキーボード スキーム**  
 Visual Studio は、フォーカスがあるときにのみ、ショートカット キーのコマンドを受信します。 Excel にフォーカスがある場合は、Excel は、すべてのショートカット キーのコマンドを受信します。 たとえば、ファンクション キーを押して**f5 キーを押して**フォーカスを Excel には、Excel が開かれ、**ジャンプ** ダイアログ ボックス。 キーを押す場合**f5 キーを押して**がソリューションのデバッグ フォーカスを Visual Studio には、Visual Studio を起動します。  
  
## <a name="see-also"></a>関連項目  
 [Microsoft Office Word Keyboard、Microsoft Office Keyboard 設定オプション ダイアログ ボックス](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  