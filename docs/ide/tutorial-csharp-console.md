---
title: Visual Studio での C# コンソール アプリの概要
description: Visual Studio で C# コンソール アプリを作成する方法について、ステップ バイ ステップで説明します。
ms.custom: ''
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: ad1ee95cb9cc754261502e7377cde6c91e5befce
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859511"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>チュートリアル: Visual Studio での C# コンソール アプリの概要

この C# 用のチュートリアルでは、Visual Studio を使用して、コンソール アプリを作成および実行しながら、[Visual Studio の統合開発環境 (IDE)](visual-studio-ide.md) の一部の機能を検討します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、C# アプリケーション プロジェクトを作成します。 このプロジェクトの種類には、必要となるすべてのテンプレート ファイルが付属していますので、何も追加する必要はありません。

1. Visual Studio 2017 を開きます。

2. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

3. 左側のウィンドウの **[新しいプロジェクト]** ダイアログ ボックスで、**[C#]** を展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[Console App (.NET Core)]** を選択します。 次に、ファイルに *Calculator* という名前を付けます。

   ![Visual Studio IDE の [新しいプロジェクト] ダイアログ ボックスに示されているコンソール アプリ (.NET Core) プロジェクト テンプレート](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>ワークグループを追加する (省略可能)

**コンソール アプリ (.NET Core)** プロジェクト テンプレートが表示されない場合は、**.NET Core クロスプラットフォームの開発**ワークロードを追加して取得できます。 コンピューターにインストールされている Visual Studio 2017 の更新プログラムに応じて、次の 2 つの方法のうちのいずれかでこのワークロードを追加することができます。

#### <a name="option-1-use-the-new-project-dialog-box"></a>オプション 1: [新しいプロジェクト] ダイアログ ボックスを使用する

1. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで、**[Visual Studio インストーラーを開く]** リンクを選択します。

   ![[新しいプロジェクト] ダイアログ ボックスから [Visual Studio インストーラーを開く] リンクを選択する](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. Visual Studio インストーラーが起動します。 **[.NET Core クロスプラットフォームの開発]** ワークロードを選択し、**[変更]** を選択します。

   ![Visual Studio インストーラーの [.NET Core クロスプラットフォームの開発] ワークロード](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>オプション 2: [ツール] メニュー バーを使用する

1. **[新しいプロジェクト]** ダイアログ ボックスを取り消し、上部のメニュー バーから **[ツール]** > **[ツールと機能を取得]** の順に選択します。

1. Visual Studio インストーラーが起動します。 **[.NET Core クロスプラットフォームの開発]** ワークロードを選択し、**[変更]** を選択します。

## <a name="create-a-c-console-calculator-app"></a>"C# Console Calculator" アプリを作成する

1. Visual Studio 2017 を開き、上部のメニュー バーから **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

1. 左側のウィンドウの **[新しいプロジェクト]** ダイアログ ボックスで、**[C#]** を展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[Console App (.NET Core)]** を選択します。 次に、ファイルに *Calculator* という名前を付けます。

1. コード エディターに次のコードを入力または貼り付けます。

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

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
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   `static void Main(string[] args)` の後に現れるコードは、次のスクリーンショットのようになります。

   ![C# Console Calculator を表示するコード エディター](../ide/media/csharp-console-calculator-code.png)

1. **[Calculator]** を選択してプログラムを実行するか、**F5** キーを押します。

   ![[Calculator] ボタンを選択して、ツールバーからアプリを実行する](../ide/media/csharp-console-calculator-button.png)

1. コンソール ウィンドウでアプリを確認します。 画面の指示に従うと、アプリの外観は次のスクリーン ショットのようになります。

    ![アクションを実行するプロンプトを含む、Calculator アプリが表示されているコンソール ウィンドウ。](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>アプリを閉じる

1. 任意のキーを押して、Calculator アプリを閉じます。

1. Visual Studio の **[出力]** ウィンドウを閉じます。

   ![Visual Studio の [出力] ウィンドウを閉じる](../ide/media/csharp-calculator-close-output-pane.png)

1. Visual Studio を閉じます。

## <a name="quick-answers-faq"></a>FAQ に対する簡単な回答

以下の簡単な FAQ で、主な概念をいくつか示します。

### <a name="what-is-c"></a>C# とは何ですか?

C# は、.NET Framework と .NET Core 上で実行される、タイプ セーフなプログラミング言語です。 C# を使用すると、Windows アプリケーション、クライアント/サーバー アプリケーション、データベース アプリケーション、XML Web サービス、分散コンポーネントなど、さまざまなアプリケーションを作成できます。

### <a name="what-is-visual-studio"></a>Visual Studio とは何ですか?

Visual Studio は、開発者向け生産性向上ツールの統合開発スイートです。 プログラムやアプリケーションを作成するために使用できるプログラムのようなものと考えてください。

### <a name="what-is-a-console-app"></a>コンソール アプリとは何ですか?

コンソール アプリは、コマンドライン ウィンドウ (コンソールともいう) で入力を取得して、 出力を表示します。

### <a name="what-is-net-core"></a>.NET Core とは何ですか?

.NET Core は、.NET Framework の次の進化段階です。 .NET Framework ではプログラミング言語間でコードを共有できましたが、.NET Core ではプラットフォーム間でコードを共有する機能が追加されました。 さらに良い点は、オープン ソースであるという点です 

(.NET Framework と .NET Core には、両方とも事前構築済み機能のライブラリが含まれています。 これらには共通言語ランタイム (CLR) も含まれています。これは、コードを実行する仮想マシンのように動作します。)

## <a name="next-steps"></a>次の手順

これでこのチュートリアルは完了です。 さらに詳しく学習するには、引き続き以下のチュートリアルをご覧ください。

> [!div class="nextstepaction"]
> [C# のチュートリアル](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>関連項目

* [超初心者向けの C# の基本ビデオ コース](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
