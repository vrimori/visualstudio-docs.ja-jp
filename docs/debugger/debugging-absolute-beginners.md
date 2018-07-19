---
title: 超初心者向けのコードのデバッグ
description: 初めてデバッグする場合は、Visual Studio でデバッグ モードでアプリを実行するためのいくつかの原則を説明します。
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42a04a64f5ed7f62f4b01f703efa85e36aa854ff
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39131870"
---
# <a name="how-to-debug-for-absolute-beginners"></a>超初心者向けのデバッグ方法

失敗せずソフトウェア開発者として記述するコードは常に実行予想を。 まったく異なるエンティティです。 次のタスクが、理由を把握するにはこのような場合は、私たちをコードで時間だけ見つめを保持したくなる可能性がありますが、はるかに簡単かつ効率的にデバッグ ツールを使用するか、デバッガーは.

残念ながら、デバッガーでは、コードですべての問題または「バグ」を表示できます魔法のようなものはありません。 *デバッグ*などのプログラミングの間違いが行われる場所の正確なポイントを検索する、Visual Studio のコード、デバッグ ツールでは、ステップ バイ ステップを実行することを意味します。 コードにする必要があるどのような修正を理解して、デバッグのツールを多くの場合、使用すると、プログラムの実行を継続できるように、一時的な変更を加えます。

デバッガーを効果的に使用するは、時間と方法については、スキルもが、基本的なタスクをソフトウェア開発者すべてが最終的にします。 この記事でデバッグの中核となる原則を紹介し、開始するためのヒントを提供します。

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>適切な質問を自問して問題を明確化します。

その修正を試みる前に直面する問題を明確に役立ちます。 予定を既に実行されたことに問題が発生、コードで、それ以外の場合はありませんがここでしようとしてそれをデバッグする方法します。 そのため、デバッグを開始する前に確認解決しようとしている問題を特定しました。

* 何を期待していたためにはコードですか。

* 代わりに何が発生しましたか。

    アプリの実行中にエラー (例外) を実行すると、良いことをことができます。 ある種のエラーでは通常、コードを実行するときに発生した予期しないイベントは例外です。 デバッグ ツールでは、例外が発生した、コード内の正確な場所にかかるし、考えられる修正方法を調査することができます。

    他の何か問題が発生した場合の問題の症状が何ですか。 行う可能性があるコードでこの問題が発生しましたか。 たとえば、コードがいくつかのテキストが表示されますが、テキストが正しくない場合は、いずれか、データが正しくないか、表示文字列を設定するコードにはある種のバグをわかります。 デバッガーでコードをステップ実行、変数を設定して、不適切な値が割り当てられている方法とタイミングを正確に検出するすべての変更を確認できます。

## <a name="examine-your-assumptions"></a>前提条件を確認します。

バグまたはエラーを調査する前に、解釈が特定の結果を期待すると考えてください。 非表示または不明な前提は、デバッガーで適切な問題の原因を探している場合でも、問題を識別する邪魔ことができます。 可能な前提条件の長いリストを使用するがあります。 ここでは、いくつかの質問を自問するみると、想定を見直します。

* (これは、適切なオブジェクト、関数、メソッド、またはプロパティ) は、適切な API を使用しているでしょうか。 使用している API は考えるを実行します。 (デバッガーでの API 呼び出しを調べると、後に問題を修正する必要があります、適切な API を識別できるようにドキュメントへのトリップ。)

* API を正しく使用していますか。 おそらく API を適切に使用が、適切な方法で使用していません。

* コードには、タイプミスが含まれているでしょうか。 単純な変数名のスペルミスなどのいくつかの入力ミスについては、変数を使用する前に宣言を必要としない言語を使用する場合に特に困難になります。

* でした、コードに変更を加えるし、すれば問題に関連でない前提としていますか。

* 期待していたオブジェクトや、特定の値 (または特定の種類の値) を格納する変数は実際に変更点が異なりますか?

* コードの意図をご存知ですか。 詳細は、コードの他のユーザーがデバッグは困難です。 場合は、コードではありませんは、ことを正確にどのようなコードは、効果的にデバッグする前に時間の学習を費やす必要があります。

    > [!TIP]
    > コードを記述する場合は、小規模で開始し、動作するコードで開始! (適切なサンプル コードは便利なここ) です。場合によっては、実現しようとして、コア タスクを示すコードの小さなまとまりを始めることで、大規模または複雑な一連のコードを修正するのには簡単です。 次に、変更したり、コードを段階的に、追加のエラーは、各ポイントでのテストできます。

