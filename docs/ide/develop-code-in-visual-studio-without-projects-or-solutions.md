---
title: "プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code, editing
- code editor, syntax coloring
- code editor [Visual Studio]
- brace matching
- code editor, line numbers
- code editor, brace matching
- line numbers
- syntax coloring
- code editor
- code files
- code
ms.assetid: cb53bb9b-5b76-4759-b9b8-7bf32298bcbb
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2d1d3c327101e535c037dba30ed19af3dcf7faaa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する  
Visual Studio 2017 で、ほぼすべての種類のディレクトリ ベースのプロジェクトから、ソリューションまたはプロジェクト ファイルを使用せずに Visual Studio にコードを開くことができます。 これは、たとえば、Git でコード プロジェクトを検索し、それを複製して、直接 Visual Studio に開き、ソリューションまたはプロジェクトを作成することなく開発を開始できることを意味します。  

Visual Studio でコードを編集したり構築したりすることができるだけでなく、コード間を移動したりすることもできます ([移動] コマンドを使用するなど)。 コードは構文が色付けして表示され、通常、基本的なステートメント入力候補およびデバッグが含まれ、ブレークポイントで補完されます。 一部の言語では、追加の機能も用意されています。 詳しくは、「[移植可能なカスタム エディター設定を作成する](create-portable-custom-editor-options.md)」をご覧ください。  

## <a name="open-code-anywhere"></a>どこででもコードを表示  
Visual Studio でコードを開く方法は、次のとおりです。  

- Visual Studio メニュー バーで、**[ファイル]**、**[開く]**、**[フォルダー]** の順に選択し、コードの場所を参照します。  

- コードを含むフォルダーのコンテキスト (右クリック) メニューで、**[Visual Studio で開く]** コマンドを選択します。  

- Visual Studio スタート ページで **[フォルダーを開く]** を選択します。  

- GitHub リポジトリから複製されたコードを開きます。  

