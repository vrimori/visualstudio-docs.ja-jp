---
title: "Visual Studio 内の C++ の概要 | Microsoft Docs"
ms.custom: mvc
ms.date: 12/04/2017
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: get-started-article
author: corob-msft
ms.author: tglee
manager: ghogen
dev_langs: CPP
ms.workload: cplusplus
ms.openlocfilehash: 9c0a7a8e206704e1b7cd694a91f376f4ec531d6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="get-started-with-c-in-visual-studio"></a>Visual Studio 内の C++ の概要

このクイックスタートを完了すると、Visual Studio を使用して C++ のアプリケーションを開発する際に使用できるさまざまなツールおよびダイアログ ボックスの使用方法を習得できます。 "Hello, World" スタイルのコンソール アプリケーションを作成しながら、統合開発環境 (IDE) での作業方法について学習します。

## <a name="prerequisites"></a>必須コンポーネント

このクイックスタートを完了するために C++ について理解しておく必要はありませんが、いくつかの一般的なプログラミングの概念とデバッグの概念については理解しておく必要があります。 Visual Studio のドキュメントでは、C++ でのプログラミング方法を説明しません。 C++ の学習リソースとしては、ISO C++ Web サイトの「[Get Started](https://isocpp.org/get-started)」 (概要) をお勧めします。

作業を進めるには、Visual Studio 2017 バージョン 15.3 以降のコピーと、**C++ によるデスクトップ開発**ワークロードがインストールされている必要があります。 インストールのためのファースト ガイドについては、「[Install C++ support in Visual Studio](/cpp/build/vscpp-step-0-installation)」 (Visual Studio での C++ のインストール サポート) を参照してください。

## <a name="create-a-console-app"></a>コンソール アプリを作成する

Visual Studio がまだ実行されていない場合は、起動します。

![Visual C++ の設定が適用された IDE](../ide/media/get-started-cpp-ide-layout.png "Visual C++ の設定が適用された IDE")

Visual Studio を開くと、IDE の 3 つの基本的なパーツを確認できます。ツール ウィンドウ、メニューとツール バー、およびメイン ウィンドウ領域です。 ツール ウィンドウは、アプリ ウィンドウの左側と右側にドッキングされます。 上部には、**クイック起動**ボックス、メニュー バー、および標準ツールバーがあります。 ウィンドウの中央には、**[スタート ページ]**が表示されます。 ソリューションまたはプロジェクトを開くと、この領域にはエディターとデザイナーが表示されます。 アプリを開発する場合は、ほとんどの時間をこの中央の領域での作業に費やします。

Visual Studio では、"*プロジェクト*" を使用してアプリのコードを整理し、"*ソリューション*" を使用してプロジェクトを整理します。 プロジェクトには、アプリをビルドする場合に使用するすべてのオプション、構成、および規則が含まれています。 また、プロジェクトでは、プロジェクトのすべてのファイルと、外部のファイルとの間のリレーションシップも管理します。 アプリを作成するには、まず、新しいプロジェクトとソリューションを作成します。

### <a name="to-create-a-console-app-project"></a>コンソール アプリ プロジェクトを作成するには

1. メニューバーで **[ファイル]、[新規作成]、[プロジェクト]** の順に選択して、**[新しいプロジェクト]** ダイアログ ボックスを開きます。

   ![メニュー バーで [ファイル]、[新規作成]、[プロジェクト] の順に選択](../ide/media/get-started-cpp-file-new-project-menu.png "メニュー バーで [ファイル]、[新規作成]、[プロジェクト] の順に選択")

1. **[新しいプロジェクト]** ダイアログで、**[インストール]、[Visual C++]** の順に選択する操作をまだ行っていない場合は、実行します。 中央のウィンドウで **[Windows コンソール アプリケーション]** テンプレートを選択します。 **[名前]** 編集ボックスに、「*HelloApp*」と入力します。

   ![[新しいプロジェクト] ダイアログを使用してアプリ プロジェクトを作成する](../ide/media/get-started-cpp-new-project-dialog.png "[新しいプロジェクト] ダイアログを使用してアプリ プロジェクトを作成する")

   ダイアログ ボックスに含まれる選択肢は、インストールされている Visual Studio ワークロードおよびコンポーネントによって異なる場合があります。 Visual C++ プロジェクト テンプレートが見つからない場合は、Visual Studio インストーラーをもう一度実行し、**C++ によるデスクトップ開発**ワークロードをインストールする必要があります。 この作業は、**[新しいプロジェクト]** ダイアログから直接行うことができます。 インストーラーを起動するには、ダイアログで **[Visual Studio インストーラーを開く]** リンクを選択します。

1. **[OK]** ボタンを選択して、アプリのプロジェクトとソリューションを作成します。

   Windows コンソール アプリの基本的なファイルを含む HelloApp プロジェクトとソリューションが作成され、**ソリューション エクスプローラー**に自動的に読み込まれます。 コード エディターで HelloApp.cpp ファイルが開かれます。 次の項目が**ソリューション エクスプローラー**に表示されます。

   ![ソリューション エクスプローラーに表示されたソリューションのファイル](../ide/media/get-started-cpp-solution-explorer.png "ソリューション エクスプローラーに表示されたソリューションのファイル")

## <a name="add-code-to-the-app"></a>アプリケーションにコードを追加する

次に、コンソール ウィンドウに "Hello" という語を表示するコードを追加します。

### <a name="to-edit-code-in-the-editor"></a>エディターでコードを編集するには

1. HelloApp.cpp ファイルの `return 0;` という行の前に空白行を挿入し、次のコードを入力します。

   ```cpp
   cout << "Hello\n";
   ```

   `cout`の下に赤い波線が表示されます。 これにポインターを合わせると、エラー メッセージが表示されます。

   ![cout のエラー テキスト](../ide/media/get-started-cpp-intellisense-error.png "cout のエラー テキスト")

   エラー メッセージは、 **[エラー一覧]** ウィンドウにも表示されます。 このウィンドウを表示するには、メニュー バーで **[表示]、[エラー一覧]** の順に選択します。

   ![[エラー一覧] ウィンドウのエラー](../ide/media/get-started-cpp-error-list.png "[エラー一覧] ウィンドウのエラー")

   コードには [std::cout](/cpp/standard-library/iostream) の宣言が欠落しています。これは \<iostream> ヘッダー ファイルにあります。

1. iostream ヘッダーを組み込むには、このコードを `#include "stdafx.h"` の後に入力します。

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   コードを入力したとき、ボックスが表示されたのに気づいたはずです。 このボックスには、入力した文字のオートコンプリート候補が含まれています。 これは、C++ の IntelliSense の一部で、コーディングの一連のヒントを提供します。それには、クラスやインターフェイスのメンバーやパラメーター情報が含まれます。 定義済みのコード ブロックであるコード スニペットを使用することもできます。 詳細については、 [Using IntelliSense](../ide/using-intellisense.md) および [Code Snippets](../ide/code-snippets.md)を参照してください。

   ![エディターでのコードの修正](../ide/media/get-started-cpp-cout-fix.png "エディターでのコードの修正")

   エラーを修正すると、 `cout` の下の赤い波線が消えます。

1. ファイルに変更内容を保存するには、**Ctrl + S** キーを押します。

## <a name="build-the-app"></a>アプリをビルドする

コードをビルドするのは簡単です。 メニュー バーで、**[ビルド]、[ソリューションのビルド]** の順にクリックします。 Visual Studio は HelloApp ソリューションをビルドし、**[出力]** ウィンドウに進行状況をレポートします。

   ![HelloApp ソリューションのビルド](../ide/media/get-started-cpp-build-solution.gif "HelloApp ソリューションのビルド")

## <a name="debug-and-test-the-app"></a>アプリのデバッグとテスト

HelloApp をデバッグして、コンソール ウィンドウに "Hello" という語が表示されるかどうかを確認できます。

### <a name="to-debug-the-app"></a>アプリをデバッグするには

1. デバッガーを起動するには、メニュー バーで **[デバッグ]、[デバッグ開始]** の順に選択します。

   ![[デバッグ] メニューの [デバッグの開始] コマンド](../ide/media/get-started-cpp-start-debugging-menu.png "[デバッグ] メニューの [デバッグの開始] コマンド")

   デバッガーが起動し、コードが実行されます。 コンソール ウィンドウ (コマンド プロンプトのように見える別のウィンドウ) が数秒間表示されますが、デバッガーが実行を停止するとすぐに閉じます。 テキストを表示するには、ブレークポイントを設定してプログラムの実行を停止する必要があります。

### <a name="to-add-a-breakpoint"></a>ブレークポイントを追加するには

1. エディターで、`return 0;` の行にカーソルを置きます。 メニュー バーで、**[デバッグ]、[ブレークポイントの設定/解除]** の順に選択します。 左側の余白内をクリックしてブレークポイントを設定することもできます。

     ![[デバッグ] メニューの [ブレークポイントの設定/解除] コマンド](../ide/media/get-started-cpp-toggle-breakpoint-menu.png "[デバッグ] メニューの [ブレークポイントの設定/解除] コマンド")

     コード行の横の、エディター ウィンドウの左端の余白部分に、赤い円が表示されます。

     ![ウィンドウの余白部分に表示されたブレークポイント](../ide/media/get-started-cpp-breakpoint-set.png "ウィンドウの余白部分に表示されたブレークポイント")

1. デバッグを開始するには、**F5** キーを押します。

   デバッガーが起動し、コンソール ウィンドウが表示されて **Hello**という語が示されます。

   ![コンソール ウィンドウの Hello テキスト](../ide/media/get-started-cpp-helloapp-window.png "コンソール ウィンドウの Hello テキスト")

1. デバッグを停止するには、**Shift + F5** キーを押します。

コンソール プロジェクトのデバッグの詳細については、[コンソール プロジェクト](../debugger/debugging-preparation-console-projects.md)に関するページを参照してください。

## <a name="build-a-release-version-of-the-app"></a>アプリのリリース バージョンのビルド

すべてが機能することを確認したら、アプリケーションのリリース ビルドを準備できます。 リリース ビルドでは、デバッグ情報を省略し、コンパイラの最適化オプションを使用してコードをより簡潔かつ迅速に作成します。

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>ソリューション ファイルをクリーンアップし、リリース バージョンをビルドするには

1. メニュー バーで、**[ビルド]、[ソリューションのクリーン]** の順に選択して、前のビルドで作成された中間ファイルと出力ファイルを削除します。

   ![[ビルド] メニューの [ソリューションのクリーン] コマンド](../ide/media/get-started-cpp-clean-solution-menu.png "ExploreIDE-CleanSolution")

1. HelloApp のソリューション構成を **[デバッグ]** から **[リリース]** に変更するには、ツールバーの [ソリューション構成] コントロールでドロップダウンを選択し、**[リリース]** を選択します。

   ![アプリケーションのリリース バージョンのビルド](../ide/media/get-started-cpp-set-release-configuration.png "C++IDE_ChangingBuildtoRelease")

1. ソリューションをビルドします。 メニュー バーで、**[ビルド]、[ソリューションのビルド]** の順にクリックします。

このビルドが完了すると、コマンド プロンプト ウィンドウでコピーおよび実行できるアプリの作成は完了です。 大したことではありませんが、これはより複雑な処理へ通じる入口となります。

このクイック スタートは完了しました。 その他の例については、「[Visual Studio Samples](../ide/visual-studio-samples.md)」を参照してください。

## <a name="see-also"></a>関連項目

[C++ デスクトップ開発のための Visual Studio IDE の使用](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)  
[チュートリアル : Visual C# または Visual Basic による簡単なアプリケーションの作成](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)  
[Visual Studio の生産性に関するヒント](../ide/productivity-tips-for-visual-studio.md)  
[Visual Studio のサンプル](../ide/visual-studio-samples.md)  
[Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md)
