---
title: C++ 用の CTest を使用する方法
ms.date: 11/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 7a4475cba023f792c2ff96895eb4dd7e0b4ebcf5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050214"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Visual Studio で C++ 用の CTest を使用する方法

CMake (CTest を含む) は、**C++ ワークロードでのデスクトップ開発**のコンポーネントとして Visual Studio IDE に既定で統合されています。 お使いのコンピューターにインストールする必要がある場合は、Visual Studio インストーラー プログラムを開き、**[変更]** ボタンをクリックします。次に、ワークロード コンポーネントの一覧で [[CMake Tools for Visual C++]](/cpp/ide/cmake-tools-for-visual-cpp) をオンにします。

## <a name="to-write-tests"></a>テストを記述するには

Visual Studio の CMake サポートでは、Visual Studio プロジェクト システムを必要としません。 したがって、任意の CMake 環境の場合と同様に、CTest テストを記述して構成します。 Visual Studio での CMake 使用の詳細については、[Visual C++ 用の CMake ツール](/cpp/ide/cmake-tools-for-visual-cpp)に関する記事を参照してください。

## <a name="to-run-tests-visual-studio-2017-version-156"></a>テストを実行するには (Visual Studio 2017 バージョン 15.6)

Visual Studio 2017 バージョン 15.6 では、CTest は**テスト エクスプローラー**に完全に統合され、Google 単体テスト フレームワークと Boost 単体テスト フレームワークの両方もサポートしています。 これらのフレームワークは、**C++ ワークロードでのデスクトップ開発** にコンポーネントとして既定で含まれています。 ただし、Visual Studio の以前のバージョンからプロジェクトをアップグレードする場合は、Visual Studio インストーラー プログラムを使用してこれらのフレームワークをインストールする必要があります。

次の図は、Google テスト フレームワークを使用して実行した CTest の結果を示しています。

![VS2017 15.6 での Google Test Framework による CTest](media/ctest-test-explorer.png)

CTest を使用するが、Google アダプターまたは Boost アダプターを使用していない場合、結果は、個別のテスト方法レベルではなく、CTest レベルで表示されます。 CTest 専用実行可能ファイルのデバッグとステップ実行を行うことができますが、個々のテストのスタック トレースはサポートされません。

## <a name="to-run-tests-visual-studio-2017-version-155"></a>テストを実行するには (Visual Studio 2017 バージョン 15.5)

**Visual Studio 2017 バージョン 15.5** では、CTest は**テスト エクスプローラー**に統合されていません。 テストは、CMake のメイン メニューから実行するか、または**ソリューション エクスプローラー**で *CMakeLists.txt* ファイルに対するコンテキスト メニューから実行することができます。 テストの結果は、Visual Studio の **[出力ウィンドウ]** に送られます。

![VS2017 15.5 での CTest テストの実行](media/cpp-cmake-run-tests.png)

## <a name="see-also"></a>関連項目

[C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)