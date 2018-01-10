---
title: "Visual Studio で C++ 用の CTest を使用する方法 | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: 989f2b06df55fd0927863fe7e5603d3d0ec90b06
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Visual Studio で C++ 用の CTest を使用する方法
CMake (CTest を含む) は、C++ ワークロードでの**デスクトップ開発**のコンポーネントとして Visual Studio IDE に統合されています。 お使いのコンピューターにインストールするには、Visual Studio インストーラーを起動し、ワークロード コンポーネントの一覧で [CMake Tools for Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) を見つけます。

Visual Studio の CMake サポートでは、Visual Studio プロジェクト システムを必要としません。 したがって、任意の CMake 環境の場合と同様に、CTest テストを記述して構成します。 Visual Studio での CMake 使用の詳細については、「[CMake Tools for Visual C++](/cpp/ide/cmake-tools-for-visual-cpp)」(Visual C++ 用の CMake ツール) を参照してください。

**Visual Studio 2017 バージョン 15.5** CTest は現在、**テスト エクスプローラー**に統合されていません。 テストは、CMake のメイン メニューから実行するか、または**ソリューション エクスプローラー**で **CMakeLists.txt** ファイルに対するコンテキスト メニューから実行することができます。 テストの結果は、Visual Studio の **[出力ウィンドウ]** に送られます。

![CTest テストの実行](media/cpp-cmake-run-tests.png "CTest テストの実行")


## <a name="see-also"></a>参照
[C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)


  







