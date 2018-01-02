---
title: "クイックスタート: Visual Studio で Visual Basic を使用してコンソール アプリを作成する | Microsoft Docs"
ms.custom: 
ms.date: 12/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: vb
ms.openlocfilehash: 57441895ccff8bf32b59d6306ca4ae618382d356
ms.sourcegitcommit: 38097344f3ff74ba7b03bcfa45910015ca6bc2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2017
---
# <a name="quickstart-create-a-console-app-in-visual-studio-with-visual-basic"></a>クイックスタート: Visual Studio で Visual Basic を使用してコンソール アプリを作成する
ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、コンソールで実行される簡単な Visual Basic アプリケーションを作成します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する
まず、Visual Basic アプリケーション プロジェクトを作成します。 このプロジェクトの種類には、必要となるすべてのテンプレート ファイルが付属していますので、何も追加する必要はありません。

1. Visual Studio 2017 を開きます。

2. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。

3. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで、**[Visual Basic]** を展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[Console App (.NET Core)]** を選択します。 プロジェクトに *HelloWorld* という名前を付けます。

   ![Visual Studio インストーラーの [.NET Core クロスプラットフォームの開発] ワークロード](../ide/media/new-project-vb-dotnet-helloworld-console-app.png)

     **[Console App (.NET Core)]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。

   ![[新しいプロジェクト] ダイアログ ボックスで [Visual Studio インストーラーを開く] リンクをクリックする](../ide/media/vb-open-visual-studio-installer.png)

     Visual Studio インストーラーが起動します。 **[.NET Core クロスプラットフォームの開発]** ワークロードを選択し、**[変更]** を選択します。

     ![Visual Studio インストーラーの [.NET Core クロスプラットフォームの開発] ワークロード](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>アプリケーションを作成する
Visual Basic プロジェクト テンプレートを選択し、プロジェクトに名前を付けると、簡単な "Hello World" アプリケーションが自動的に作成されます。 [Console.WriteLine(System.String)](https://docs.microsoft.com/en-us/dotnet/api/system.console.writeline?view=netframework-4.7.1#System_Console_WriteLine_System_String) メソッドを呼び出し、リテラル文字列 "Hello World!" を コンソール ウィンドウに表示します。

![テンプレートから既定の Hello World コードを表示する](../ide/media/vb-console-helloworld-template.png)

IDE で **[Hello World]** ボタンをクリックした場合、デバッグ モードでプログラムを実行することができます。

  ![[Hello World] ボタンをクリックして、デバッグ モードでプログラムを実行する](../ide/media/vb-console-hello-world-button.png)

プログラムを実行すると、コンソール ウィンドウが一瞬だけ表示され、すぐに閉じられます。 これは、`Main` メソッドの 1 つのステートメントが実行されると、このメソッドは終了し、その結果、アプリケーションも終了するためです。

### <a name="add-some-code"></a>何らかのコードを追加する
アプリケーションを一時停止し、ユーザーに入力を求めるのためのコードを追加してみましょう。

1. [Console.WriteLine(System.String)](https://docs.microsoft.com/en-us/dotnet/api/system.console.writeline?view=netframework-4.7.1#System_Console_WriteLine_System_String) メソッドへの呼び出しのすぐ後に、次のコードを追加します。

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   これにより、キー入力があるまで、プログラムは一時停止状態となります。

2. メニュー バーで **[ビルド]** > **[ソリューションのビルド]** の順に選択します。

   これにより、プログラムが IL (中間言語) にコンパイルされ、それが JIT (just-in-time) コンパイラによってバイナリ コードに変換されます。

## <a name="run-the-application"></a>アプリケーションの実行
1. ツールバーの **[Hello World]** ボタンをクリックします。

   ![[Hello World] ボタンをクリックして、ツールバーからプログラムを実行する](../ide/media/vb-console-hello-world-button.png)

2. 任意のキーを押して、コンソール ウィンドウを閉じます。

   !["Hello World! Press any key to continue" と表示されているコンソール ウィンドウ](../ide/media/vb-console-hello-world-press-any-key.png)

このクイック スタートは完了しました。 Visual Basic と Visual Studio IDE について少しはご理解いただけたかと思います。 さらに深く理解したい場合は、目次の**チュートリアル** セクションに示されているチュートリアルを続行してください。

## <a name="see-also"></a>関連項目
* [クイックスタート: Visual Studio で Visual Basic を使用して "Hello World" Windows フォーム アプリを作成する](quickstart-visual-basic-winforms.md)
* [Visual Basic IntelliSense について](visual-basic-specific-intellisense.md)
