---
title: 'チュートリアル: シンプルな C# コンソール アプリを作成する'
description: Visual Studio で C# コンソール アプリを作成する方法について、ステップ バイ ステップで説明します。
ms.custom: seodec18, get-started
ms.date: 01/25/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-dev15
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 856c20175fd444c7acf83bdf02526c907a28b92f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936958"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>チュートリアル: Visual Studio でシンプルな C# コンソール アプリを作成する

この C# 用のチュートリアルでは、Visual Studio を使用して、コンソール アプリを作成および実行しながら、Visual Studio の統合開発環境 (IDE) の一部の機能を検討します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

始めるには、C# アプリケーション プロジェクトを作成します。 このプロジェクトの種類には、必要となるすべてのテンプレート ファイルが付属していますので、何も追加する必要はありません。

1. Visual Studio 2017 を開きます。

2. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

3. 左側のウィンドウの **[新しいプロジェクト]** ダイアログ ボックスで、**[C#]** を展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[Console App (.NET Core)]** を選択します。 次に、ファイルに *Calculator* という名前を付けます。

   ![Visual Studio IDE の [新しいプロジェクト] ダイアログ ボックスに示されているコンソール アプリ (.NET Core) プロジェクト テンプレート](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>ワークグループを追加する (省略可能)

**コンソール アプリ (.NET Core)** プロジェクト テンプレートが表示されない場合は、**.NET Core クロスプラットフォームの開発**ワークロードを追加して取得できます。 ここではその方法を説明します。

#### <a name="option-1-use-the-new-project-dialog-box"></a>オプション 1:[新しいプロジェクト] ダイアログ ボックスを使用する

1. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで、**[Visual Studio インストーラーを開く]** リンクを選択します。

   ![[新しいプロジェクト] ダイアログ ボックスから [Visual Studio インストーラーを開く] リンクを選択する](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio インストーラーが起動します。 **[.NET Core クロスプラットフォームの開発]** ワークロードを選択し、**[変更]** を選択します。

   ![Visual Studio インストーラーの [.NET Core クロスプラットフォームの開発] ワークロード](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>オプション 2:[ツール] メニュー バーを使用する

1. **[新しいプロジェクト]** ダイアログ ボックスを取り消し、上部のメニュー バーから **[ツール]** > **[ツールと機能を取得]** の順に選択します。

1. Visual Studio インストーラーが起動します。 **[.NET Core クロスプラットフォームの開発]** ワークロードを選択し、**[変更]** を選択します。

## <a name="create-the-app"></a>アプリを作成する

まず、C# での基本的な整数計算を見ていきます。 次に、基本的な電卓を作成するコードを追加します。 次に、機能を追加するコードを調整します。 その後を、アプリをデバッグし、エラーを発見して修正します。 最後に、コードを改良していっそう効率的にします。

C# での整数計算を始めましょう。

1. コード エディターで、既定の "Hello World" のコードを削除します。

    ![新しい電卓アプリから既定の Hello World コードを削除する](./media/csharp-console-calculator-deletehelloworld.png)

   具体的には、`Console.WriteLine("Hello World!");` と記述された行を削除します。

1. その場所に、次のコードを入力します。

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```
1. **[Calculator]** を選択してプログラムを実行するか、**F5** キーを押します。

   ![[Calculator] ボタンを選択して、ツールバーからアプリを実行する](./media/csharp-console-calculator-button.png)

   コンソール ウィンドウが開き、42 + 119 の合計が表示されます。

1. 今度は別の演算子 (減算の場合は `-`、乗算の場合は `*`、除算の場合は */*) を使用して、コードの `int c = a + b;` 行を変更します。

    演算子を変更してプログラムを実行すると、結果も変わることに注目してください。

次に、より複雑な一連の電卓コードをプロジェクトに追加してみましょう。

1. コード エディターに表示されているすべてのコードを削除します。

1. コード エディターに次の新しいコードを入力するか貼り付けます。

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```
1. **[Calculator]** を選択してプログラムを実行するか、**F5** キーを押します。

   ![[Calculator] ボタンを選択して、ツールバーからアプリを実行する](./media/csharp-console-calculator-button.png)

   コンソール ウィンドウが開きます。

1. コンソール ウィンドウでアプリを表示し、指示に従って値 **42** と **119** を追加します。

   アプリは次のスクリーンショットのようになります。

    ![アクションを実行するプロンプトを含む、Calculator アプリが表示されているコンソール ウィンドウ](./media/csharp-console-calculator.png)

### <a name="add-decimals"></a>小数を追加する

現在、電卓アプリでは整数を受け取って返します。 ただし、小数に対応するコードを追加するともっと正確になります。

次のスクリーンショットのように、アプリを実行して、値 42 を値 119 で割ると、結果は 0 (ゼロ) になり正確ではありません。

![結果として小数を返さない電卓アプリが表示されているコンソール ウィンドウ](./media/csharp-console-calculator-nodecimal.png)

小数を処理するようにコードを修正しましょう。

1. **Ctrl** + **F** キーを押して **[検索と置換]** コントロールを開きます。

1. `int` 変数の各インスタンスを `float` に変更します。

    ![int 変数を float に変更する方法を示す [検索と置換] コントロールのアニメーション](./media/find-replace-control-animation.gif)

1. 電卓アプリをもう一度実行し、値 **42** を値 **119** で割ります。

   アプリがゼロではなく小数を返すようになったことに注意してください。

    ![結果として小数を返すようになった電卓アプリが表示されているコンソール ウィンドウ](./media/csharp-console-calculator-decimal.png)

ただし、アプリは小数の結果を生成するだけです。 もう少しコードに手を加えて、小数を計算できるようにしましょう。

1. **[検索と置換]** コントロール (**Ctrl** + **F** キー) を使用して `float` 変数の各インスタンスを `double` に変更し、`Convert.ToInt32` メソッドの各インスタンスを `Convert.ToDouble` に変更します。

1. 電卓アプリを実行し、値 **42.5** を値 **119.75** で割ります。

   アプリが小数値を受け付け、結果として長い小数値を返すようになったことに注意してください。

    ![小数値を受け取り結果として長い小数値を返すようになった電卓アプリが表示されているコンソール ウィンドウ](./media/csharp-console-calculator-usedecimals.png)

    (小数点以下の桁数は、「[コードを修正する](#revise-the-code)」セクションで修正します。)

## <a name="debug-the-app"></a>アプリをデバッグする

基本的な電卓アプリを改善しましたが、ユーザー入力エラーなどの例外を処理するための安全装置がまだありません。

たとえば、0 で数値を割ったり、数値が必要なときにアルファベット文字を入力したりすると (またはその逆)、アプリは動作を停止し、エラーが返されます。

いくつかの一般的なユーザー入力エラーを行い、デバッガーでそれを検索して、コードを修正を行ってみましょう。

>[!TIP]
>デバッガーとそのしくみの詳細については、「[最初に Visual Studio デバッガーを見る](../../debugger/debugger-feature-tour.md)」を参照してください。

### <a name="fix-the-divide-by-zero-error"></a>"0 除算" エラーを修正する

数値を 0 で割ろうとすると、コンソール アプリはフリーズします。 コード エディターに問題が表示されます。

   ![0 除算エラーが表示されている Visual Studio のコード エディター](./media/csharp-console-calculator-dividebyzero-error.png)

このエラーを処理するようにコードを変更してみましょう。

1. `case "d":` とコメント `// Wait for the user to respond before closing` の間に表示されているコードを削除します。

1. 見つかったコードを次のコードと置き換えます。

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   コードを追加した後、`switch` ステートメントを含むセクションは次のスクリーンショットのようになります。

   ![Visual Studio コード エディターで変更された "switch" セクション](./media/csharp-console-calculator-switch-code.png)

今度は、数値を 0 で割ると、別の値の入力を求められます。 さらに良い点:ゼロ以外の数値を入力するまで、入力要求は停止しません。

   ![0 除算エラーが表示されている Visual Studio のコード エディター](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>"書式" エラーを修正する

アプリで数字が予期されているときにアルファベット文字を入力すると (またはその逆)、コンソール アプリはフリーズします。 コード エディターに問題が表示されます。

   ![書式エラーが表示されている Visual Studio コード エディター](./media/csharp-console-calculator-format-error.png)

このエラーを解決するには、前に入力したコードをリファクタリングする必要があります。

#### <a name="revise-the-code"></a>コードを修正する

`program` クラスに依存してすべてのコードを処理するのではなく、アプリを 2 つのクラス `calculator` と `program` に分割します。

`calculator` クラスでは計算作業をまとめて処理し、`program` クラスではユーザー インターフェイスとエラー キャプチャの作業を処理します。

では、始めましょう。

1. 次のコード ブロックの "*後*" にあるものをすべて削除します。

    ```csharp

    using System;

    namespace Calculator
    {

    ```

1. そして、次のように、新しい `calculator` クラスを追加します。

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error

            // Use a switch statement to do the math
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. さらに、次のように、新しい `program` クラスを追加します。

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing
            }
            return;
        }
    }
    ```
1. **[Calculator]** を選択してプログラムを実行するか、**F5** キーを押します。

1. 画面の指示に従って、値 **42** を値 **119** で割ります。 アプリは次のようになります。

    ![実行するアクションのプロンプトと正しくない入力のエラー処理を含むようにリファクタリングされた電卓アプリが示されているコンソール ウィンドウ](./media/csharp-console-calculator-refactored.png)

    コンソール アプリの終了を選択するまで、さらに式を入力するためのオプションがあることに注意してください。 また、結果の小数点以下の桁数も減らしています。

## <a name="close-the-app"></a>アプリを閉じる

1. まだ行っていない場合は、電卓アプリを閉じます。

1. Visual Studio の **[出力]** ウィンドウを閉じます。

   ![Visual Studio の [出力] ウィンドウを閉じる](./media/csharp-calculator-close-output-pane.png)

1. Visual Studio で **Ctrl** + **S** キーを押してアプリを保存します。

1. Visual Studio を閉じます。

## <a name="code-complete"></a>完成したコード

このチュートリアルでは、電卓アプリに多くの変更を行いました。 アプリでは、コンピューティング リソースがより効率的に処理され、ほとんどのユーザーの入力エラーが処理されるようになっています。

次に完全なコードをまとめて示します。

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error

            // Use a switch statement to do the math
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>次の手順

これでこのチュートリアルは完了です。 さらに詳しく学習するには、引き続き以下のチュートリアルをご覧ください。

> [!div class="nextstepaction"]
> [C# のチュートリアル](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>関連項目

* [ビデオ コース: 全くの初心者向けの C# の基本](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
* [Visual Studio での C# コードのデバッグについて理解する](tutorial-debugger.md)