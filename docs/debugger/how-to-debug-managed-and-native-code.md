---
title: 'チュートリアル: マネージ コードとネイティブ コードのデバッグ |Microsoft ドキュメント'
description: .NET Core または .NET Framework アプリからネイティブ DLL をデバッグする方法をについてください。
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
ms.openlocfilehash: aeb74bac5196450ec98426727a1456a009adb5c1
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>チュートリアル: Visual Studio でのマネージ コードとネイティブ コードをデバッグします。

Visual Studio では、デバッガーの 1 つ以上の種類をデバッグするときに混合モードのデバッグと呼ばれるを有効にすることができます。 このチュートリアルでは、単一のデバッグ セッションでマネージとネイティブ コードの両方をデバッグするオプションを設定します。 このチュートリアルは、管理対象アプリからのネイティブ コードをデバッグする方法を示しますが、その逆を実行することもでき、[ネイティブ アプリからマネージ コードをデバッグ](../debugger/how-to-debug-in-mixed-mode.md)です。 デバッガーは、他の種類のデバッグなど、混合モードのデバッグもサポートしています。 [Python とネイティブ コード](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)と ASP.NET などの種類のアプリで、スクリプト デバッガーを使用します。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * 単純なネイティブ DLL を作成します
> * DLL を呼び出す単純な .NET Core または .NET Framework アプリを作成します。
> * デバッガーを起動します。
> * 管理対象アプリでのブレークポイントをヒットします。
> * ネイティブ コードにステップ イン

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio をインストールする必要があります、 **C++ を使用したデスクトップ開発**ワークロード。

    まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。

    ワークロードをインストールする必要があるが、既に Visual Studio を所有している場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

* いずれかを持つ必要があります、 **.NET デスクトップ開発**ワークロードまたは**クロス プラットフォーム開発 .NET Core**ワークロードがインストールされている、どのアプリの種類に応じて作成します。

## <a name="create-a-simple-native-dll"></a>単純なネイティブ DLL を作成します

1. Visual Studio で、次のように選択します。**ファイル** > **新規** > **プロジェクト**です。

1. **新しいプロジェクト** ダイアログ ボックスで、選択**Visual C**、**全般**し、インストールされたテンプレート セクションから、中央のペインで選択**空のプロジェクト**.

1. **名前**フィールドに「**混合モード デバッグ** をクリック**OK**です。

    Visual Studio では、右側のウィンドウで、ソリューション エクスプ ローラーで表示される空のプロジェクトを作成します。

1. ソリューション エクスプ ローラーで右クリックし、**ソース ファイル**ノード、C++ ではプロジェクトをクリックして**追加** > **新しい項目の**、し、 **C++ファイル (.cpp)** です。 ファイルの名前を付けます**Mixed Mode.cpp**を選択して**追加**です。

    Visual Studio では、新しい C++ ファイルを追加します。

1. 次のコードをコピー *Mixed Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. ソリューション エクスプ ローラーで右クリックし、**ヘッダー ファイル**ノード、C++ ではプロジェクトをクリックして**追加** > **新しい項目の**、し、 **ヘッダー ファイル (.h)** です。 ファイルの名前を付けます**Mixed Mode.h**を選択して**追加**です。

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

1. [デバッグ] ツールバーを選択、**デバッグ**構成と**Any CPU** 、プラットフォームとして場合 .NET core は選択**x64**プラットフォームとして。

    > [!NOTE]
    > .NET Core 順にクリックして**x64**プラットフォームとして。 これは、必要なために、.NET core は 64 ビット モードで必ず実行されます。

1. ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし (**混合モード デバッグ**) を選択して**プロパティ**です。

1. **プロパティ**ページで、選択**構成プロパティ** > **リンカー** > **詳細**、および次に、**エントリ ポイントなし**ドロップダウン リストで、**いいえ**です。 設定を適用します。

1. **プロパティ**ページで、選択**構成プロパティ** > **全般**、し、**ダイナミック ライブラリ (.dll)** から、**構成の種類**フィールドです。 設定を適用します。

    ![ネイティブ DLL に切り替える](../debugger/media/mixed-mode-set-as-native-dll.png)

1. プロジェクトを右クリックして選択**デバッグ** > **ビルド**です。

    プロジェクトがエラーのない状態でビルドされます。

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>DLL を呼び出す単純な .NET Framework または .NET Core アプリを作成します。

1. Visual Studio で、次のように選択します。**ファイル** > **新規** > **プロジェクト**です。

