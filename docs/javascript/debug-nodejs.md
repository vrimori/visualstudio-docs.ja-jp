---
title: JavaScript または TypeScript のアプリをデバッグする
description: Visual Studio では、Visual Studio での JavaScript アプリと TypeScript アプリのデバッグをサポートします
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 29b58d588a07be8ba25ab844da171222c57df545
ms.sourcegitcommit: 8bfabab73b39b3b3e68a3e8dc225515e8b310fed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2019
ms.locfileid: "54398235"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Visual Studio で JavaScript アプリまたは TypeScript アプリをデバッグする

Visual Studio を使用して、JavaScript および TypeScript のコードをデバッグすることができます。 ブレークポイントを設定してそこにヒットし、変数を検査し、呼び出し履歴を表示し、その他のデバッグ機能を使用することができます。

> [!TIP]
> Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。 実行するアプリ開発の種類によっては、Visual Studio と共に **Node.js ワークロード**をインストールする必要がある場合があります。

## <a name="debug-server-side-script"></a>サーバー側のスクリプトをデバッグする

1. Visual Studio でプロジェクトを開いた状態で、サーバー側の JavaScript ファイル (*server.js* など) を開き、左の余白をクリックしてブレークポイントを設定します。

    ![ブレークポイントの設定](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    ブレークポイントは、信頼できるデバッグの最も基本的で重要な機能です。 ブレークポイントは、Visual Studio が実行コードを中断する場所を示します。これにより、変数の値またはメモリの動作を確認したり、コードの分岐が実行されるかどうかを確認したりすることができます。

1. アプリを実行するには、**F5** キーを押します (**[デバッグ]** > **[デバッグの開始]**)。

    設定したブレークポイントでデバッガーが一時停止します (現在のステートメントは黄色でマークされます)。 ここで、**[ローカル]** ウィンドウや **[ウォッチ]** ウィンドウなどのデバッガー ウィンドウを使って、現在スコープ内にある変数をマウスでポイントすることにより、アプリの状態を調べることができます。

1. アプリを続行するには **F5** キーを押します。

1. Chrome の開発者ツールまたは F12 ツールを使う場合は、**F12** キーを押します。 これらのツールでは、DOM を調べたり、JavaScript コンソールを使ってアプリを操作したりできます。

## <a name="debug-client-side-script"></a>クライアント側のスクリプトをデバッグする

Visual Studio では、Chrome および Internet Explorer のみのデバッグ サポートが提供されます。 一部のシナリオでは、デバッガーで自動的に、HTML ファイルの埋め込みスクリプトおよび JavaScript や TypeScript コードのブレークポイントにヒットします。

TypeScript や Babel などのトランスパイラによってソースが縮小または作成されている場合、最適なデバッグ エクスペリエンスを得るために、[ソース マップ](#generate_sourcemaps)を使用する必要があります。 ソース マップを使用しなくても、実行中のクライアント側スクリプトにデバッガーをアタッチすることはできます。 しかし、ブレークポイントの設定やヒットが可能なのは、元のソース ファイルではなく、縮小またはトランスパイルされたファイルでのみとなります。 たとえば、Vue.js アプリでは、縮小されたスクリプトは文字列として `eval` ステートメントに渡されます。ソース マップを使用しない限り、Visual Studio デバッガーを効果的に使って、このコードをステップ実行する方法はありません。 いくつかの複雑なデバッグ シナリオでは、Chrome の開発者ツールまたは Microsoft Edge の F12 ツールを使用する場合もあります。

Visual Studio からデバッガーをアタッチし、クライアント側のコードのブレークポイントにヒットするには、通常、デバッガーで正しいプロセスを識別できるようにサポートする必要があります。 ここではその方法の 1 つとして、Chrome を使用します。

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Chrome を使用してクライアント側スクリプトにデバッガーをアタッチする

1. Chrome のすべてのウィンドウを閉じます。

    デバッグ モードで Chrome を実行する前に、この操作を実行する必要があります。

2. Windows の **[スタート]** ボタンから **[ファイル名を指定して実行]** コマンドを開き (右クリックして **[ファイル名を指定して実行]** を選択)、次のコマンドを入力します。

    `chrome.exe --remote-debugging-port=9222`

    このコマンドにより、デバッグが有効な状態で Chrome が起動します。

3. Visual Studio に切り替え、ソース コードにブレークポイントを設定します  (`return` ステートメントや `var` 宣言など、ブレークポイントを許可するコード行でブレークポイントを設定します)。

    ![ブレークポイントの設定](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    生成された大きなファイルで特定のコードを見つける必要がある場合は、**Ctrl** + **F** キー (**[編集]** > **[検索と置換]** > **[クイック検索]**) を使用します。

4. Visual Studio でデバッグ ターゲットとして Chrome を選択し、**Ctrl**+**F5** キーを押して (**[デバッグ]** > **[デバッグなしで開始]**)、ブラウザーでアプリを実行します。

    アプリがブラウザーの新しいタブで開きます。

    Chrome をコンピューターで使用できるのにオプションには表示されない場合は、デバッグ ターゲットのドロップダウン リストから **[Browse With]\(ブラウザー\)** を選択し、Chrome を既定のブラウザーに選択します (**[Set as Default]\(既定値として設定\)** を選択)。

5. **[デバッグ]** > **[プロセスにアタッチ]** の順に選びます。

6. **[プロセスにアタッチ]** ダイアログ ボックスの **[アタッチ先]** フィールドで **[WebKit code]\(WebKit コード\)** を選び、フィルター ボックスに「**chrome**」と入力して検索結果をフィルター処理します。

    **WebKit コード**は、WebKit ベースのブラウザーである、Chrome に必要な値です。

7. 正しいホスト ポート (この図では 1337) の Chrome プロセスを選び、**[アタッチ]** を選択します。

    ![プロセスにアタッチする](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Visual Studio で DOM Explorer と JavaScript コンソールが開けば、デバッガーが正しくアタッチしたことがわかります。 これらのデバッグ ツールは、Chrome の開発者ツールや Microsoft Edge の F12 ツールに似ています。

    > [!NOTE]
    > デバッガーがアタッチされず、「プロセスにアタッチできません。 現在の状態での操作は無効です" というメッセージが表示される場合、Chrome をデバッグ モードで開始する前に、タスク マネージャーを使用して Chrome のすべてのインスタンスを閉じます。 Chrome の拡張機能が実行され、フル デバッグ モードが阻止されている場合があります。

8. ブレークポイントを設定したコードを既に実行している場合は、ブラウザーのページを更新してブレークポイントにヒットします。

    デバッガーで一時停止している間に、変数をマウスでポイントし、デバッガー ウィンドウを使って、アプリの状態を確認できます。 コードをステップ実行することにより (**F5**、**F10**、**F11**)、デバッガーを進めることができます。

    縮小またはトランスパイルされた JavaScript では、ご利用の環境やブラウザーの状態に応じて、(ソース マップを使用して) TypeScript ファイルでトランスパイルされた JavaScript またはそのマップされた場所でブレークポイントにヒットする場合があります。 どちらの場合も、コードをステップ実行して、変数を確認できます

    * TypeScript ファイルのコードを中断する必要があるときにできない場合は、前の手順で説明したデバッガーをアタッチするための **[プロセスにアタッチ]** を使用します。 次に、ソリューション エクスプローラーで **[スクリプト ドキュメント]** > **[filename.tsx]** の順に開き、動的に生成された TypeScript ファイルを開いて、ブレークポイントを設定し、ブラウザーでページを更新します (`return` ステートメントや `var` 宣言など、ブレークポイントを許可するコード行にブレークポイントを設定します)。

        または、TypeScript ファイル内のコードで中断する必要があるときにできない場合は、TypeScript ファイルで `debugger;` ステートメントを使うか、代わりに Chrome の開発者ツールでブレークポイントを設定してみてください。

    * トランスパイルされた JavaScript ファイル (*app-bundle.js* など) 内のコードで中断する必要があるときにできない場合は、ソース マップ ファイルである *filename.js.map* を削除します。

     > [!TIP]
     > 以上の手順に従って初めてプロセスにアタッチした後は、Visual Studio 2017 で **[デバッグ]** > **[プロセスに再アタッチする]** を選ぶことで、同じプロセスにすぐに再アタッチできます。

## <a name="generate_sourcemaps"></a> デバッグ用のソース マップを生成する

Visual Studio には、JavaScript ソース ファイルでソース マップを使用して生成する機能があります。 これは多くの場合、ソースが TypeScript や Babel のようなトランスパイラによって縮小または作成されている場合に必要です。 使用できるオプションはプロジェクトの種類によって異なります。

* Visual Studio の TypeScript プロジェクトでは、既定でソース マップが生成されます。

* JavaScript プロジェクトでは、webpack などのバンドラー、およびプロジェクトに追加できる、TypeScript コンパイラ (または Babel) などのコンパイラを使用して、ソース マップを生成する必要があります。 TypeScript コンパイラの場合は、*tsconfig.json* ファイルを追加する必要もあります。 基本的な webpack 構成を使用してこれを行う方法を示す例については、[React を使用した Node.js アプリの作成](../javascript/tutorial-nodejs-with-react-and-jsx.md)に関するページを参照してください。

> [!NOTE]
> ソース マップを初めて使用する場合は、続行する前に「[Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/)」 (JavaScript ソース マップの概要) をお読みください。

ソース マップの詳細設定を構成するには、*tsconfig.json* と、TypeScript プロジェクトのプロジェクト設定の両方ではなく、いずれかを使用します。

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>tsconfig.json ファイルを使用してソース マップを構成する

*tsconfig.json* ファイルをプロジェクトに追加する場合、Visual Studio ではディレクトリ ルートが TypeScript プロジェクトとして扱われます。 ファイルを追加するには、ソリューション エクスプローラーでプロジェクトを右クリックし、**[追加]、[新しい項目]、[Web]、[スクリプト]、[TypeScript JSON 構成ファイル]** の順に選択します。 *tsconfig.json* ファイルは、次のようにプロジェクトに追加されます。

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>tsconfig.json のコンパイラ オプション

* **inlineSourceMap**:ソース ファイルごとに別のソース マップを作成するのではなく、ソース マップを含む 1 つのファイルを出力します。
* **inlineSources**:1 つのファイル内のソース マップと共にソースを出力します。*inlineSourceMap* または *sourceMap* を設定する必要があります。
* **mapRoot**:既定の場所ではなく、デバッガーでソース マップ (*.map*) ファイルを検索する必要がある場所を指定します。 実行時の *.map* ファイルを、*.js* ファイルとは異なる場所に配置する必要がある場合は、このフラグを使用します。 指定された場所は、*.map* ファイルの場所にデバッガーを移動するために、ソース マップに埋め込まれます。
* **sourceMap**:対応する *.map* ファイルを生成します。
* **sourceRoot**:ソースの場所ではなく、デバッガーで TypeScript ファイルを検索する必要がある場所を指定します。 実行時のソースを、設計時の場所とは異なる場所に配置する必要がある場合は、このフラグを使用します。 指定された場所は、ソース ファイルが配置されている場所にデバッガーを移動するために、ソース マップに埋め込まれます。

コンパイラ オプションの詳細については、TypeScript ハンドブックの「[Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)」 (コンパイラ オプション) ページを確認してください。

### <a name="configure-source-maps-using-project-settings"></a>プロジェクト設定を使用してソース マップを構成する

プロジェクトを右クリックし、**[プロジェクト]、[プロパティ]、[TypeScript ビルド]、[デバッグ]** の順に選択することで、プロジェクト プロパティを使用してソース マップ設定を構成することもできます。

以下のプロジェクト設定を使用できます。

* **ソース マップを生成する** (*tsconfig.json* の **sourceMap** と同等):対応する *.map* ファイルを生成します。
* **ソース マップのルート ディレクトリを指定する** (*tsconfig.json* の **mapRoot** と同等):生成された場所ではなく、デバッガーでマップ ファイルを検索する必要がある場所を指定します。 実行時の *.map* ファイルを、.js ファイルとは異なる場所に配置する必要がある場合は、このフラグを使用します。 指定された場所は、マップ ファイルが配置されている場所にデバッガーを移動するために、ソース マップに埋め込まれます。
* **TypeScript ファイルのルート ディレクトリを指定する** (*tsconfig.json* の **sourceRoot** と同等):ソースの場所ではなく、デバッガーで TypeScript ファイルを検索する必要がある場所を指定します。 実行時のソース ファイルを、設計時の場所とは異なる場所に配置する必要がある場合は、このフラグを使用します。 指定された場所は、ソース ファイルが配置されている場所にデバッガーを移動するために、ソース マップに埋め込まれます。

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Razor (ASP.NET) を使用して動的ファイルで JavaScript をデバッグする

Visual Studio では、Chrome および Internet Explorer のみのデバッグ サポートが提供されます。 ブレークポイントは自動的に、HTML ファイルの JavaScript/TypeScript および埋め込みスクリプトにアタッチされます。

動的に生成されたファイルのデバッグは自動ではありません。 Razor 構文 (cshtml、vbhtml) で生成されたファイルのブレークポイントに自動的にヒットすることはできません。 この種のファイルのデバッグに使用できる方法は、次の 2 つです。

* **中断する場所に `debugger;` ステートメントを配置する**:これにより、動的スクリプトで実行が停止され、作成中にすぐにデバッグが開始されます。
* **Visual Studio でページを読み込み、動的なドキュメントを開く**:デバッグ中に動的ファイルを開き、ブレークポイントを設定し、この方法が機能するようにページを更新する必要があります。 Chrome と Internet Explorer のどちらを使用するかに応じて、次の方法のいずれかを使ってファイルを見つけます。

   Chrome の場合は、**[ソリューション エクスプローラー]、[スクリプト ドキュメント]、[YourPageName]** の順に移動します。

    > [!NOTE]
    > Chrome を使用する場合は、"`no source is available between `<script>` tags.` This is OK, just continue debugging.

   Internet Explorer の場合は、**[ソリューション エクスプローラー]、[スクリプト ドキュメント]、[Windows Internet Explorer]、[YourPageName]** の順に移動します。

詳細については、「[Client-side debugging of ASP.NET projects in Google Chrome](https://blogs.msdn.microsoft.com/webdev/2016/11/21/client-side-debugging-of-asp-net-projects-in-google-chrome/)」 (Google Chrome での ASP.NET プロジェクトのクライアント側デバッグ) をご覧ください。
