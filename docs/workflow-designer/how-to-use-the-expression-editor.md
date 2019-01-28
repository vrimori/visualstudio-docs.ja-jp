---
title: ワークフロー デザイナー - 方法。式エディターを使用する
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c6d2bf026295d899f2bd0aee05eccb8013eedf0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967259"
---
# <a name="how-to-use-the-expression-editor"></a>方法: 式エディターを使用する

式エディターは、多くのワークフロー アクティビティで入力し、式の評価に使用するワークフロー デザイナー コントロールです。 式エディターは、編集、IntelliSense など、エクスペリエンスの色付け、本格的な IDE を提供します。 パラメーター情報、他の機能の 1 つのエラーの波線。 コンパイラは、入力された後に、式を検証します。 式が無効な場合は、エラー アイコンが表示されます。 として、エディターを開くことも、**式エディター**  ダイアログ ボックス。

式は、引数またはプロパティにバインドされたリテラル値または Visual Basic コードです。 新しい値を生成する操作を組み合わせて値要素 (たとえば、変数、定数、リテラル、プロパティなど) が含まれます。 アプリケーションが C# を使用したプログラムに含まれている場合でも、式の記述には VB.NET 構文が使用されます。 つまり、大文字小文字は区別されません、1 つの等号を使用して比較を実行 (「=」「= =」ではなく) に署名をブール演算子は、単語「と」とシンボルではなく「または」"(& a) (& a)"と"| |"、および**何も**使用代わりに**null**します。 式および Visual Basic における演算子の詳細については、およびサンプルは、「 [Visual Basic の演算子よぶ式](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100))します。

**式エディター**ように動作します。

- フォーカスがない場合、式エディターは通常の TextBlock コントロールと同様の外観になります。

- フォーカスが式エディターに移ると、式エディター コントロールと同様の外観と動作になります。 フォーカスを失った後、式エディターはもう一度通常の TextBlock のようになります。

- 再ホストされたワークフロー デザイナーで式エディターにフォーカスを設定した場合は、TextBox と同じように動作します。 再ホストされたワークフロー デザイナーでフォーカスが失われると、式エディターは、通常の TextBlock と同様の外観に戻ります。

> [!NOTE]
> 式エディターの IntelliSense は Visual Studio 内でのみ使用できます。 Visual Studio と再ホストされたシナリオの両方では、コンパイラは、入力されていることと、式エディターは、式が有効でない場合にエラー アイコンを表示した後に式を検証します。

## <a name="use-the-expression-editor"></a>式エディターを使用する

1.  Visual Studio で、新規または既存のワークフロー プロジェクトを開きます。

2.  ワークフローに <xref:System.Activities.Statements.Assign> などのアクティビティを追加します。

    > [!NOTE]
    > 式エディターを使用できるワークフロー アクティビティは複数あります。 変数デザイナー、引数デザイナー、および動的引数デザイナーには、式 TextBlock も表示されます。 ここでは、例として <xref:System.Activities.Statements.Assign> アクティビティを使用しています。

3.  <xref:System.Activities.Statements.Assign> アクティビティのアクティビティ デザイナーで、左側の式エディターをクリックします。

     灰色のウォーターマークの文字列**\<に >** と **\<VB の式を入力してください >** の式エディターに既定値をテキスト文字列は、<xref:System.Activities.Statements.Assign>アクティビティ。

4.  式を入力します。 文字列を入力する場合は、文字列を引用符で囲みます。 式の引数を変数にバインドする場合は、引用符を省略してください。

     完了すると、リージョンまたはデザイナーの別の部分にフォーカスを移動して式エディターの外部で領域を選択します。 フォーカスをシフトすると、前述のように、式を検証するコンパイラがさせます。

     入力するか、式を編集する別の方法では、プロパティ グリッドでプロパティ名の横にある省略記号をクリックします。 省略記号を選択すると表示、**式エディター**  ダイアログ ボックス。

## <a name="see-also"></a>関連項目

- <xref:System.Activities.Presentation.View.ExpressionTextBox>