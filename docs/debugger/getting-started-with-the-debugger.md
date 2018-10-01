---
title: Visual Studio デバッガーを使用してデバッグするについて説明します
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f12e1e95daed3a4e9c6228808123f87174f2202a
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612689"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>チュートリアル: Visual Studio を使用してデバッグする方法を学習します。

この記事では、ステップ バイ ステップ チュートリアルでは、Visual Studio デバッガーの機能について説明します。 デバッガー機能の上位レベルのビューにする場合は、「[デバッガー機能ツアー](../debugger/debugger-feature-tour.md)します。 ときにする*アプリのデバッグ*、アタッチされたデバッガーでアプリケーションを実行していることを通常意味します。 デバッガーにはさまざまな方法でコードが何を参照してください。 これを行うときに実行中にします。 ウォッチを設定するコードをステップ実行し、変数に格納されている値を確認することができます、値を変更する場合に、変数に、コードの実行パスを調べて、コードの分岐が実行されているのかどうかを確認します。 コードをデバッグしようとした初めての場合は、読み取りをする可能性があります[超初心者向けのデバッグ](../debugger/debugging-absolute-beginners.md)にこの記事に進む前にします。

|         |         |
|---------|---------|
|  ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る")  |    [ビデオを見る](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171)のデバッグに関する同様の手順を示すです。 |

デモ アプリは、c# および C++ にはの機能は、Visual Basic、JavaScript、および (場合を除き)、Visual Studio でサポートされている他の言語に適用されます。 スクリーン ショットは、c# では。 C# と C++ のサンプル コードでは、この記事を切り替えるには、このページの右上にある言語のフィルターを使用します。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * デバッガーを起動し、ブレークポイントにヒットします。
> * デバッガーでコードをステップ実行コマンドを習得します。
> * データのヒント、およびデバッガー ウィンドウで変数を検査します。
> * コール スタックを調べる

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio 2017 をインストールする必要があります、 **.NET デスクトップ開発**または**C++ によるデスクトップ開発**ワークロード。

    Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

    ワークロードをインストールする必要があるが、既に Visual Studio を所有している場合は、(**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択し) **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 選択します。**NET のデスクトップ開発**または**C++ によるデスクトップ開発**ワークロードを選択し、**変更**します。

## <a name="create-a-project"></a>プロジェクトを作成する

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

2. **Visual c#** または**Visual C**、選択**Windows デスクトップ**、中央のペインの **コンソール アプリ**(**Windows コンソール アプリケーション**C++ で)。

    表示されない場合、**コンソール アプリケーション**プロジェクト テンプレートをクリックして、 **Visual Studio インストーラーを開く**の左側のウィンドウで、リンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 選択、 *.NET デスクトップ開発** または**C++ によるデスクトップ開発**ワークロードを選択し、**変更**します。

3. ような名前を入力**get の開始-デバッグ** をクリック**OK**します。

    Visual Studio によってプロジェクトが作成されます。

