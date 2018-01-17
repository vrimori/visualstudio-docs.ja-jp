---
title: "Visual Studio で C++ 用の Boost.Test を使用する方法 | Microsoft Docs"
ms.custom: 
ms.date: 01/05/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdf772be03f6021f499b9bf777922d6d2743e0dc
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio で C++ 用の Boost.Test を使用する方法

**Visual Studio 2017 バージョン 15.5** 以降では、Boost.Test テスト アダプターが **[C++ によるデスクトップ開発]** ワークロードのコンポーネントとして Visual Studio IDE に統合されています。

![Boost.Test のテスト アダプター](media/cpp-boost-component.png "Boost.Test コンポーネントのテスト アダプター")

**[C++ によるデスクトップ開発]** ワークロードがインストールされていない場合は、**Visual Studio インストーラー**を開いて、**[変更]** を選択します。 **[C++ によるデスクトップ開発]** ワークロードを選んで、**[変更]** ボタンを選択します。

## <a name="install-boost"></a>Boost をインストールする

Boost.Test には [Boost](http://www.boost.org/) が必要です。 Boost がインストールされていない場合は、Vcpkg パッケージ マネージャーを使うことをお勧めします。

1. 「[vcpkg: Windows 用の C++ パッケージ マネージャー](/cpp/vcpkg)」の説明に従って、vcpkg をインストールします (まだない場合)。

1. Boost.Test のダイナミック ライブラリまたはスタティック ライブラリをインストールします。

    - Boost.Test のダイナミック ライブラリをインストールするには、`vcpkg install boost-test` を実行します。
    
       または
       
    - Boost.Test のスタティック ライブラリをインストールするには、`vcpkg install boost-test:x86-windows-static` を実行します。

1. `vcpkg integrate install` を実行して、ライブラリで Visual Studio を構成し、Boost のヘッダーとバイナリへのパスを組み込みます。

## <a name="create-a-project-for-your-tests"></a>テスト用のプロジェクトを作成する

> [!NOTE]
> Visual Studio 2017 バージョン 15.5 には、Boost.Test に利用できる構成済みのテスト プロジェクトまたは項目テンプレートはありません。 したがって、テストを保持するコンソール アプリケーション プロジェクトを作成する必要があります。 Visual Studio の将来のバージョンには、Boost.Test 用のテスト テンプレートが組み込まれる予定です。

1. **ソリューション エクスプローラー**で、ソリューション ノードを右クリックして、**[追加]** > **[新しいプロジェクト...]** の順に選択します。

1. 左側のウィンドウで **[Visual C++]** > **[Windows デスクトップ]** を選んだ後、**[Windows コンソール アプリケーション]** テンプレートを選択します。

1. プロジェクト名を設定し、**[OK]** を選択します。

## <a name="link-and-configuration-boost-static-library-only"></a>リンクと構成 (Boost スタティック ライブラリのみ)

Boost.Test テストを実行するようにプロジェクトを構成します。

1. プロジェクト ファイルを編集するには、最初にプロジェクト ファイルをアンロードします。 **ソリューション エクスプローラー**で、プロジェクト ノードを右クリックして **[プロジェクトのアンロード]** を選択します。 次に、プロジェクト ノードを右クリックして、**[<名前\>.vcxproj の編集]** を選択します。

1. 次に示すように、**Globals** プロパティ グループに 2 つの行を追加します。

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
1. \*.vcxproj ファイルを保存して閉じた後、プロジェクトをリロードします。

1. **プロパティ ページ**を開くには、プロジェクト ノードを右クリックして、**[プロパティ]** を選択します。

1. **[C/C++]** > **[コード生成]** の順に展開し、**[ランタイム ライブラリ]** を選択します。 デバッグ スタティック ランタイム ライブラリの場合は `/MTd` を選び、リリース スタティック ランタイム ライブラリの場合は `/MT` を選びます。

1. **[リンカー] > [システム]** を展開します。 **[サブシステム]** が **[コンソール]** に設定されていることを確認します。

1. **[OK]** を選んで、プロパティ ページを閉じます。

## <a name="add-include-directives"></a>インクルード ディレクティブを追加する

1. `main` 関数がテストの .cpp ファイルにある場合は、それを削除します。

1. テストの .cpp ファイルで、必要な `#include` ディレクティブを追加して、プログラムの型と関数がテスト コードに認識されるようにします。 通常、プログラムはフォルダー階層で 1 つ上のレベルです。 「`#include "../"`」と入力すると IntelliSense ウィンドウが表示され、ヘッダー ファイルへの完全パスを選択できます。

   ![#include ディレクティブを追加する](media/cpp-gtest-includes.png "テストの .cpp ファイルに include ディレクティブを追加する")

   次のようにすると、スタンドアロン ライブラリを使うことができます。

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   または、次のようにすると、単一ヘッダー バージョンを使うことができます。

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   次に、`BOOST_TEST_MODULE` を定義します。

テストが**テスト エクスプローラー**で検出されるのに十分な例を次に示します。

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my\_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>テストを作成して実行する
Boost テストを作成して実行する準備が整いました。 テスト マクロについては、[Boost Test ライブラリのドキュメント](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html)をご覧ください。 **テスト エクスプローラー**を使ってテストを検出、実行、グループ化する方法については、「[テスト エクスプローラーを使用して単体テストを実行する](run-unit-tests-with-test-explorer.md)」をご覧ください。

## <a name="see-also"></a>関連項目
[C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)
