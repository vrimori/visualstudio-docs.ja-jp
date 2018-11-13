---
title: 'チュートリアル: マネージ コードとネイティブ コード (混在モード) のデバッグします。'
description: 混合モード デバッグを使用して .NET Core または .NET Framework アプリからネイティブ DLL をデバッグする方法について説明します
ms.custom: ''
ms.date: 11/02/2018
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
ms.openlocfilehash: 121584611dcf0f25fa1f32a616253ecdecf04332
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295762"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>チュートリアル: 同じデバッグ セッションでのマネージ コードとネイティブ コードをデバッグします。

Visual Studio では、混合モードのデバッグと呼ばれる、デバッグ セッションで 1 つ以上のデバッガーの種類を有効にすることができます。 このチュートリアルでは、1 つのデバッグ セッションでマネージ コードとネイティブの両方のコードをデバッグについて説明します。 

このチュートリアルは、管理対象アプリからネイティブ コードをデバッグする方法を示しますが、することもできます[ネイティブ アプリからマネージ コードをデバッグ](../debugger/how-to-debug-in-mixed-mode.md)します。 デバッガーは、他の種類のデバッグなど、混合モードのデバッグもサポートしています。 [Python とネイティブ コード](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)、ASP.NET などのアプリの種類のスクリプト デバッガーを使用するとします。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * 単純なネイティブ DLL を作成します。
> * DLL を呼び出す単純な .NET Core または .NET Framework アプリを作成します。
> * 混合モード デバッグを構成します。
> * デバッガーを起動します。
> * 管理対象アプリでのブレークポイントにヒットします。
> * ネイティブ コードにステップ イン

## <a name="prerequisites"></a>必須コンポーネント

Visual Studio をインストールし、次のワークロードが必要です。
- **C++ によるデスクトップ開発**
- いずれか **.NET デスクトップ開発**または **.NET Core クロス プラットフォーム開発**、作成するアプリの種類によって異なります。

Visual Studio を持っていない場合は、 [Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) を無料でインストールするページ。

Visual Studio がインストールされているワークロードを選択する必要がない場合**Visual Studio インストーラーを開く**Visual Studio の左側のウィンドウで**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーでして選択して、ワークロードを選択します。**変更**します。

## <a name="create-a-simple-native-dll"></a>単純なネイティブ DLL を作成します。

**DLL プロジェクトのファイルを作成します。**

1. Visual Studio で、次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

1. **新しいプロジェクト**ダイアログ ボックスで、 **Visual C**を選択します**他**、し、**空のプロジェクト**中央のペインでします。

1. **名前**フィールドに「 **Mixed_Mode_Debugging**、し、 **OK**。

   Visual Studio は、空のプロジェクトを作成し、表示で**ソリューション エクスプ ローラー**します。

1. **ソリューション エクスプ ローラー**を選択します**ソースファイル**、し、**プロジェクト** > **新しい項目の追加**します。 または、右クリック**ソース ファイル**選択**追加** > **新しい項目の**します。 

1. **新しい項目の**ダイアログ ボックスで、 **C++ ファイル (.cpp)** します。 型**Mixed_Mode.cpp**で、**名前**フィールドを選び**追加**します。

    Visual Studio は、C++ の新しいファイルを追加します。**ソリューション エクスプ ローラー**します。

1. 次のコードをコピー *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. **ソリューション エクスプ ローラー**、**ヘッダー ファイル**、し、**プロジェクト** > **新しい項目の追加**。 または、右クリック**ヘッダー ファイル**選択**追加** > **新しい項目の**します。 

1. **新しい項目の**ダイアログ ボックスで、**ヘッダー ファイル (.h)** します。 型**Mixed_Mode.h**で、**名前**フィールドを選び**追加**します。

   Visual Studio に新しいヘッダー ファイルを追加します**ソリューション エクスプ ローラー**します。

1. 次のコードをコピー *Mixed_Mode.h*:

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

1. 選択**ファイル** > **すべて保存**またはキーを押します**Ctrl**+**Shift**+**S**ファイルに保存します。

**構成して、DLL プロジェクトを作成します。**

1. Visual Studio のツールバーで選択**デバッグ**構成と**x86**または**x64**プラットフォーム。 呼び出し元のアプリが常に 64 ビット モードで実行され、.NET Core の場合は、選択**x64**プラットフォームとして。

1. **ソリューション エクスプ ローラー**を選択、 **Mixed_Mode_Debugging**プロジェクト ノードと選択、**プロパティ**アイコン、またはプロジェクト ノードを右クリックし、を選択します **。プロパティ**します。

1. 上部にある、**プロパティ**ウィンドウで、ことを確認、**構成**に設定されている**アクティブ (debug)** と**プラットフォーム**ことと同じですツールバーの設定: **x64**、または**Win32** x86 プラットフォーム。 

   > [!IMPORTANT]
   > プラットフォームを切り替えた場合**x86**に**x64**またはその逆の場合、新しいプラットフォームのプロパティを再構成する必要があります。 

1. **構成プロパティ**左側のウィンドウで次のように選択します**リンカー** > **詳細**、および横にあるドロップダウンで**のエントリポイントなし。**、**いいえ**します。 変更する必要がある。 場合**いいえ**を選択します**適用**します。

1. **構成プロパティ**を選択します**全般**、および横にあるドロップダウンで**構成の種類**を選択します**ダイナミック ライブラリ (.dll)**. 選択**適用**、し、 **OK**します。

   ![ネイティブ DLL に切り替える](../debugger/media/mixed-mode-set-as-native-dll.png)

1. プロジェクトを選択**ソリューション エクスプ ローラー**選び**ビルド** > **ソリューションのビルド**、キーを押して**F7**、または右クリックプロジェクトと選択**ビルド**します。

   プロジェクトがエラーのない状態でビルドされます。

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>DLL を呼び出す単純な管理対象アプリを作成します。