4. *Program.cs* (c#) または*get 開始 debugging.cpp* (C++)、次のコードに置き換えます

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    ```c++
    int main()
    {
        return 0;
    }
    ```

    を、次のコードで置換します。

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }
   
        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }

    }

    /* Output:
        Drawing a rectangle
        Performing base class drawing tasks
        Drawing a triangle
        Performing base class drawing tasks
        Drawing a circle
        Performing base class drawing tasks
    */
    ```

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>デバッガーを起動します。

1. キーを押して**F5** (**デバッグ > [デバッグ開始]**) または**デバッグの開始**ボタン![デバッグの開始](../debugger/media/dbg-tour-start-debugging.png "デバッグの開始")デバッグ ツールバー。

     **F5 キーを押して**、処理は現時点ではコードをチェックする特別な処理を完了していないのデバッガーでアプリをアプリにアタッチされている開始します。 アプリを読み込むようにし、コンソール出力を参照してください。

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     このチュートリアルで、デバッガーを使用してこのアプリを詳しく見てがされさらに機能が、デバッガーを参照してください。

2. 赤色の停止を押して、デバッガーを停止![デバッグの停止](../debugger/media/dbg-tour-stop-debugging.png "デバッグの停止")ボタンをクリックします。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>ブレークポイントを設定し、デバッガーを起動します

1. `foreach`のループ、`Main`関数 (`for` C++ でのループ`main`関数)、次のコード行の左余白をクリックしてブレークポイントを設定します。

    `shape.Draw()` (または、 `shape->Draw()` C++ で)

    ブレークポイントを設定した赤い円が表示されます。

    ブレークポイントは、信頼できるデバッグの最も基本的で重要な機能です。 ブレークポイントは、Visual Studio が実行コードを中断する場所を示します。これにより、変数の値またはメモリの動作を確認したり、コードの分岐が実行されるかどうかを確認したりすることができます。 

6. キーを押して**F5**または**デバッグの開始**ボタンをクリックして、アプリが起動し、ブレークポイントを設定したコードの行に、デバッガーが実行されます。

    ![設定し、ブレークポイントにヒット](../debugger/media/get-started-set-breakpoint.gif)

    黄色の矢印は、デバッガーが一時停止されても (このステートメントがまだ実行) 同じ時点でアプリの実行を中断するステートメントを表します。

     アプリがまだ実行されていない場合**F5**デバッガーを起動し、最初のブレークポイントで停止します。 それ以外の場合、 **F5**次のブレークポイントまでアプリの実行が続行されます。

    ブレークポイントは、コードの行または詳細に確認するコードのセクションがわかっている場合に便利な機能です。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>ステップ コマンドを使用して、デバッガーでコードを移動します。

ほとんどの場合、使用してキーボード ショートカットここでは、取得する優れた方法であるデバッガー (同等のコマンド メニューなどのコマンドは、かっこ内に表示されます) で、アプリの実行時に、高速です。

1. 一時停止中に、`shape.Draw`でメソッドを呼び出す、`Main`メソッド (`shape->Draw` C++ で)、キーを押して**F11** (選択または**デバッグ > ステップ イン**) のコードに進めておく、 `Rectangle`クラス。

     ![F11 キーを使用して、コードにステップ インを](../debugger/media/get-started-f11.png "ステップ イン F11")

     F11 キーは、**ステップ イン**コマンドを実行し、時にアプリの実行の 1 つのステートメントを進めます。 F11 キーは、ほとんどの詳細情報で実行フローを確認する良い方法です。 (コードをより迅速に紹介するその他のオプションも。)既定で、デバッガーが非ユーザー コードをスキップ (詳細についてを実行する場合に、「[マイ コードのみ](../debugger/just-my-code.md)).

2. キーを押します**F10** (選択または**デバッグ > ステップ オーバー**) を数回にデバッガーを停止するまで、`base.Draw`メソッドの呼び出し (`Shape::Draw` C++ で)、し、キーを押します**F10**もう一度。

     ![F10 キーを使用して、ステップ オーバー コードを](../debugger/media/get-started-step-over.png "f10 キーを押してステップ オーバー")

     注意この時間、デバッガーがステップ インしない、`Draw`基本クラスのメソッド (`Shape`)。 **F10 キーを押して**(まだコードが実行される)、アプリのコードの関数やメソッドにステップ インすることがなく、デバッガーを進めます。 F10 キーを押して、 `base.Draw` (または`Shape::Draw`) メソッドの呼び出し (の代わりに**F11**) の実装コードは省略しました`base.Draw`(おそらくはいない、対象となるで現在どの)。

## <a name="navigate-code-using-run-to-click"></a>クリックで実行を使用してコードを移動します。

5. コード エディターで下にスクロールし、マウス、`Console.WriteLine`メソッド (`std::cout` C++ で) で、`Triangle`緑までクラス**クリックで実行**ボタン![クリックで実行](../debugger/media/dbg-tour-run-to-click.png "RunToClick")左側に表示します。

     ![クリックで実行を使用して機能](../debugger/media/get-started-run-to-click.png "クリックで実行")

    >  [!NOTE]
    > **クリックで実行**ボタンは新[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]します。 緑色の矢印ボタンが表示されない場合は、使用**F11**この例では代わりに、デバッガーを適切な場所に進みます。

6. をクリックして、**クリックで実行**ボタン![クリックで実行](../debugger/media/dbg-tour-run-to-click.png "RunToClick")します。

    このボタンを使用することは、一時的なブレークポイントを設定に似ています。 **クリックで実行**はアプリのコード (開いているファイルでクリックすることができます) の可視領域内で簡単に回避するために便利です。

    デバッガーに進めます、`Console.WriteLine`メソッドの実装、`Triangle`クラス (`std::cout` C++ で)。

    を一時停止中に、誤りがある場合に注意してください。 「、Trangle を描画する」出力のスペルが間違っています。 ここで、デバッガーで、アプリの実行中に解決できます。

## <a name="edit-code-and-continue-debugging"></a>コードを編集してデバッグを続行する

1. クリックして「を trangle の描画」と"trangle"を"triangle"に変更する、修正を入力します。

1. キーを押して**F11**して、デバッガーが再び進めるを参照してください。

    > [!NOTE]
    > によって、デバッガーで編集するためのコードの種類、警告メッセージが表示する可能性があります。 一部のシナリオで、コードは、続行する前に再コンパイルする必要があります。

## <a name="step-out"></a>ステップ アウト

終了することと検査、`Draw`メソッド、`Triangle`クラスしたい場合、関数から取得され、デバッガー。 これを行うを使用して、**ステップ アウト**コマンド。

1. キーを押して**Shift** + **F11** (または**デバッグ > ステップ アウト**)。

     このコマンドがアプリの実行を再開 (および、デバッガーを進めます) まで、現在の関数を返します。

     戻る必要があります、`foreach`ループ、`Main`メソッド (`for` C++ でのループ)。

## <a name="restart-your-app-quickly"></a>アプリを迅速に再起動します。

をクリックして、**再起動**![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp")デバッグ ツールバーのボタン (**Ctrl** + **Shift**  +  **F5**)。

押したとき**再起動**アプリを停止して、デバッガーを再起動すると時間が節約されます。 コードを実行してヒットした最初のブレークポイントでデバッガーが一時停止します。

設定するでのブレークポイントでデバッガーが再び停止する、`shape.Draw()`メソッド (`shape->Draw()` C++ で)。

## <a name="inspect-variables-with-data-tips"></a>データ ヒントで変数を検査します。

変数を検査できるようにする機能は、デバッガーの最も便利な機能の 1 つと、これを行う方法はあります。 多くの場合、問題をデバッグするときに、変数が期待どおりにして、特定の時刻値を格納するかどうかを確認しようとしています。

1. 一時停止中に、`shape.Draw()`メソッド (`shape->Draw()` C++ で)、マウス、`shapes`オブジェクトとその既定のプロパティ値を参照してください。、`Count`プロパティ。

1. 展開、`shapes`オブジェクト、配列の最初のインデックスなど、すべてのプロパティを表示する`[0]`の値を持つ`Rectangle`(c#) またはメモリ アドレス (C++)。

     ![データ ヒントを表示する](../debugger/media/get-started-data-tip.gif "データ ヒントを表示します。")

    などのプロパティを表示するオブジェクトをさらに展開することができます、`Height`四角形のプロパティ。

    多くの場合、オブジェクト、プロパティ値を確認する簡単な方法が必要なデバッグ時にし、データ ヒントには、これを行う良い方法です。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>[自動変数] と [ローカル] ウィンドウで変数を検査します。

1. 見て、 **[自動変数]** コード エディターの下部のウィンドウ。

     ![[自動変数] ウィンドウで変数の検査](../debugger/media/get-started-autos-window.png "[自動変数] ウィンドウ")

    **[自動変数]** ウィンドウで、変数と、現在の値を参照してください。 **[自動変数]** ウィンドウには、現在の行または前の行で使用されるすべての変数が表示されます (C++ で、ウィンドウが表示されます変数に上記の 3 行のコード。 言語固有の動作のマニュアルを確認)。

    > [!NOTE]
    > JavaScript では、**ローカル**ウィンドウはサポートされていませんが、 **[自動変数]** ウィンドウ。

2. 次を見て、**ローカル**ウィンドウの横にタブで、 **[自動変数]** ウィンドウ。

    **ローカル**ウィンドウには、現在のある変数[スコープ](https://www.wikipedia.org/wiki/Scope_(computer_science))します。

## <a name="set-a-watch"></a>ウォッチを設定します。

1. メインのコード エディター ウィンドウで右クリックし、`shapes`オブジェクトし、選択**ウォッチ式の追加**します。

    **ウォッチ**コード エディターの下部にあるウィンドウが表示されます。 使用することができます、**ウォッチ**ウィンドウ上に注意する変数 (または式) を指定します。

    ここで、ウォッチがある、`shapes`オブジェクトとは、その値をデバッガー内を移動するように変更を表示できます。 その他の変数ウィンドウとは異なり、**ウォッチ**ウィンドウは常に表示、変数試聴していること (グレー場合にスコープ外)。

## <a name="examine-the-call-stack"></a>コール スタックを調べる

1. 一時停止中に、`foreach`ループ (`for` C++ でのループ)、をクリックして、**呼び出し履歴**ウィンドウで、既定の右下のウィンドウで開くことです。

1. をクリックして**F11**何回か、デバッガーで一時停止が表示されるまで、`Circle.Draw`コード エディターでのメソッド。 見て、**呼び出し履歴**ウィンドウ。

    ![呼び出し履歴を調べ](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    **呼び出し履歴**ウィンドウ メソッドと関数を呼び出す作業はこれで順序が表示されます。 先頭行は、現在の関数を示しています (、`Circle.Draw`または`Circle::Draw`このアプリでメソッド)。 2 行目はことを示しています`Circle.Draw`から呼び出されていた、`Main`メソッド (`main` C++ で) など。

    >  [!NOTE]
    > **呼び出し履歴**Eclipse などの一部の Ide ウィンドウはデバッグ パースペクティブに似ています。

    呼び出し履歴は、調査およびアプリの実行フローを理解することをお勧めします。

    ソース コードを確認します。 コード行をダブルクリックしても、デバッガーによって検査されている現在のスコープを変更します。 このアクションでは、デバッガーは変化しません。

    右クリック メニューを使用することもできます、**呼び出し履歴**ウィンドウを他の操作を行います。 たとえば、指定した関数にブレークポイントを挿入を使用して、デバッガーを進める**カーソルまで実行**、go ソース コードを調べるとします。 詳細については、次を参照してください。[方法: 呼び出し履歴を調べる](../debugger/how-to-use-the-call-stack-window.md)します。

## <a name="change-the-execution-flow"></a>実行フローを変更します。

1. デバッガーで一時停止、`Circle.Draw`メソッドの呼び出し、キーを押して**F11**を数回までで、デバッガーが一時停止、`base.Draw`メソッドの呼び出し (`Shape::Draw` C++ で)。

1. 左側の黄色の矢印 (実行ポインター) を取得し、移動を 1 つの行に黄色の矢印にマウスを使用して、 `Console.WriteLine` (`std::cout` C++ で) メソッドの呼び出し。

1. キーを押して**F11**もう 1 回です。

    デバッガーを再実行した、`Console.WriteLine`メソッド (`std::cout` C++ で)。

    実行フローを変更するには、別のコードの実行パスをテストまたはデバッガーを再起動しなくてもコードを再実行などの処理を行うことができます。

    > [!WARNING]
    > 多くの場合、この機能により、注意する必要があり、ツールヒントに警告を表示します。 すぎて他の警告を表示可能性があります。 ポインターを移動すると、アプリケーションを以前のアプリの状態を元に戻すことはできません。

1. キーを押して**F5**アプリの実行を続行します。

    これでこのチュートリアルは完了です。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、コードをステップ実行、デバッガーを起動し、変数を確認する方法を学習できました。 詳細情報へのリンクと共にデバッガー機能の概要を取得することがあります。

> [!div class="nextstepaction"]
> [デバッガーのヒントと秘訣](../debugger/debugger-tips-and-tricks.md)
