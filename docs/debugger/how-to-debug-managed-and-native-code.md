---
title: 'チュートリアル: マネージ コードとネイティブ コード (混在モード) のデバッグします。'
description: 混合モード デバッグを使用して .NET Core または .NET Framework アプリからネイティブ DLL をデバッグする方法について説明します
ms.custom: ''
ms.date: 04/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 1f34f6af0a98e71f5feb910f84e8d67ada051ae9
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057038"
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>チュートリアル: Visual Studio でマネージ コードとネイティブ コードをデバッグします。

Visual Studio デバッガーの 1 つ以上の種類をデバッグするときに混合モードのデバッグと呼ばれるを有効にすることができます。 このチュートリアルでは、1 つのデバッグ セッションでマネージ コードとネイティブの両方のコードをデバッグするオプションを設定します。 このチュートリアルは、管理対象アプリからネイティブ コードをデバッグする方法を示しますが、その逆を実行することもでき、[ネイティブ アプリからマネージ コードをデバッグ](../debugger/how-to-debug-in-mixed-mode.md)します。 デバッガーは、他の種類のデバッグなど、混合モードのデバッグもサポートしています。 [Python とネイティブ コード](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)と ASP.NET などのアプリの種類のスクリプト デバッガーを使用します。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * 単純なネイティブ DLL を作成します。
> * DLL を呼び出す単純な .NET Core または .NET Framework アプリを作成します。
> * デバッガーを起動します。
> * 管理対象アプリでのブレークポイントにヒットします。
> * ネイティブ コードにステップ イン

## <a name="prerequisites"></a>前提条件

* Visual Studio をインストールする必要があります、 **C++ によるデスクトップ開発**ワークロード。

    Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

    ワークロードをインストールする必要があるが、既に Visual Studio を所有している場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

* いずれかをいる必要があります、 **.NET デスクトップ開発**ワークロードまたは **.NET Core クロス プラットフォーム開発**ワークロードがインストールされているアプリの種類に応じて作成します。

## <a name="create-a-simple-native-dll"></a>単純なネイティブ DLL を作成します。

1. Visual Studio で、次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

1. **新しいプロジェクト** ダイアログ ボックスで、選択**Visual C**、**全般**し、インストールされているテンプレート セクションから、中央のペインで選択**空のプロジェクト**.

1. **名前**フィールドに「**混合モード デバッグ** をクリック**OK**します。

    Visual Studio では、右側のウィンドウで、ソリューション エクスプ ローラーで表示される空のプロジェクトを作成します。

1. ソリューション エクスプ ローラーで右クリックし、**ソース ファイル**ノード、C++ でプロジェクトを選び、**追加** > **新しい項目の**、し、 **C++ファイル (.cpp)** します。 ファイルの名前を付けます**Mixed Mode.cpp**、選択**追加**します。

    Visual Studio では、新しい C++ ファイルを追加します。

1. 次のコードをコピー *Mixed Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. ソリューション エクスプ ローラーで右クリックし、**ヘッダー ファイル**ノード、C++ でプロジェクトを選び、**追加** > **新しい項目の**、し、 **ヘッダー ファイル (.h)** します。 ファイルの名前を付けます**Mixed Mode.h**、選択**追加**します。

    Visual Studio では、新しいヘッダー ファイルを追加します。

