---
title: "Visual Studio で C++ 用の Google Test を使用する方法 | Microsoft Docs"
ms.date: 11/04/2017
ms.technology: vs-ide-test
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 35cc31bbe7a1d83270035217dc36fce5f3a8ab6d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Visual Studio で C++ 用の Google Test を使用する方法
**Visual Studio 2017 バージョン 15.5** 以降では、Google Test が **C++ ワークロードでのデスクトップ開発**の既定のコンポーネントとして Visual Studio IDE に統合されています。 お使いのコンピューターにインストールされていることを確認するには、Visual Studio インストーラーを起動し、ワークロード コンポーネントの一覧で Google Test を探します。

![Google Test をインストールする](media/cpp-google-component.png "C++ 用 Google Test をインストールする")

## <a name="add-a-google-test-project-to-the-solution"></a>Google Test プロジェクトをソリューションに追加する
1. **ソリューション エクスプローラー**で、ソリューション ノードを右クリックして、**[追加] > [新しいプロジェクト]** の順に選びます。
2. 左側のウィンドウで **[Visual C++] > [テスト]** を選び、中央のウィンドウで **[Google Test Project]\(Google Test プロジェクト\)** を選びます。
3. テスト プロジェクトの名前を設定し、**[OK]** をクリックします。

![新しい Google Test プロジェクト](media/cpp-gtest-new-project.png "新しい Google Test プロジェクトを追加する")

## <a name="configure-the-test-project"></a>テスト プロジェクトを構成する
表示される **[テスト プロジェクト構成]** ダイアログでは、テストするプロジェクトを選ぶことができます。 プロジェクトを選択すると、選んだプロジェクトへの参照が追加されます。 プロジェクトを選ばない場合は、テスト対象のプロジェクトへの参照を手動で追加する必要があります。 Google Test バイナリへのリンクを静的または動的のどちらにするかを選ぶときの考慮事項は、他の C++ プログラムの場合と同様です。 詳細については、「[Visual C++ の DLL](/cpp/build/dlls-in-visual-cpp)」をご覧ください。

 ![Google Test プロジェクトを構成する](media/cpp-gtest-config.png "Google Test プロジェクトを構成する")

## <a name="set-additional-options"></a>その他のオプションを設定する
その他のオプションを設定するには、メイン メニューから **[ツール] > [オプション] > [Test Adapter for Google Test]** を選びます。 これらの設定については、Google Test のドキュメントをご覧ください。

 ![Google Test プロジェクトの設定](media/cpp-gtest-settings.png "Google Test プロジェクトの設定")

## <a name="add-include-directives"></a>インクルード ディレクティブを追加する
テストの .cpp ファイルで、必要な `#include` ディレクティブを追加して、プログラムの型と関数がテスト コードに認識されるようにします。 通常、プログラムはフォルダー階層で 1 つ上のレベルです。 「`#include "../"`」と入力すると IntelliSense ウィンドウが表示され、ヘッダー ファイルへの完全パスを選択できます。

![#include ディレクティブを追加する](media/cpp-gtest-includes.png "テストの .cpp ファイルに include ディレクティブを追加する")

## <a name="write-and-run-tests"></a>テストを作成して実行する
Google Test のテストを作成して実行する準備が整いました。 テスト マクロについては、[Google Test の基礎](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md)に関するページをご覧ください。 **テスト エクスプローラー**を使ってテストを検出、実行、グループ化する方法については、「[テスト エクスプローラーを使用して単体テストを実行する](run-unit-tests-with-test-explorer.md)」をご覧ください。

## <a name="see-also"></a>関連項目
[C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)










