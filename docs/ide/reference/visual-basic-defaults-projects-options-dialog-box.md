---
title: '[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a558fa33760645648b427c3f6cc95991d601c483
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934505"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])
Visual Basic プロジェクトのオプションに対する既定の設定を指定します。 新しいプロジェクトを作成すると、指定したオプション ステートメントがコード エディターのプロジェクト ヘッダーに追加されます。 このオプションは、すべての Visual Basic プロジェクトに適用されます。

 このダイアログ ボックスにアクセスするには、**[ツール]** メニューの **[オプション]** をクリックし、**[プロジェクトおよびソリューション]** フォルダーを展開して、**[Visual Basic の既定値]** をクリックします。

 **Option Explicit**

 明示的な変数の宣言が必要となるように、コンパイラの既定値を設定します。 既定では、**[Option Explicit]** は **[On]** に設定されています。 詳細については、「[/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)」を参照してください。

 **Option Strict**

 明示的な縮小変換を必要とし、遅延バインディングが許可されるように、コンパイラの既定値を設定します。 既定では、**[Option Strict]** は **[Off]** に設定されています。 詳細については、「[/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)」を参照してください。

 **Option Compare**

 文字列比較でのコンパイラの既定値を設定します。[binary] (大文字と小文字を区別する) または [text] (大文字と小文字を区別しない) を設定できます。既定では、**[Option Compare]** は **[Binary]** に設定されています。 詳細については、「[/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)」を参照してください。

 **Option Infer**

 ローカル型の推論についてのコンパイラの既定値を設定します。 既定では、新しく作成されたプロジェクトの場合は **[Option Infer]** が **[On]** に設定され、以前のバージョンの Visual Basic で作成されて移行されたプロジェクトの場合は **[Off]** に設定されます。 詳細については、「[/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)」を参照してください。

## <a name="see-also"></a>「

- [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)