前提条件を疑問視されることは、によって、コードで問題を見つけるためにかかる時間を減らすことができます。 また、問題を解決にかかる時間を減らすことができます。

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>問題の発生場所を確認するモードのデバッグにコードをステップ実行

通常アプリを実行すると、コードを実行した後にのみエラーと不適切な結果を表示します。 プログラムは、理由を示すことがなくが予期せず終了も可能性があります。

デバッガー内でアプリを実行するいるとも呼ばれます*デバッグ モード*、デバッガー積極的に監視できるすべてのプログラムの実行時に行われていることを意味します。 また、任意の時点の状態を確認して、すべての詳細を見ることが行われるために 1 行ずつコードをステップでアプリを一時停止することもできます。

Visual Studio を使用してデバッグ モードを入力する**F5** (または**デバッグ** > **デバッグの開始**メニュー コマンド、または**デバッグの開始**ボタン![デバッグの開始](../debugger/media/dbg-tour-start-debugging.png "デバッグの開始"))、[デバッグ] ツールバーでします。 例外が発生した場合、正確なポイントと、例外が発生した、他の有用な情報を提供するは Visual Studio の例外ヘルパーします。

例外が届かなかった可能性がある場合をお勧め、コード内の問題を検索する場所。 これを使用する*ブレークポイント*自分でコードをより慎重に確認する機会を提供するデバッガーの使用。 ブレークポイントは、信頼できるデバッグの最も基本的で重要な機能です。 ブレークポイントを参照してください、変数の値またはメモリの動作またはコードを実行するシーケンスを行うために、Visual Studio で実行中のコードに停止する必要がありますを示します。

Visual Studio でのコード行の横にある左の余白をクリックして、ブレークポイントをすばやく設定できます。 カーソルを置き、線とキーを押してまたは**F9**します。

これらの概念を示すために、私たちを見て既にいくつかのバグのあるコード例。 C# を使用しているが、デバッグの機能は、Basic、C++、JavaScript、Python、およびその他のサポートされている言語は、ビジュアルに適用されます。 します。

### <a name="create-a-sample-app-with-some-bugs"></a>(いくつかのバグ) でサンプル アプリを作成します。

次に、いくつかのバグのあるアプリケーションを作成します。

1. Visual Studio をインストールし、いずれかが必要、します。**NET のデスクトップ開発**ワークロードまたは **。クロス プラットフォーム開発の NET Core**ワークロードがインストールされているアプリの種類に応じて作成します。

    Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

    かどうか、ワークロードをインストールする をクリックして、Visual Studio が既にある必要があります**ツール** > **ツールの入手と機能**します。 Visual Studio インストーラーが起動します。 選択します。**NET のデスクトップ開発**(または **。クロス プラットフォーム開発の NET Core**) ワークロードを選択し、**変更**します。

1. Visual Studio を開き、選択**ファイル** > **新規** > **プロジェクト**します。

1. アプリケーション コードのテンプレートを選択します。

    .NET Framework 用で、**新しいプロジェクト** ダイアログ ボックスで、選択**Visual c#**、 **Windows デスクトップ**インストールされているテンプレート セクションから、中央のペインの選択で**コンソール アプリ (.NET Framework)** します。

    .NET core での**新しいプロジェクト** ダイアログ ボックスで、選択**Visual c#**、 **.NET Core**し、インストールされているテンプレート セクションから、中央のペインで選択**コンソール アプリ (.NET Core)** します。

    これらのテンプレートが表示されない場合は、適切なワークロードをインストールする必要があります (前の手順を参照してください)。

1. **名前**フィールドに「 **ConsoleApp FirstApp**  をクリック**OK**します。

    Visual Studio では、右側のウィンドウで、ソリューション エクスプ ローラーで表示されるコンソール プロジェクトを作成します。

1. *Program.cs*、すべての既定のコードを次のコードに置き換えます。

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    このコードの意図では、すべての一覧で、galaxy と galaxy 種類までの距離、galaxy 名前を表示します。 デバッグするには、コードの意図を理解する必要があります。 出力に表示する必要がある一覧から 1 行の形式を次に示します。

    *galaxy 名前*、*距離*、 *galaxy 型*します。

