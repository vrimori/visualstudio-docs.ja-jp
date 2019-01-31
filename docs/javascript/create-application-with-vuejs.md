---
title: Node.js を使用して Vue.js アプリを作成する
description: Visual Studio で Vue.js フレームワークを使用して Node.js アプリケーションを作成することができます
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a4b912f523be0380858d639dbf43a4c53bc358c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947024"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Node.js Tools for Visual Studio を使用して Vue.js アプリケーションを作成する

Visual Studio 2017 には [Vue.js](https://vuejs.org/) フレームワークの強化されたサポートが含まれており、Vue.js、JavaScript、TypeScript でアプリケーションを作成するときの開発エクスペリエンスが向上します。

次の新機能は、Visual Studio での Vue.js アプリケーションの開発をサポートします。

* *.vue* ファイルの Script、Style、Template ブロックのサポート
* *.vue* ファイルでの `lang` 属性の認識
* Vue.js プロジェクトとファイル テンプレート

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio 2017 バージョン 15.8 Preview 3 以降と **Node.js 開発ワークロード**がインストールされている必要があります。

    > [!IMPORTANT]
    > この記事では、Visual Studio 2017 バージョン 15.8 Preview 3 以降でのみ使用できる機能が必要です。

    Visual Studio をまだインストールしていない場合は、 [Visual Studio のダウンロード](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  ページに移動し、無料試用版をインストールしてください。

    ワークロードをインストールする必要があるが、既に Visual Studio を所有している場合は、(**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択し) **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

* ASP.NET Core プロジェクトを作成するには、ASP.NET と、Web 開発ワークロードおよび .NET Core クロスプラットフォーム開発ワークロードがインストールされている必要があります。

* Node.js ランタイムをインストールしている必要があります。

    インストールされていない場合は、LTS バージョンを [Node.js](https://nodejs.org/en/download/) Web サイトからインストールしてください。 一般に、Visual Studio はインストール済みの Node.js ランタイムを自動的に検出します。 インストール済みのランタイムが検出されない場合は、プロパティ ページでインストール済みのランタイムを参照するようにプロジェクトを構成できます。 (プロジェクトを作成した後、プロジェクト ノードを右クリックして **[プロパティ]** を選択します)。

## <a name="create-a-vuejs-project-using-a-template"></a>テンプレートを使用して Vue.js プロジェクトを作成する

新しい Vue.js テンプレートを使用して新しいプロジェクトを作成できます。 テンプレートを使うのが開始する最も簡単な方法です。 詳細については、「[Use Visual Studio to create your first Vue.js app](../javascript/quickstart-vuejs-with-nodejs.md)」(Visual Studio を使用して初めての Vue.js アプリを作成する) をご覧ください。

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>ASP.NET Core と Vue CLI を使用して Vue.js プロジェクトを作成する

Vue.js では、迅速にスキャフォールディングするプロジェクトの正式な CLI が提供されています。 CLI を使用してアプリケーションを作成する場合は、この記事の手順に従って開発環境を設定します。

> [!IMPORTANT]
> 以下の手順では、Vue.js フレームワークについてある程度の経験があるものとします。 ない場合は、[Vue.js](https://vuejs.org/) にアクセスしてフレームワークの詳細を学習してください。

### <a name="create-a-new-aspnet-core-project"></a>新しい ASP.NET Core プロジェクトを作成する

この例では、空の ASP.NET Core アプリケーション (C#) を使用します。 ただし、さまざまなプロジェクトやプログラミング言語から選択することができます。

#### <a name="create-an-empty-project"></a>空のプロジェクトを作成する

1. Visual Studio を開き、メイン メニューから **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

1. **[Visual C#]** > **[Web]** で **ASP.NET Core Web アプリケーション**を選択して、**[OK]** をクリックします。

    **ASP.NET Core Web アプリケーション** プロジェクト テンプレートが表示されない場合は、**ASP.NET と Web 開発**ワークロードと **.NET Core 開発**ワークロードを最初にインストールする必要があります。 ワークロードをインストールするには、**[新しいプロジェクト]** ダイアログ ボックス (**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択) の左側のウィンドウで **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 必要なワークロードを選択します。

1. **[空]** を選択して、**[OK]** をクリックします。

    Visual Studio によってプロジェクトが作成され、ソリューション エクスプローラー (右側のウィンドウ) で開かれます。

#### <a name="configure-the-project-startup-file"></a>プロジェクトのスタートアップ ファイルを構成する

* *./Startup.cs* ファイルを開き、Configure メソッドに次の行を追加します。

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Vue CLI をインストールする

vue-cli npm モジュールをインストールするには、コマンド プロンプトを開き、「`npm install --g vue-cli`」または「`npm install -g @vue/cli`」 (現在ベータ版のバージョン 3.0 の場合) と入力します。

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Vue CLI を使用して新しいクライアント アプリケーションをスキャフォールディングする

1. コマンド プロンプトに移動し、現在のディレクトリをお使いのプロジェクト ルート フォルダーに変更します。

1. 「`vue init webpack ClientApp`」と入力し、追加の質問に回答するように求められたら手順に従います。

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>ビルドされたファイルを wwwroot に出力するように webpack の構成を変更する

* *./ClientApp/config/index.js* ファイルを開き、`build.index` および `build.assetsRoot` を wwwroot のパスに変更します。

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a>ビルドがトリガーされるたびに ClientApp をビルドするようにプロジェクトを設定する

1. Visual Studio で **[プロジェクト]** > **[プロパティ]** > **[ビルド イベント]** に移動します。

1. **[ビルド前に実行するコマンド ライン]** に「`npm --prefix ./ClientApp run build`」と入力します。

#### <a name="configure-webpacks-output-module-names"></a>webpack の出力モジュール名を構成する

* *./ClientApp/build/webpack.base.conf.js* ファイルを開き、出力のプロパティに次のプロパティを追加します。

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Vue CLI で TypeScript のサポートを追加する

次の手順では、現在ベータ版である vue-cli 3.0 が必要です。

1. コマンド プロンプトに移動し、現在のディレクトリをプロジェクト ルート フォルダーに変更します。

1. 「`vue create ClientApp`」と入力し、**[Manually select features]\(手動で機能を選択する\)** を選択します。

1. **[TypeScript]** を選択し、他の必要なオプションを選択します。

1. 残りの手順に従って、質問に応答します。

#### <a name="configure-a-vuejs-project-for-typescript"></a>TypeScript の Vue.js プロジェクトを構成する

1. *./ClientApp/tsconfig.json* ファイルを開き、コンパイラ オプションに `noEmit:true` を追加します。

    このオプションを設定すると、Visual Studio でプロジェクトをビルドするたびにプロジェクトが繁雑にならなくなります。

1. 次に、*./ClientApp/* に *vue.config.js* ファイルを作成し、次のコードを追加します。

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    上記のコードは、webpack を構成して、wwwroot フォルダーを設定します。

#### <a name="build-with-vue-cli-30"></a>vue-cli 3.0 でビルドする

vue-cli 3.0 の原因がわからない問題のため、ビルド プロセスを自動化できません。 wwwroot フォルダーを更新するたびに、ClientApp フォルダーで `npm run build` コマンドを実行する必要があります。

## <a name="limitations"></a>制限事項

* `lang` 属性は、JavaScript および TypeScript 言語のみをサポートします。 受け付けられる値は、js、jsx、ts、tsx です。
* `lang` 属性は、template または style タグでは動作しません。
* *.vue* ファイル内の script ブロックのデバッグは、その前処理される性質によりサポートされていません。
* TypeScript は *.vue* ファイルをモジュールとして認識しません。 *.vue* ファイルがどのようなものかを TypeScript に伝えるには、次のようなコードを含むファイルが必要です (vue-cli 3.0 のテンプレートにはこのファイルが既に含まれます)。

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* vue-cli 3.0 を使用しているときは、プロジェクト プロパティでのビルド前イベントとしての `npm run build` コマンドの実行は動作しません。

## <a name="see-also"></a>関連項目

- https://vuejs.org/v2/guide - Vue の概要ガイド。
- https://github.com/vuejs/vue-cli - Vue CLI プロジェクト。
- https://webpack.js.org/configuration/ - webpack 構成ドキュメント。