1. 次のコードをコピー *Mixed Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
        __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
            return a * b;
        }
    }
    #endif
    ```

1. デバッグ ツールバーで、次のように選択します。、**デバッグ**構成と**Any CPU**としてのプラットフォームまたは .NET Core の、選択**x64**プラットフォームとして。

    > [!NOTE]
    > .NET Core では、選択**x64**プラットフォームとして。 これは、必要な .NET core は常に 64 ビット モードで実行されます。

1. ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし (**混合モード デバッグ**) 選択**プロパティ**します。

1. **プロパティ**ページで、選択**構成プロパティ** > **リンカー** > **詳細**と次に、**エントリ ポイントなし**ドロップダウン リストで、**いいえ**します。 設定を適用します。

1. **プロパティ**ページで、選択**構成プロパティ** > **全般**、し、**ダイナミック ライブラリ (.dll)** から、**構成の種類**フィールド。 設定を適用します。

    ![ネイティブ DLL に切り替える](../debugger/media/mixed-mode-set-as-native-dll.png)

1. プロジェクトを右クリックし、選択**デバッグ** > **ビルド**します。

    プロジェクトがエラーのない状態でビルドされます。

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>DLL を呼び出す単純な .NET Framework または .NET Core アプリを作成します。

1. Visual Studio で、次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

1. アプリケーション コードのテンプレートを選択します。

    .NET Framework 用で、**新しいプロジェクト** ダイアログ ボックスで、選択**Visual c#**、 **Windows デスクトップ**インストールされているテンプレート セクションから、中央のペインの選択で**コンソール アプリ (.NET Framework)** します。

    .NET core での**新しいプロジェクト** ダイアログ ボックスで、選択**Visual c#**、 **.NET Core**し、インストールされているテンプレート セクションから、中央のペインで選択**コンソール アプリ (.NET Core)** します。

1. **名前**フィールドに「 **Mixed_Mode_Calling_App**  をクリック**OK**します。

    Visual Studio では、右側のウィンドウで、ソリューション エクスプ ローラーで表示されるコンソール プロジェクトを作成します。

1. *Program.cs*既定のコードを次のコードに置き換えます。

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed-Mode-Debugging\x64\Debug\Mixed-Mode-Debugging.dll
            // Here, we show a typical path for a DLL targeting the **Any CPU** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed-Mode-Debugging\Debug\Mixed-Mode-Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="configure-mixed-mode-debugging-net-framework"></a>混合モードのデバッグ (.NET Framework) の構成します。

1. ソリューション エクスプ ローラーで右マネージ**Mixed_Mode_Calling_App**プロジェクト**スタートアップ プロジェクトとして設定**します。

1. マネージを右クリックして**Mixed_Mode_Calling_App**プロジェクトを選び、**プロパティ**を選び、**デバッグ**左側のウィンドウでします。 選択**ネイティブ コードのデバッグを有効にする**、変更を保存するプロパティ ページを閉じます。

    ![混合モード デバッグを有効にします。](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>混合モードのデバッグ (.NET Core) を構成します。

ほとんどのバージョンの Visual Studio 2017 では、ネイティブ コードを使用して .NET Core アプリでの混合モードのデバッグを有効する必要があります、 *launchSettings.json*ファイルの代わりに、**プロパティ**ページ。 この機能の UI の更新を追跡するには、参照[GitHub 問題](https://github.com/dotnet/project-system/issues/1125)します。

1. 開く、 *launchSettings.json*ファイル、*プロパティ*フォルダー。 既定では、この場所にファイルが表示されます。

    *C:\Users\<ユーザー名 > \source\repos\Mixed_Mode_Calling_App\Properties*

    ファイルが存在しない場合は、プロジェクトのプロパティを開きます (マネージを右クリックして**Mixed_Mode_Calling_App**順に選択してソリューション エクスプ ローラーで**プロパティ**)。 一時的な変更を加える、**デバッグ**タブし、プロジェクトをビルドします。 行った変更を元に戻します。

1. *Lauchsettings.json*ファイルに、次のプロパティを追加します。

    ```csharp
    "nativeDebugging": true
    ```

    そのためなど、ファイルは、次のようになります可能性があります。

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-the-debugger"></a>ブレークポイントを設定し、デバッガーを起動します

1. C# プロジェクトで開きます*Program.cs*し、左側の余白をクリックして、次のコード行にブレークポイントを設定します。

    ```csharp
    int result = Multiply(7, 7);
    ```

    ブレークポイントを設定することを示す左余白に赤い円が表示されます。

1. キーを押して**f5 キーを押して**(**デバッグ** > **デバッグの開始**)、デバッガーを開始します。

    デバッガーは、設定したブレークポイントで一時停止します。 黄色の矢印は、デバッガーが現在一時停止を示します。

## <a name="step-into-native-code"></a>ネイティブ コードにステップ イン

1. 管理対象アプリで一時停止、中にキーを押して**F11** (**デバッグ** > **ステップ イン**)。

    ネイティブ コードとヘッダー ファイルが開き、黄色の矢印が、デバッガーが一時停止した場所を参照してください。

    ![ネイティブ コードにステップ イン](../debugger/media/mixed-mode-step-into-native-code.png)

    ここで、セットなどを行うことができますのブレークポイントのヒットし変数の検査と。

1. その値を表示する変数の上でマウス ポインターを移動します。

1. 見て、 **[自動変数]** と**ローカル**変数とその値を表示する windows。

    デバッガーで一時停止、中に、その他のデバッガー機能をなど、使用できる、**ウォッチ**ウィンドウと**呼び出し履歴**ウィンドウ。

1. キーを押して**F11**デバッガーの 1 つの行を進めるためにもう一度です。

1. キーを押して**Shift + F11** (**デバッグ** > **ステップ アウト**) アプリの実行を続行して、管理対象アプリでもう一度一時停止します。

1. アプリを続行するには **F5** キーを押します。

    おめでとうございます! 混合モード デバッグのためのチュートリアルを完了しました。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、混合モード デバッグを有効にすると、管理対象アプリからネイティブ コードをデバッグする方法について説明しました。 その他のデバッガー機能の概要については、次の記事を参照してください。

> [!div class="nextstepaction"]
> [デバッガーでのはじめに](../debugger/debugger-feature-tour.md)