### <a name="run-the-app"></a>アプリを実行する

1. キーを押して**F5**または**デバッグの開始**ボタン![デバッグの開始](../debugger/media/dbg-tour-start-debugging.png "デバッグの開始")コード エディターの上にある [デバッグ] ツールバー。

    アプリが起動することで、デバッガーで表示される例外はありません。 ただし、コンソール ウィンドウに表示出力は、予想したものです。 予想される出力を次に示します。

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    しかし、これを代わりに参照します。

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    出力には、コードを見ると、当社は知って`GType`galaxy 種類を格納するクラスの名前を指定します。 実際の galaxy タイプ「スパイラル」)、(を表示しようとしましたが、クラス名ではありません!

### <a name="debug-the-app"></a>アプリをデバッグします

1. まだ実行されているアプリで、左余白の横をクリックしてブレークポイントを設定、`Console.WriteLine`メソッドの呼び出しのコード行にします。

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    ブレークポイントを設定すると、左の余白に赤い点が表示されます。

    出力に問題がわかりますので、デバッガーで、出力を設定する前のコードを調べることでデバッグをまず始めます。

1. をクリックして、**再起動**![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp")デバッグ ツールバーのボタン (**Ctrl** + **Shift**  +  **F5**)。

    アプリは、設定したブレークポイントで一時停止します。 黄色の専門は、デバッガーが一時停止していることを示します (コードの黄色い線がまだ実行)。

1. ポインターを合わせる、 `GalaxyType` 、右側にし、レンチのアイコンの左側に変数を展開`theGalaxy.GalaxyType`します。 参照してください`GalaxyType`プロパティを含む`MyGType`、およびプロパティの値に設定されます`Spiral`します。

    ![変数を検査します。](../debugger/media/beginners-inspect-variable.png)

    「スパイラル」は、コンソールに出力を想定していた実際に正しい値です。 これは、適切な出発点として、アプリの実行中にこのコードでは、この値にアクセスできることです。 このシナリオでは、無効な API を使用します。 かどうかの解決に役立てるこのデバッガーでコードの実行中に表示されます。

1. 同じコードでまだデバッグ中にカーソルを置くの最後に`theGalaxy.GalaxyType`に変更および`theGalaxy.GalaxyType.MyGType`します。 この変更を行うことができますが、コード エディターでは、このコードをコンパイルすることはできませんを示すエラー。

    ![構文エラー](../debugger/media/beginners-edit.png)

1. クリックして**編集**で、**エディット コンティニュ**メッセージ ボックス。 ようになりましたエラー メッセージを参照してください、**エラー一覧**ウィンドウ。 エラーが示す、`'object'`の定義が含まれていない`MyGType`します。

    ![構文エラー](../debugger/media/beginners-no-definition.png)

    型のオブジェクトと各 galaxy を設定しても`GType`(を持つ、`MGType`プロパティ)、デバッガーが認識しない、`theGalaxy`オブジェクト型のオブジェクトとして`GType`します。 どうなっているのですか。 Galaxy 型を設定しているコード全体を確認するには。 これを行うことがわかります、`GType`クラスのプロパティには間違いなく`MyGType`が適切なものはありません。 に関するエラー メッセージ`object`への手掛かり; 言語のインタープリターに型は型のオブジェクトに表示されます。`object`型のオブジェクトではなく`GType`します。

1. 検索の galaxy 型の設定に関連するコードを調べて、`GalaxyType`のプロパティ、`Galaxy`クラスとして指定`object`の代わりに`GType`します。

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. これには、上記のコードを変更します。

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. をクリックして、**再起動**![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp")デバッグ ツールバーのボタン (**Ctrl** + **Shift**  +  **F5**) コードを再コンパイルし、再起動します。

    デバッガーが一時停止すると、 `Console.WriteLine`、ポイントすると`theGalaxy.GalaxyType.MyGType`、正しく設定されていることを確認します。

1. 左マージンにブレークポイント円をクリックして、ブレークポイントの削除 (または右クリックし、選択**ブレークポイント** > **ブレークポイントの削除**)、およびキーを押します**F5**を続行します。

    アプリでは、実行し、出力を表示します。 これは、問題はなさが; の 1 つが発生しました。コンソール出力では、不規則な galaxy として表示する小さな Magellanic クラウド galaxy 予期していたが示していますありません galaxy 型にします。

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. 次のコードでブレークポイントを設定します。

    ```csharp
    public GType(char type)
    ```

    このコードは、詳しく見てたい galaxy 型が設定されています。

1. をクリックして、**再起動**![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp")デバッグ ツールバーのボタン (**Ctrl** + **Shift**  +  **F5**) を再起動します。

    デバッガーは、ブレークポイントを設定するコード行で一時停止します。  

1. ポインターを合わせる、`type`変数。 値を参照してください`S`(次の文字コード)。 値に関心がある`I`不規則な galaxy 型であることがわかっているため、します。

1. キーを押して**F5**ポインターを合わせると、`type`変数をもう一度です。 値が表示されるまで、この手順を繰り返します`I`で、`type`変数。

    ![変数を検査します。](../debugger/media/beginners-inspecting-data.png)

1. ここで、キーを押して**F11** (**デバッグ** > **ステップ イン**または**ステップ イン**デバッグ ツールバーのボタン)。

    **F11**一度に 1 つのステートメントをデバッガーを進めます (およびコードを実行します)。 **F10 キーを押して**(**ステップ オーバー**) 類似のコマンドは、デバッガーを使用する方法を学習するときに両方が非常に便利です。

1. キーを押して**F11**内のコード行で停止するまで、 `switch` 'I' の値のステートメント。 ここでは、入力ミスによるクリアの問題を参照してください。 設定に進むにコードが期待どおり`MyGType`irregular、デバッガーは galaxy の型を代わりにこのコードを完全にスキップし、で一時停止します、`default`のセクション、`switch`ステートメント。

    ![入力ミスを検索します。](../debugger/media/beginners-typo.png)

    ミスを表示するコードを見て、`case 'l'`ステートメント。 必要がある`case 'I'`します。

1. コードでクリックして`case 'l'`、置き換える ' case 'I'。

1. 設定したブレークポイントを削除し、**再起動**アプリの再起動ボタンをクリックします。

    これで、バグが修正し、予期される出力を参照してください!

    アプリを終了する任意のキーを押します。

## <a name="summary"></a>まとめ

問題が表示されたら、デバッガーを使用および[ステップ コマンド](../debugger/navigating-through-code-with-the-debugger.md)など**F10**と**F11**問題のあるコードの領域を検索します。

> [!NOTE]
> 問題が発生する前に実行されるコードにブレークポイントを設定し、問題が表示されるまで、手順のコマンドを使用して、問題が発生するコードの領域を特定する困難な場合は、マニフェスト。 使用することも[トレース ポイント](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)にメッセージをログに記録する、**出力**ウィンドウ。 によってログに記録されたメッセージを表示 (およびメッセージがまだログインしていないことに注意!)、多くの場合、問題のあるコードの領域を分離することができます。 このプロセスを複数回繰り返して、絞り込むためにする必要があります。

問題のあるコードの領域が見つかったら、デバッガーを使用して調査します。 問題の原因を見つけるには、デバッガーで、アプリの実行中に問題のコードを検査します。

* [変数の検査](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)をする必要がありますが含まれている値の型が含まれているかどうかを確認します。 無効な値を検索する場合は、不適切な値が設定されたを調べる (値の設定を検索するには、デバッガーを再起動いずれかを確認する必要がある可能性があります、[コール スタック](../debugger/how-to-use-the-call-stack-window.md)、またはその両方)。

* アプリケーションが必要なコードを実行するかどうかを確認します。 (たとえば、サンプル アプリケーションで不規則な場合に galaxy 型を設定する switch ステートメントのコードが必要ですが、アプリは、入力ミスにより、コードをスキップ)。

> [!TIP]
> デバッガーを使用して、バグを見つけるのに役立ちます。 デバッグ ツールがバグを発見*を*し、コードの意図を認識している場合にのみです。 その意図を表現する、開発者は場合、ツールは、コードの意図を把握のみできます。 書き込み[単体テスト](../test/improve-code-quality.md)はその方法。

## <a name="next-steps"></a>次の手順

この記事では、いくつかの一般的なデバッグの概念を学びました。 次に、Visual Studio でデバッグする方法を学習を開始することができます。

> [!div class="nextstepaction"]
> [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)
