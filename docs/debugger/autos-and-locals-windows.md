---
title: '[自動変数] と [ローカル] ウィンドウに変数の調査 |マイクロソフトのドキュメント'
ms.custom: H1Hack27Feb2017
ms.date: 04/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35fa37831ad79a55effe849f8605ae6b5d299d3a
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349651"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>[自動変数] と [ローカル] ウィンドウに変数を検査します。

**[自動変数]** と**ローカル**windows は、デバッグ中に変数の値を表示します。 Windows はデバッグ セッション中にのみ使用できます。

**[自動変数]** ウィンドウには、現在のブレークポイントを使用する変数が表示されます。 **ローカル**ウィンドウには、現在の関数またはメソッドは、通常は、ローカル スコープで定義された変数が表示されます。

開くには、 **[自動変数]** ウィンドウで、デバッグ中に、**デバッグ** > **Windows** > **[自動変数]**、またはキーを押します**Ctrl**+**Alt**+**V** > **A**します。

開くには、**ローカル**ウィンドウで、デバッグ中に、**デバッグ** > **Windows** > **ローカル**、またはキーを押します**Alt**+**4**します。

基本的なデバッグの詳細が必要な場合は、次を参照してください。[デバッガーの概要](../debugger/getting-started-with-the-debugger.md)します。

> [!NOTE]
> このトピックでは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac では、次を参照してください。 [Visual studio for Mac のデータの視覚化](/visualstudio/mac/data-visualizations)します。

## <a name="use-the-autos-and-locals-windows"></a>[自動変数] と [ローカル] ウィンドウを使用します。

配列とオブジェクトの表示で、 **[自動変数]** と**ローカル**ツリーのコントロールとして windows。 フィールドとプロパティを表示するビューを展開する変数名の左側にある矢印を選択します。 次の例に示します、<xref:System.IO.FileStream?displayProperty=fullName>オブジェクト、**ローカル**ウィンドウ。

![[ローカル] FileStream](../debugger/media/locals-filestream.png "ローカル FileStream")

赤の値で、**ローカル**または **[自動変数]** ウィンドウは、値が、最後の評価から変更されたことを意味します。 前のデバッグ セッションから、変更可能性がありますまたはウィンドウで値を変更したためです。

デバッガー ウィンドウで既定の数値書式指定は decimal です。 これを 16 進数を変更するのには右クリック、**ローカル**または **[自動変数]** ウィンドウと選択**16 進数の表示**します。 この変更では、すべてのデバッガー ウィンドウに影響します。

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>[自動変数] または [ローカル] ウィンドウで変数の値を編集します。

ほとんどの変数の値を編集する、 **[自動変数]** または**ローカル**windows は、値をダブルクリックし、新しい値を入力します。

たとえば `a + b`のように、値に式を入力することもできます。 デバッガーは、正しい言語式であれば大部分を受け入れます。

ネイティブの C++ コードでは、変数名のコンテキストを修飾しなければならない場合があります。 詳細については、次を参照してください。 [Context operator (C++)](../debugger/context-operator-cpp.md)します。

>[!CAUTION]
>値と式を変更する前に、結果を理解することを確認します。 いくつか考えられる問題は次のとおりです。
>
>-   式を評価すると、変数の値が変わる場合や、プログラムの状態に影響が及ぶ場合があります。 たとえば、評価`var1 = ++var2`両方の値を変更`var1`と`var2`します。 これらの式といいますが[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))します。 副作用で、それらを認識していない場合、予期しない結果が生じる場合があります。
>
>-   浮動小数点値を編集すると、小数部分の 10 進とバイナリの変換により、多少の誤差が発生する場合があります。 一見無害の編集もバイトが、浮動小数点変数のビットの一部に変更します。

## <a name="change-the-context-for-the-autos-or-locals-window"></a>[自動変数] または [ローカル] ウィンドウのコンテキストを変更します。

使用することができます、**デバッグの場所**必要な関数、スレッド、またはのコンテキストを変更するには、プロセスを選択するにはツールバー、 **[自動変数]** と**ローカル**windows。

有効にする、**デバッグの場所**ツールバーで、 をクリックし、ツールバー領域の空の部分で**デバッグの場所**ドロップダウンで、または選択から**ビュー**  >  **ツールバー** > **デバッグの場所**します。

ブレークポイントを設定し、デバッグを開始します。 実行の一時停止しては、内の場所を表示できます、ブレークポイントにヒットしたときに、**デバッグの場所**ツールバー。

![[デバッグの場所] ツールバー](../debugger/media/debuglocationtoolbar.png "デバッグの場所 ツールバー")

## <a name="bkmk_whatvariables"></a> [自動変数] ウィンドウで変数

 **[自動変数]** ウィンドウが使用できるC#、Visual Basic、C++ コードと、しない場合は JavaScript 用またはF#します。

 別のコードの言語での異なる変数を表示する、 **[自動変数]** ウィンドウ。

 - C#と Visual Basic の場合、 **[自動変数]** ウィンドウが現在または前の行に使用される変数が表示されます。 たとえば、C#または Visual Basic のコードは、次の 4 つの変数を宣言します。

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   行にブレークポイントを設定`c = 3;`、し、デバッガーを起動します。 実行が一時停止したときに、 **[自動変数]** ウィンドウに表示されます。

   ![[自動変数] CSharp](../debugger/media/autos-csharp.png "CSharp の [自動変数]")

   値`c`なので、行`c = 3`実行されていません。

 - C++ では、 **[自動変数]** ウィンドウには、実行が一時停止している現在の行の前に少なくとも 3 つの行で使用される変数が表示されます。 たとえば、C++ コードでは、6 つの変数を宣言します。

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    行にブレークポイントを設定`e = 5;`し、デバッガーを実行します。 実行が停止したとき、 **[自動変数]** ウィンドウに表示されます。

    ![[自動変数] C++](../debugger/media/autos-cplus.png "[自動変数] C++")

    変数`e`ために、初期化、されていない行`e = 5`が実行されていません。

##  <a name="bkmk_returnValue"></a> View return values of method calls
 .NET および C++ のコードでの戻り値を確認することができます、 **[自動変数]** ステップ上またはメソッドの呼び出しからステップするときにウィンドウ。 表示メソッドの呼び出しを返す、ローカル変数に保存されていない場合、値が役に立ちます。 メソッドは、パラメーター、または別のメソッドの戻り値として使用できます。

 たとえば、次C#コードは、2 つの関数の戻り値を追加します。

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

戻り値を表示する、`sumVars()`と`subtractVars()`メソッドの呼び出しで、[自動変数] ウィンドウ。

1. `int x = sumVars(a, b) + subtractVars(c, d);` の行にブレークポイントを設定します。

1. デバッグを開始し、実行がブレークポイントで一時停止したときに選択**ステップ オーバー**またはキーを押します**F10**します。 次の戻り値を表示する必要があります、 **[自動変数]** ウィンドウ。

  ![[自動変数] は値を返すC# ](../debugger/media/autosreturnvaluecsharp2.png "戻り値を [自動変数]C#")

## <a name="see-also"></a>関連項目

- [デバッガー ウィンドウ](../debugger/debugger-windows.md)
- [Visual studio for Mac のデータの視覚化](/visualstudio/mac/data-visualizations)