1. Visual Studio で、次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

   > [!NOTE]
   > 既存の C++ ソリューションに新しいマネージ プロジェクトを追加することもできます、新しいソリューションを作成するより多くのデバッグ シナリオ サポートしています。

1. **新しいプロジェクト**ダイアログ ボックスで、 **Visual C#** 、および中央のウィンドウで。

   - .NET Framework アプリでは、次のように選択します。**コンソール アプリ (.NET Framework)** します。
   
   - .NET Core アプリでは、次のように選択します。**コンソール アプリ (.NET Core)** します。

1. **名前**フィールドに「 **Mixed_Mode_Calling_App**、し、 **OK**。

   Visual Studio は、空のプロジェクトを作成し、表示で**ソリューション エクスプ ローラー**します。

1. すべてのコードに置き換えます*Program.cs*を次のコード。

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
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
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

1. 新しいコードでのファイル パスを置き換える`[DllImport]`をファイル パスに、 *Mixed_Mode_Debugging.dll*で作成しました。 ヒントのためのコードのコメントを参照してください。 置き換えてください、 *username*プレース ホルダーです。

1. 選択**ファイル** > **Program.cs を保存**またはキーを押します**Ctrl**+**S**ファイルを保存します。

## <a name="configure-mixed-mode-debugging"></a>混合モード デバッグを構成します。 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>混合モード デバッグ、.NET Framework アプリを構成するには 

1. **ソリューション エクスプ ローラー**を選択、 **Mixed_Mode_Calling_App**プロジェクト ノードと選択、**プロパティ**アイコン、またはプロジェクト ノードを右クリックし、を選択します **。プロパティ**します。

1. 選択**デバッグ**左側のウィンドウで、選択、**ネイティブ コードのデバッグを有効にする**チェック ボックスをオンし、変更を保存するプロパティ ページを閉じます。

    ![混合モード デバッグを有効にします。](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>混合モード デバッグ、.NET Core アプリを構成するには 

ほとんどのバージョンの Visual Studio 2017 では、使用する必要があります、 *launchSettings.json* .NET Core アプリでネイティブ コードの混合モードのデバッグを有効にするプロジェクトのプロパティではなくファイル。 この機能の UI の更新を追跡するには、参照[GitHub 問題](https://github.com/dotnet/project-system/issues/1125)します。

1. **ソリューション エクスプ ローラー**、展開**プロパティ**を開き、 *launchSettings.json*ファイル。 

   >[!NOTE]
   >既定では、 *launchSettings.json*に*C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*します。 場合*launchSettings.json*存在、 **Mixed_Mode_Calling_App**プロジェクト**ソリューション エクスプ ローラー**を選び、 **プロパティ**アイコン、またはプロジェクトを右クリックし、選択**プロパティ**します。 一時的な変更を加える、**デバッグ**タブをクリックし、プロジェクトをビルドします。 これは、作成、 *launchSettings.json*ファイル。 行った変更を元に戻す、**デバッグ**タブ。

1. *Lauchsettings.json*ファイルに、次の行を追加します。

    ```csharp
    "nativeDebugging": true
    ```

    完全なファイルは、次の例のようになります。

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

## <a name="set-a-breakpoint-and-start-debugging"></a>ブレークポイントを設定し、デバッグを開始

1. C#プロジェクトを開き、 *Program.cs*します。 一番左の余白をクリックし、行を選択すると、キーを押してして次のコード行にブレークポイントを設定**F9**、行を右クリックし、選択または**ブレークポイント** >  **ブレークポイントの挿入**します。

    ```csharp
    int result = Multiply(7, 7);
    ```

    ブレークポイントを設定した左余白に赤い円が表示されます。

1. キーを押して**F5**、Visual Studio のツールバーで緑色の矢印を選択または選択**デバッグ** > **デバッグの開始**デバッグを開始します。

   デバッガーは、設定したブレークポイントで一時停止します。 黄色の矢印は、デバッガーが現在一時停止を示します。

## <a name="step-in-and-out-of-native-code"></a>ネイティブ コードと出力の手順

1. 管理対象アプリでのデバッグが一時停止中のキーを押して**F11**、または選択**デバッグ** > **ステップ イン**します。

   *Mixed_Mode.h*ネイティブ ヘッダー ファイルが開いたら、および黄色の矢印が、デバッガーが一時停止した場所を参照してください。

   ![ネイティブ コードにステップ イン](../debugger/media/mixed-mode-step-into-native-code.png)

1. ここで、設定のブレークポイントのヒットしし、ネイティブまたはマネージ コード内の変数を検査できます。

   - その値を表示するソース コード内の変数をポイントします。

   - 変数とその値を見て、 **[自動変数]** と**ローカル**windows。

   - デバッガーで一時停止、中に使用することも、**ウォッチ**windows および**呼び出し履歴**ウィンドウ。

1. キーを押して**F11**デバッガーの 1 つの行を進めるためにもう一度です。

1. キーを押して**Shift**+**F11**または選択**デバッグ** > **ステップ アウト**実行を続行し、もう一度で一時停止、管理対象アプリ。

1. キーを押して**F5**またはアプリのデバッグを続行する緑色の矢印を選択します。

おめでとうございます! 混合モード デバッグのためのチュートリアルを完了しました。

## <a name="next-step"></a>次のステップ

このチュートリアルでは、混合モード デバッグの有効化して、管理対象アプリからネイティブ コードをデバッグする方法について説明しました。 その他のデバッガー機能の概要についてを参照してください。

> [!div class="nextstepaction"]
> [デバッガーでのはじめに](../debugger/debugger-feature-tour.md)
