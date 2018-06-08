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
ms.openlocfilehash: 9edd5cd987eb6a4e93b02c8e774adefbc7f969d2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572112"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word Keyboard、Microsoft Office Keyboard 設定オプション ダイアログ ボックス
  Microsoft Office Word および Visual Studio 両方のショートカット キーを処理します。 同じショートカット キーの組み合わせは、Word では Visual Studio での異なるコマンドのスタンバイことができます。 Word で開いている場合、ドキュメント レベルのプロジェクトを Visual Studio で、一度に 1 つだけのアプリケーションは、ショートカット キーのコマンドを受信します。 既定では、Visual Studio はすべてのショートカット キー コマンドを受け取りますが、Word のドキュメントにフォーカスがある場合を選択して受信を行うことができます**ダイナミック キーボード スキーム**です。  
  
 ショートカット キーが処理されているアプリケーションでのコマンドに割り当てられているショートカット キーを使用する場合、その他のアプリケーションには、ショートカット キーは渡されます。  
  
 選択したオプションは、変更するまで Word プロジェクトの有効になります。 選択範囲では Microsoft Office Excel プロジェクトには影響しませんMicrosoft Office Excel キーボード オプションを使用して Excel 用のすべての変更を行う必要があります。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **Visual Studio キーボード スキーム**  
 Visual Studio は、Word 文書にフォーカスがある場合でも、すべてのショートカット キー コマンドを受信します。 たとえば、ファンクション キーを押して**f5 キーを押して**がソリューションのデバッグ、ドキュメントにフォーカスが、Visual Studio を起動します。  
  
 **動的なキーボード スキーム**  
 Visual Studio は、フォーカスがあるときにのみ、ショートカット キーのコマンドを受信します。 Word 文書にフォーカスがある場合は、Word がショートカット キーのすべてのコマンドを受信します。 ファンクション キーを押す場合など、 **f5 キーを押して**Word が開き、Word 文書にフォーカスがあるときに、**検索し、置換**ダイアログ ボックスに、**ジャンプ**タブを選択します。 キーを押す場合**f5 キーを押して**がソリューションのデバッグ フォーカスを Visual Studio には、Visual Studio を起動します。  
  
## <a name="see-also"></a>関連項目  
 [Microsoft Office Excel Keyboard、Microsoft Office Keyboard 設定オプション ダイアログ ボックス](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  