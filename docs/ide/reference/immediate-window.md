---
title: イミディエイト ウィンドウ
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91f25f9ab44bee749283603b78744c9e01e4e469
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992634"
---
# <a name="immediate-window"></a>イミディエイト ウィンドウ

**[イミディエイト]** ウィンドウは、式のデバックと評価、ステートメントの実行、変数値の出力などのために使用します。 このモードでは、デバッグ時に、開発言語で評価または実行される式を入力できます。

**[イミディエイト]** ウィンドウを表示するには、編集用にプロジェクトを開いて、**[デバッグ]** > **[ウィンドウ]** > **[イミディエイト]** の順に選択するか、**Ctrl**+**Alt**+**I** キーを押します。 また、**[コマンド]** ウィンドウに「**Debug.Immediate**」と入力することもできます。

**[イミディエイト]** ウィンドウは、個々の Visual Studio コマンドを発行するために使用できます。 使用できるコマンドには、`EvaluateStatement` があります。このコマンドは、変数に値を割り当てるのに使用できます。 **[イミディエイト]** ウィンドウは、IntelliSense もサポートしています。

## <a name="display-the-values-of-variables"></a>変数の値を表示する

**[イミディエイト]** ウィンドウはアプリケーションをデバッグするときに特に役に立ちます。 たとえば、`varA` 変数の値を確認するには、[Print コマンド](../../ide/reference/print-command.md)を使用します。

```cmd
>Debug.Print varA
```

疑問符 (?) は`Debug.Print` のエイリアスであるため、このコマンドは次のように書き換えることもできます。

```cmd
>? varA
```

コマンドをどちらで入力した場合でも、変数 `varA` の値が返されます。

> [!TIP]
> **[イミディエイト]** ウィンドウで Visual Studio コマンドを発行するには、コマンドの先頭に大なり記号 (>) を付ける必要があります。 複数のコマンドを入力するには、**[コマンド]** ウィンドウに切り替えます。

## <a name="design-time-expression-evaluation"></a>デザイン時の式評価

**[イミディエイト]** ウィンドウを使用すると、デザイン時に関数またはサブルーチンを実行できます。

### <a name="execute-a-function-at-design-time"></a>デザイン時に関数を実行する

1. 次のコードを [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] コンソール アプリケーションにコピーします。

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. **[デバッグ]** メニューの **[ウィンドウ]** をポイントし、**[イミディエイト]** をクリックします。

3. **[イミディエイト]** ウィンドウに「`?MyFunction(2)`」と入力し、**Enter** キーを押します。

    **[イミディエイト]** ウィンドウで `MyFunction` が実行され、`4` と表示されます。

関数またはサブルーチンにブレークポイントが含まれている場合、適切なポイントで実行が中断されます。 デバッガー ウィンドウを使用して、プログラムの状態を確認できます。 詳細については、「[チュートリアル:デザイン時のデバッグ](../../debugger/walkthrough-debugging-at-design-time.md)」をご覧ください。

デザイン時の式の評価は、実行時環境の起動を必要とするプロジェクトの種類 ([!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)] プロジェクト、Web プロジェクト、スマート デバイス プロジェクト、SQL プロジェクトなど) には使用できません。

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>デザイン時の式の評価 (複数のプロジェクトから成るソリューションの場合)

デザイン時の式の評価におけるコンテキストを設定する際、Visual Studio はソリューション エクスプローラーで現在選択されているプロジェクトを参照します。 ソリューション エクスプローラーでプロジェクトが選択されていない場合、Visual Studio はスタートアップ プロジェクトで関数を評価します。 現在のコンテキストで関数を評価できない場合は、エラー メッセージが表示されます。 ソリューションのスタートアップ プロジェクト以外のプロジェクトで関数を評価しようとしていたときにエラーを受け取った場合は、ソリューション エクスプローラーで評価対象プロジェクトを選択し、再度評価を試みてください。

## <a name="enter-commands"></a>コマンドを入力する

**[イミディエイト]** ウィンドウで Visual Studio コマンドを発行するときは、大なり記号 (>) を入力する必要があります。 **上方向**キーおよび**下方向**キーを使用して、以前に発行したコマンドの間をスクロールします。

|タスク|ソリューション|例|
|----------|--------------|-------------|
|式を評価する。|式の先頭に疑問符 (?) を付けます。|`? a+b`|
|イミディエイト モードの場合に、一時的にコマンド モードに移行して 1 つのコマンドを実行する。|先頭に不等号 (>) を付けてコマンドを入力します。|`>alias`|
|[コマンド] ウィンドウに切り替る。|先頭に不等号 (>) を付けて、ウィンドウに「`cmd`」と入力します。|`>cmd`|
|[イミディエイト] ウィンドウに戻る。|不等号 (>) を付けずにウィンドウに「`immed`」と入力します。|`immed`|

## <a name="mark-mode"></a>マーク モード

**[イミディエイト]** ウィンドウで、既に出力されている任意の行をクリックすると、自動的にマーク モードに切り替わります。 これにより、テキスト エディターでの操作と同じように、既に入力されたコマンドのテキストを選択、編集、およびコピーし、現在の行に貼り付けることができます。

## <a name="the-equals-sign"></a>等号 (=)

`EvaluateStatement` コマンドをどのウィンドウに入力するかによって、等号 (=) を比較演算子として解釈するのか、代入演算子として解釈するのかが決まります。

**[イミディエイト]** ウィンドウの場合、等号 (=) は、代入演算子と解釈されます。 したがって、たとえば次のコマンド

```cmd
>Debug.EvaluateStatement(varA=varB)
```

では、変数 `varA` に変数 `varB` の値が代入されます。

**[コマンド]** ウィンドウの場合、等号 (=) は、比較演算子と解釈されます。 **[コマンド]** ウィンドウでは、代入演算は使用できません。 したがって、たとえば変数 `varA` と変数 `varB` の値が異なる場合、次のコマンド

```cmd
>Debug.EvaluateStatement(varA=varB)
```

この場合は値 `False` が返ります。

## <a name="first-chance-exception-notifications"></a>初回例外通知

設定の構成によっては、**[イミディエイト]** ウィンドウに初回例外通知が表示されることがあります。

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>[イミディエイト] ウィンドウで初回例外通知を切り替える

1. **[表示]** メニューの **[その他のウィンドウ]** をポイントし、**[出力]** をクリックします。

2. **[出力]** ウィンドウのテキスト領域で右クリックし、**[例外メッセージ]** をクリックして選択または選択解除します。

## <a name="see-also"></a>関連項目

- [デバッガーでのコード間の移動](../../debugger/navigating-through-code-with-the-debugger.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [デバッガーでのはじめに](../../debugger/debugger-feature-tour.md)
- [チュートリアル: デザイン時のデバッグ](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio での正規表現の使用](../../ide/using-regular-expressions-in-visual-studio.md)