1. アプリケーション コードのテンプレートを選択します。

    .NET Framework 用で、**新しいプロジェクト** ダイアログ ボックスで、選択**Visual c#**、 **Windows クラシック デスクトップ**インストールされたテンプレート セクションから、中央のペインで、選択**コンソール アプリケーション (.NET Framework)** です。

    .NET core で、**新しいプロジェクト** ダイアログ ボックスで、選択**Visual c#**、 **.NET Core**し、インストールされたテンプレート セクションから、中央のペインで選択**コンソール アプリケーション (.NET Core)** です。

1. **名前**フィールドに「 **Mixed_Mode_Calling_App**  をクリック**OK**です。

    Visual Studio では、右側のウィンドウで、ソリューション エクスプ ローラーで表示されるコンソール プロジェクトを作成します。

1. *Program.cs*既定のコードを次のコードに置き換えます。

    ```c#
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

## <a name="configure-mixed-mode-debugging-net-framework"></a>混合モード (.NET Framework) を構成します。

1. ソリューション エクスプ ローラーで、右クリックし、マネージ**Mixed_Mode_Calling_App**プロジェクト**スタートアップ プロジェクトとして設定**です。

1. マネージを右クリックして**Mixed_Mode_Calling_App**プロジェクトをクリックして**プロパティ**を選択し**デバッグ**左側のウィンドウでします。 選択**ネイティブ コードのデバッグを有効にする**、変更を保存するプロパティ ページを閉じます。

    ![混合モード デバッグを有効にします。](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>混合モード (.NET Core) を構成します。

ほとんどのバージョンの Visual Studio 2017 では、混合モードは、.NET Core を使用してアプリのネイティブ コードのデバッグを有効する必要があります、 *launchSettings.json*ファイルの代わりに、**プロパティ**ページ。 この機能の UI の更新を追跡するためにこれを参照して[GitHub 問題](https://github.com/dotnet/project-system/issues/1125)です。

1. 開く、 *launchSettings.json*ファイルで、*プロパティ*フォルダーです。 既定では、この場所にファイルを見つけることができます。

    *C:\Users\<ユーザー名 > \source\repos\Mixed_Mode_Calling_App\Properties*

    ファイルが存在しない場合は、プロジェクトのプロパティを開きます (マネージを右クリックして**Mixed_Mode_Calling_App**ソリューション エクスプ ローラーでプロジェクトを選択**プロパティ**)。 一時的な変更を加える、**デバッグ**タブし、プロジェクトをビルドします。 加えた変更を元に戻します。

1. *Lauchsettings.json*ファイルに追加し、次のプロパティ。

    ```
    "nativeDebugging": true
    ```
    
    そのためなど、ファイルは次のようになります可能性があります。
    
    ```
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-the-debugger"></a>ブレークポイントを設定し、デバッガーを起動

1. C# プロジェクトで開きます*Program.cs*左余白をクリックして次のコード行にブレークポイントを設定します。

    ```c#
    int result = Multiply(7, 7);
    ```

    ブレークポイントを設定することを示すために、左余白に赤い丸が表示されます。

1. キーを押して**f5 キーを押して**(**デバッグ** > **デバッグの開始**)、デバッガーを起動します。

    デバッガーは、設定したブレークポイントで一時停止します。 黄色の矢印は、デバッガーが現在一時停止を示します。

## <a name="step-into-native-code"></a>ネイティブ コードにステップ イン

1. 管理対象アプリで一時停止、中に、以下のキーを押して**F11** (**デバッグ** > **ステップ イン**)。

    ネイティブ コードとヘッダー ファイルが開き、デバッガーが一時停止して黄色の矢印を参照してください。

    ![ネイティブ コードにステップ イン](../debugger/media/mixed-mode-step-into-native-code.png)

    ここで、セットなどの操作しブレークポイントをヒットしたり、調べたりできます変数。

1. その値を表示する変数上に置きます。

1. 見て、 **[自動変数]** と**ローカル**変数とその値を表示するウィンドウです。

    デバッガーで一時停止、中に、その他のデバッガー機能をなど、使用できる、**ウォッチ**ウィンドウおよび**呼び出し履歴**ウィンドウです。

1. キーを押して**F11**もう一度に 1 行ずつデバッガーを進めるです。

1. キーを押して**Shift + F11** (**デバッグ** > **ステップ アウト**) アプリの実行を継続し、管理対象アプリでもう一度一時停止にします。

1. アプリを続行するには **F5** キーを押します。

    おめでとうございます!  混合モード デバッグのためのチュートリアルを完了しました。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、混合モード デバッグを有効にして、管理対象アプリからのネイティブ コードをデバッグする方法について学習しました。 その他のデバッガー機能の概要については、次の記事を参照してください。

> [!div class="nextstepaction"]
> [デバッガーでのはじめに](../debugger/debugger-feature-tour.md)