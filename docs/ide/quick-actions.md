---
title: クイック アクション、電球、ねじ回し
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7089a9a654d1c346fefcca119f74a87d89f323b8
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349375"
---
# <a name="quick-actions"></a>クイック アクション

クイック アクションを使うと、コードのリファクタリング、生成、その他の変更を、1 つの操作で簡単に行うことができます。 クイック アクションは、C#、[C++](/cpp/ide/writing-and-refactoring-code-cpp)および Visual Basic のコード ファイルで使用できます。 クイック アクションには、言語に固有のものと、すべての言語が対象になるものがあります。

クイック アクションを使用して、次の操作を実行できます。

- [コード アナライザー](../code-quality/roslyn-analyzers-overview.md)の規則違反に対してコード修正を適用する
- コード アナライザーの規則違反を[抑制する](../code-quality/use-roslyn-analyzers.md)
- リファクタリングを適用する (例: [一時変数をインライン化する](../ide/reference/inline-temporary-variable.md))
- コードを生成する (例: [ローカル変数を導入する](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> このトピックは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac については、「[リファクタリング (Visual Studio for Mac)](/visualstudio/mac/refactoring)」を参照してください。

クイック アクションは、電球 ![電球アイコン](media/light-bulb-icon.png) アイコンまたはねじ回し ![ねじ回しアイコン](media/screwdriver-icon.png) アイコンを使うか、適切なコード行にカーソルを置いて **Ctrl**+**.** キーを押すと 利用できます。 エラーを示す赤い波線があり、Visual Studio にそのエラーに対処するために使用可能な解決策がある場合は、エラー電球 ![エラー電球アイコン](media/error-light-bulb-icon.png) が表示されます。

いずれの言語でも、サードパーティは、たとえば SDK の一部として、カスタマイズした診断や提案を表示できます。Visual Studio はそれらの規則に基づいて電球マークを表示します。

## <a name="icons"></a>アイコン

クイック アクションが使用可能なときに表示されるアイコンは、使用可能な解決策またはリファクタリングの種類を示します。 *ねじ回し*![ねじ回しアイコン](media/screwdriver-icon.png) アイコンは、コードを変更するのに使用可能なアクションがあることを示すだけで、必ずしもそれらを使用する必要はありません。 *黄色の電球* ![電球アイコン](media/light-bulb-icon.png) アイコンは、コードを改善するために実行する*必要がある*使用可能なアクションがあることを示します。 *エラー電球* ![エラー電球アイコン](media/error-light-bulb-icon.png) アイコンは、コード内のエラーを修正するために使用可能なアクションがあることを示します。

## <a name="to-see-a-light-bulb-or-screwdriver"></a>電球やねじ回しを表示するには

- 解決策が使用可能な場合は、エラーの場所にマウス ポインターを置くと、電球が自動的に表示されます。

   ![電球でのマウス ホバー](../ide/media/vs2015_lightbulb_hover.png)

- キャレットをクイック アクションが使用できるコード行に移動すると、エディターの左余白に電球とねじ回しが表示されます。

- 行の任意の場所で **Ctrl**+**.** キーを押すと、 使用可能なクイック アクションとリファクタリングの一覧が表示されます。

## <a name="to-see-potential-fixes"></a>修正候補を表示するには

電球の横の下矢印を選択するか、**[修正候補を表示する]** リンクを選択すると、使用可能なクイック アクションのリストが表示されます。

![拡大電球](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>関連項目

- [Visual Studio でのコード生成](../ide/code-generation-in-visual-studio.md)
- [共通のクイック アクション](../ide/common-quick-actions.md)
- [コード スタイルとクイック アクション](../ide/code-styles-and-quick-actions.md)
- [コードの記述とリファクタリング (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [リファクタリング (Visual Studio for Mac)](/visualstudio/mac/refactoring)