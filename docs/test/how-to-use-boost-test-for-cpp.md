---
title: "Visual Studio で C++ 用の Boost.Test を使用する方法 | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bfce4aa4153d8f01fa9ef6cd6dc0d4b08eedbc4
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Visual Studio で C++ 用の Boost.Test を使用する方法
**Visual Studio 2017 バージョン 15.5** 以降では、Boost.Test が **C++ ワークロードでのデスクトップ開発**のコンポーネントとして Visual Studio IDE に統合されています。 お使いのコンピューターにインストールするには、Visual Studio インストーラーを起動し、ワークロード コンポーネントの一覧で **Boost.Test Adapter** を見つけます。

![Boost Test のインストール](media/cpp-boost-component.png "Boost.Test for C++ のインストール")

## <a name="install-boost"></a>Boost をインストールする

 Boost.Test には [Boost](http://www.boost.org/) が必要です。 Boost がインストールされていない場合は、Vcpkg パッケージ マネージャーを使うことをお勧めします。 

1. 「[vcpkg: Windows 用の C++ パッケージ マネージャー](/cpp/vcpkg)」の説明に従って、vcpkg をインストールします (まだない場合)。
2. `vcpkg install boost` を実行して Boost ライブラリをインストールします。
3. `vcpkg integrate install` コマンドを実行して、ライブラリで Visual Studio を構成し、Boost のヘッダーとバイナリへのパスを組み込みます。 

## <a name="create-a-project-for-your-tests"></a>テスト用のプロジェクトを作成する
Visual Studio 2017 バージョン 15.5 には、Boost.Test に利用できる構成済みのテスト プロジェクトまたは項目テンプレートはありません。 したがって、テストを保持するコンソール アプリケーション プロジェクトを作成する必要があります。 Visual Studio の将来のバージョンには、Boost.Test 用のテスト テンプレートが組み込まれる予定です。 

1. **ソリューション エクスプローラー**で、ソリューション ノードを右クリックして、**[追加] > [新しいプロジェクト]** の順に選びます。 
2. 左側のウィンドウで **[Windows デスクトップ]** を選び、中央のウィンドウで **[Windows コンソール アプリケーション]** を選びます。 
3. プロジェクト名を設定し、**[OK]** をクリックします。 

## <a name="add-include-directives"></a>インクルード ディレクティブを追加する
テストの .cpp ファイルで、必要な `#include` ディレクティブを追加して、プログラムの型と関数がテスト コードに認識されるようにします。 通常、プログラムはフォルダー階層で 1 つ上のレベルです。 「`#include "../"`」と入力すると IntelliSense ウィンドウが表示され、ヘッダー ファイルへの完全パスを選択できます。

![#include ディレクティブを追加する](media/cpp-gtest-includes.png "テストの .cpp ファイルに include ディレクティブを追加する")

少なくとも、`#include <path>/unit_test.hpp` で [Boost.Test の単一ヘッダー バリアント](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html)をインクルードし、`BOOST_TEST_MODULE` を定義する必要があります。 テストが**テスト エクスプローラー**で検出されるのに十分な例を次に示します。

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>テストを作成して実行する
Boost テストを作成して実行する準備が整いました。 テスト マクロについては、[Boost Test ライブラリのドキュメント](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html)をご覧ください。 **テスト エクスプローラー**を使ってテストを検出、実行、グループ化する方法については、「[テスト エクスプローラーを使用して単体テストを実行する](run-unit-tests-with-test-explorer.md)」をご覧ください。

## <a name="see-also"></a>関連項目
[C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)


  