### <a name="to-open-code-from-a-cloned-github-repo"></a>複製された GitHub リポジトリからコードを開くには  
次の例は、GitHub リポジトリを複製し、Visual Studio でそのコードを開く方法を示しています。 この手順を実行するには、GitHub アカウントがあり、システム上に Git for Windows がインストールされている必要があります。 詳しくは、「[Signing up for a new GitHub account (GitHub アカウントに登録する)](https://help.github.com/articles/signing-up-for-a-new-github-account/)」および「[Git for Windows](https://git-for-windows.github.io/)」をご覧ください。  

1. GitHub の複製するリポジトリに移動します。  

1. **[複製またはダウンロード]** ボタンをクリックし、ドロップダウン メニューで **[クリップボードにコピー]** ボタンを選択して、GitHub リポジトリのセキュリティをコピーします。  

  ![GitHub の複製ボタン](./media/VSIDE_Code_Clone.png)

    > [!NOTE]
    >  デスクトップでプロジェクトを開くこと、またはプロジェクトの .zip ファイルをダウンロードすることも選択できる場合、この例は、セキュリティで保護された URL メソッドを使用してリポジトリを複製する方法を示します。

1. Visual Studio で、**[チーム エクスプローラー]** タブを選択し、チーム エクスプローラーを開きます。  

1. チーム エクスプローラーの **[ローカル Git リポジトリ]** セクションで **[複製]** コマンドを選択し、GitHub ページの URL をテキスト ボックスに貼り付けます。  

  ![プロジェクトの複製](./media/VSIDE_Code_Clone2.png)

1. **[複製]** ボタンを選択して、プロジェクトのファイルをローカル Git リポジトリに複製します。 リポジトリのサイズによっては、この処理に数分かかることがあります。  

1. リポジトリがシステムに複製されたら、チーム エクスプローラーで、新しく複製されたリポジトリのコンテキスト (右クリック) メニューで **[開く]** コマンドを選択します。  

  ![複製されたリポジトリ](./media/VSIDE_Code_Clone3.png)

1. **[フォルダー ビューの表示]** コマンドを選択して、ソリューション エクスプローラーでファイルを表示します。  

  ![フォルダー ビューの表示](./media/VSIDE_Code_Clone3_show.png)

  複製されたリポジトリでフォルダーとファイルを参照したり、Visual Studio コード エディターでコードを表示/検索したり、構文の色付けなどの機能でコードを補完したりできるようになりました。

    ![複製されたプロジェクト コードの検索](./media/VSIDE_Code_Clone4.png)  

|         |         |
|---------|---------|
|  ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る")  |    Visual Studio の GitHub リポジトリからコードを複製し、開く方法については、[ビデオをご覧ください](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171)。 |

## <a name="debug-your-code"></a>コードをデバッグする  
Visual Studio でプロジェクトまたはソリューションを使用せずにコードをデバッグすることができます。 一部の言語では、コード プロジェクトで有効な "*スタートアップ ファイル*" (スクリプト、実行可能ファイル、プロジェクトなど) の指定が必要になる場合があります。 コードのデバッグ時に、この指定されたコードが Visual Studio によって最初に実行されます。  

ツールバーの [開始] ボタンの横にあるドロップダウン リスト ボックスに、Visual Studio によって検出されたすべてのスタートアップ アイテムと、フォルダーで特別に選択した項目が一覧表示されます。  

![ボタン](./media/VSIDE_Code_Run_Button.png)  

Visual Studio では、プロジェクトは自動的に認識されますが、スクリプト (Python、JavaScript など) はユーザーがスタートアップ アイテムとして明示的に選択して、一覧に表示させる必要があります。 また、MSBuild および CMake などの一部のスタートアップ アイテムは複数のビルド構成を持つことができます。これらは、実行ボタンのドロップダウン リストに表示されます。  

Visual Studio では現在、次の言語のデバッグがサポートされています。  

- Node.js  

- Python  

- MSBuild ベースのプロジェクト (C#、VB、C++)  

- PDB (Python デバッガー) ファイルを使用した実行可能ファイル  

### <a name="to-debug-nodejs-and-python"></a>Node.js および Python をデバッグするには:  
1. Node.js 、Python Tools、または Visual Studio 2017 と、Node.js ランタイムをインストールします。  

1. ソリューション エクスプローラーで、JavaScript ファイルのコンテキスト メニューで、**[スタートアップ アイテムとして設定]** コマンドを選択します。  

1. **F5** キーを押して、デバッグを開始します。  

### <a name="to-debug-msbuild-projects"></a>MSBuild プロジェクトをデバッグするには  
1. Visual Studio メニューで、**[デバッグ]** を選択します。 ドロップダウン メニューでプロジェクトを選択するか、ソリューション エクスプローラーでスタートアップ アイテムとして表示するプロジェクトまたはファイルを選択します。  

1. **F5** キーを押して、デバッグを開始します。  

### <a name="to-debug-executable-files"></a>実行可能ファイルをデバッグするには  
1. Visual Studio メニューで、**[デバッグ]** を選択します。 ドロップダウン メニューでプロジェクトを選択するか、ソリューション エクスプローラーでスタートアップ アイテムとして表示するプロジェクトまたはファイルを選択します。  

1. **F5** キーを押して、デバッグを開始します。  

## <a name="enable-custom-build-tools"></a>カスタム ビルド ツールの有効化
Visual Studio は多くのさまざまな言語を実行する方法を認識していますが、すべてを認識しているわけではありません。 Visual Studio がお使いの言語を実行する方法を認識している場合、コードを直ちに実行できます。 コードを実行しようとして Visual Studio がその実行方法を認識していない場合、情報バーによりメッセージが表示され、スタートアップ アイテムとして機能させるため、コードベースにファイルを指定するように求められます。  

コードベースで、Visual Studio が認識していないカスタム ビルド ツールを使用する場合、いくつかの追加の手順を完了するまで、Visual Studio でコードを実行およびデバッグできない可能性があります。 コンパイラなど、有効な実行可能ファイルの種類と、その言語に必要なカスタム パイプラインと引数を指定する必要があります。 これを可能にするために、Visual Studio には*ビルド タスク*が用意されています。 ビルド タスクを作成して、そのコードをビルドおよび実行するために言語で必要なすべての項目を指定することができます。  

必要な操作をほぼすべて実行できる任意のビルド タスクを作成することもできます。 たとえば、フォルダーの内容を一覧表示したり、ファイルの名前を変更するタスクを作成することができます。 または、特定の引数を使用して、プロジェクトのコンパイルやビルドなどの操作を実行する、より対象を絞ったカスタム ビルド タスクを作成することもできます。 次の手順は、両方の種類のビルド タスクを作成する方法を示しています。  

#### <a name="to-create-an-arbitrary-build-task"></a>任意のビルド タスクを作成するには  
1. タスクを必要とするソリューション エクスプローラーで、プロジェクトのファイルまたはフォルダーを選択し、ファイルまたはフォルダーのコンテキスト (右クリック) メニューで **[タスクの構成]** を選択します。  

  ![タスクの構成](./media/VSIDE_Code_Config_Task.png)

  **[タスクの構成]** を選択すると、tasks.vs.json というファイルが開きます。 このファイルが存在しない場合、自動的に作成されます。 このファイルには、選択したファイルまたはフォルダーのビルド タスクが含まれています。  

  ![tasks.vs.json ファイル](./media/VSIDE_Code_Tasks_JSON.png)

1. 次のビルド タスクを tasks.vs.json に追加します。 この例では、出力ウィンドウに選択したフォルダーのファイルおよびサブフォルダーを一覧表示する "List outputs" というシンプルなタスクを追加します。 (新しいタスクは、既存の "タスク" 配列内に追加されます。)  

  ```xml
      {
        "taskName": "List outputs",
        "appliesTo": "*",
        "type": "command",
        "command": "${env.COMSPEC}",
        "args": [
          "dir ${outDir}"
        ]
      },
  ```
  完全なビルド タスクは、次のようになります。  

  ![任意のビルド タスク](./media/VSIDE_Code_Tasks_ArbTask.png)

1. プロジェクトを保存します。  

1. 選択したフォルダーのコンテキスト メニューを開きます。 コンテキスト メニューの下部に新しい任意のビルド タスクが表示されます。  

  ![任意のビルド タスクのコマンド](./media/VSIDE_Code_Tasks_ArbTask2.png)

1. 新しい **List outputs** コマンドを選択して、タスクを実行します。  

### <a name="to-create-a-custom-build-task"></a>カスタム ビルド タスクを作成するには
この手順では、nMake を使用してコードをビルドおよびクリーンする 2 つのカスタム ビルド タスクを追加します。  

1. ソリューション エクスプローラーで、スタートアップ アイテムとして後で指定するプロジェクトのファイルを選択します。 ファイルのコンテキスト (右クリック) メニューで、**[タスクの構成]** を選択します。  

  ![カスタム ビルド タスクのコマンド](./media/VSIDE_Code_Tasks_CustTask1.png)

1. 次のビルド タスクを tasks.vs.json に追加します。 この例では、2 つのタスクを追加します。1 つは nMake コマンドを使用してプロジェクトをビルドする "makefile-build" と呼ばれるもので、もう 1 つは "clean" 引数により nMake コマンドを呼び出す makefile-clean と呼ばれるものです。 (これらのタスクは、既存の "タスク" 配列内に追加されます。) (これは、ビルド タスクのほんの一例です。 これらを実際に機能させるには、システムにインストールされた [nNake](https://docs.microsoft.com/en-us/cpp/build/nmake-reference) を含むワークロードが必要です。)  

  ```xml
  {
  "taskName": "makefile-build",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "build",
  "command": "nmake"
  },
  {
  "taskName": "makefile-clean",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "clean",
  "command": "nmake",
  "args": [
    "clean"
    ]
  },
  ```
  完全なカスタム ビルド タスクは、次のようになります。  

  ![カスタム ビルド タスク](./media/VSIDE_Code_Tasks_CustTask2.png)

1. プロジェクトを保存します。  

1. 選択したファイルのコンテキスト メニューを開きます。 新しいカスタム ビルド タスクが、コンテキスト メニューの中ほどに表示されます。  

  ![カスタム ビルド タスクのコマンド](./media/VSIDE_Code_Tasks_CustTask3.png)

  > [!NOTE]
  > コマンドが、`contextType` 設定により **[タスクの構成]** コマンドの下に表示されます。"build" および "clean" はビルド コマンドであるため、コンテキスト メニューの中央のビルド セクションに表示されます。  

  カスタム ビルド コマンドをファイルと関連付けたので、これで、ファイルをスタートアップ アイテムとして指定できます。  

1. ファイルのコンテキスト メニューで、**[スタートアップ アイテムとして設定]** を選択します。  

  ![カスタム ビルド タスクのコマンド](./media/VSIDE_Code_Tasks_CustTask4.png)

1. ツールバーで、[開始] ボタンの横にあるドロップダウン矢印を選択します。 スタートアップ アイテムがオプションとして表示されます。  

  ![カスタム ビルド タスクのコマンド](./media/VSIDE_Code_Tasks_CustTask5.png)

これで、**[開始]** ボタンまたは **F5** キーを押して、コードベースを実行できるようになりました。 Visual Studio でコードベースのビルド ツールが認識されない場合でも、Visual Studio でコードベースを編集およびデバッグすることができます。 ビルド タスクの出力は**出力**ウィンドウに表示され、ビルド エラーは**エラー一覧**に表示されます。 tasks.vs.json ビルド タスク ファイルは、Visual Studio の内部開発ループを、コードベースによって使用されるカスタム ビルド ツールに組み込みます。  

カスタム ビルド タスクは、個々のファイル、または特定の種類のすべてのファイルに追加できます。 たとえば、NuGet パッケージ ファイルを "パッケージの復元" タスクを含むように構成するか、すべてのソース ファイルをスタティック分析タスク (すべての .js ファイルのリンターなど) を含むように構成することができます。  

Visual Studio では、tasks.vs.json のルートで VSCode `$variable` 代入や、環境設定 (`$env.var` など) またはキーがサポートされています。  

## <a name="specify-build-output"></a>ビルド出力の指定  
プロジェクトをコンパイルする必要がある場合に `output` という追加のタグを tasks.vs.json ファイルに追加できます。 次に例を示します。  

`"output": "${workspaceRoot}\\bin\\hellomake.exe"`

出力場所を指定すると、Visual Studio にプロジェクトのビルド出力の検索場所が通知されます。  

## <a name="tasksvsjson-file-location"></a>tasks.vs.json ファイルの場所  
既定では、tasks.vs.json ファイルは、`.vs` という非表示フォルダーに配置されます。 Visual Studio で非表示ファイルを表示するには、ソリューション エクスプローラーのツールバーで **[すべてのファイルを表示]** ボタンを選択します。  

![任意のビルド タスクのコマンド](./media/VSIDE_Code_Tasks_FileLocation.png)

tasks.vs.json ファイルは、通常、ほとんどのユーザーがこれをソース管理にチェックインする必要がないため、非表示になっています。 ただし、これをソース管理にチェックインできるようにしたい場合は、表示されるプロジェクトのルートにファイルをドラッグします。  

他の .json ファイルが .vs フォルダーに存在する場合がありますが、移動する必要があるファイルは tasks.vs.json ファイルと launch.vs.json ファイル (ある場合) のみです。 launch.vs.json ファイルでは Visual Studio デバッガーが構成され、tasks.vs.json ファイルでは Visual Studio でビルドが構成されます。  

## <a name="see-also"></a>関連項目
[コード エディターとテキスト エディターでのコードの作成](../ide/writing-code-in-the-code-and-text-editor.md)
