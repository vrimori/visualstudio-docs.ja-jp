---
ms.technology: vs-ai-tools
ms.openlocfilehash: 999e57f9b9b873f44f5a1ef0edac94c7e2b53ac4
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Visual Studio のテンプレートから AI プロジェクトを作成する

[Visual Studio Tools for AI をインストール](installation.md)すれば、さまざまなテンプレートを使って新しい AI プロジェクトを簡単に作成できます。

1. Visual Studio を起動します。

1. **[ファイル]、[新規]、[プロジェクト]** (Ctrl + Shift + N) の順に選択します。 **[新しいプロジェクト]** ダイアログで、"**AI Tools**" を検索し、希望のテンプレートを選択します。 テンプレートを選択すると、テンプレートの簡単な説明が表示されます。

    ![VS2017 Python テンプレートの [新しいプロジェクト] ダイアログ](media\create-project\new-ai-project.png)

1. このクイック スタートでは、"**TensorFlow アプリケーション**" テンプレートを選択し、("MNIST" などの) プロジェクト名を付け、場所を指定し、**[OK]** を選択します。

1. Visual Studio によってプロジェクト ファイル (ディスク上に 1 つの `.pyproj` ファイル) と、テンプレートに記述されているその他のファイルが作成されます。 "TensorFlow アプリケーション" テンプレートでは、プロジェクトと同じ名前の 1 つのファイルがプロジェクトに含まれます。 このファイルは、既定で Visual Studio エディタで開きます。

    ![Python アプリケーション テンプレートを使用した結果のプロジェクト](media\create-project\new-tensorflowapp.png)

1. TensorFlow、numpy、sys、os を含むいくつかのライブラリがコードで既にインポートされていることに注目してください。 また、いくつかの入力変数が指定され準備ができているアプリケーションが開始されています。これにより、入力トレーニング データ、出力モデル、ログ ファイルの場所を簡単に切り替えることができます。 これらのパラメーターは、複数の計算コンテキスト (つまり、Azure ファイル共有とは異なる、ローカル開発ボックスのディレクトリ) にジョブを送信する場合に役立ちます。

1. プロジェクトではいくつかのプロパティも作成されています。コマンドライン引数をこれらの入力パラメーターに自動的に渡すことで、アプリのデバッグが簡単になります。 プロジェクトを**右クリック**してから **[プロパティ]** を選択します。

    ![プロパティ](media\create-project\project-properties.png)

1. **[デバッグ]** タブをクリックして、自動的に追加された [スクリプト引数] を表示します。 必要に応じて、それらを入力データが配置される場所や出力の格納先に変更することができます。

    ![プロパティ](media\create-project\/project-properties_1.png)

1. Ctrl + F5 キーを押すか、メニューを **[デバッグ]、[デバッグなしで開始]** の順に選択して、プログラムを実行します。 結果は、コンソール ウィンドウに表示されます。
