---
title: "サーバー プロトコルの言語拡張機能を追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5124547737405af8309161df90356f607909c0fa
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="adding-a-language-server-protocol-extension"></a>サーバー プロトコルの言語拡張機能を追加します。

言語サーバー プロトコル (LSP) は、言語のさまざまなコード エディターにサービスの機能を提供するために使用の JSON RPC v2.0 の形式での一般的なプロトコルです。 プロトコルを使用して、すべての参照、LSP をサポートするさまざまなコード エディターになどを検索して、IntelliSense、エラーの診断などのサービス機能の言語を提供するサーバーを 1 つの言語を記述できます。 Visual Studio での言語サービスを追加して、いずれかで従来、TextMate 文法ファイルを使用した、または Visual Studio 機能拡張 Api の完全なセットを使用してカスタム言語サービスを記述して構文を強調表示などの基本的な機能を提供するには多くのデータを提供します。 LSP 3 番目のオプションを提供するようになりましたが、サポートします。

![Visual Studio での言語のサーバー プロトコル サービス](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>言語のサーバー プロトコル

詳細については、プロトコル自体に、ドキュメントを参照して[ここ](https://github.com/Microsoft/language-server-protocol)です。 言語のサーバー プロトコルの visual Studio の実装は、プレビュー段階とサポートは、実験的な考慮する必要があります。 このプレビュー リリースは、拡張機能の形式で ([言語サーバー プロトコル クライアント プレビュー](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview))、**この拡張機能をインストールできるのみで、プレビュー チャネルの Visual Studio ですが**です。 Visual Studio の今後のリリースでは、プレビュー フラグの削除時に、言語のサーバー プロトコルの組み込みサポートが含まれます。 **運用環境ではプレビューを使用する必要があります。**

作成する方法の詳細については、サンプルの言語のサーバーまたは Visual Studio のコードに言語の既存のサーバーを統合する方法ドキュメントを参照して、[ここ](https://code.visualstudio.com/docs/extensions/example-language-server)です。

![言語のサーバー プロトコルの実装](media/lsp-implementation.png)

この記事では、LSP ベースの言語を使用している Visual Studio 拡張機能を作成する方法について説明します。 これには、既に LSP ベース言語サーバーを開発しているし、Visual Studio に統合することが前提とします。

Visual Studio 内でのサポートについては、言語のサーバーは、次のメカニズムを使用してクライアント (Visual Studio) と通信できます。

* 標準入力/出力ストリーム
* 名前付きパイプ
* ソケット

LSP と Visual Studio でのサポートの目的は、Visual Studio 製品の一部ではないオンボード言語サービスです。 (C# のような) Visual Studio での既存の言語サービスに拡張することはありません。 既存の言語を拡張するには、言語サービスの機能拡張のガイドを参照してください (たとえば、 ["Roslyn".NET コンパイラ プラットフォーム](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md))。

## <a name="language-server-protocol-features-supported"></a>サポートされている言語サーバー プロトコルの機能

次の LSP 機能がこれまでの Visual Studio でサポートされます。

メッセージ | Visual Studio でサポートしています。
--- | ---
初期化します。 | 可
初期化済み | 可
シャットダウン | 可
exit | 可
$/cancelRequest | 可
window/showMessage | 可
window/showMessageRequest | 可
window/logMessage | 可
製品利用統計情報とイベント |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | 可
workspace/didChangeWatchedFiles | 可
workspace/symbol | 可
workspace/executeCommand | 可
workspace/applyEdit | 可
textDocument/publishDiagnostics | 可
textDocument/didOpen | 可
textDocument/didChange | 可
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | 可
textDocument/didClose | 可
textDocument/completion | 可
入力候補および resolve | 可
textDocument/hover | 可
textDocument/signatureHelp | 可
textDocument/references | 可
textDocument/documentHighlight |
textDocument/documentSymbol | 可
textDocument/書式設定 | 可
textDocument/rangeFormatting | 可
textDocument/onTypeFormatting |
textDocument/definition | 可
textDocument/codeAction | 可
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | 可

## <a name="getting-started"></a>作業の開始

### <a name="create-a-vsix-project"></a>VSIX プロジェクトを作成します。

LSP ベース言語サーバーを使用する言語サービスの拡張機能を作成するには、最初に確認がある、 **Visual Studio 拡張機能開発**ワークロードが VS のインスタンス用にインストールします。

次に移動して、新しい空白 VSIXProject を作成**ファイル** > **新しいプロジェクト** > **Visual c#**  >  **機能拡張** > **VSIX プロジェクト**:

![vsix プロジェクトを作成します。](media/lsp-vsix-project.png)

プレビュー リリースでは、LSP の VS サポートは、VSIX の形式になります ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview))。 LSP 言語サーバーを使用して拡張機能を作成する拡張機能の開発者は、この VSIX に依存関係を受け取る必要があります。 そのため、お客様をサーバーの言語拡張機能をインストールする**言語サーバー プロトコル クライアント プレビュー VSIX 最初にインストールする必要があります。**

VSIX の依存関係を定義する (ダブルクリックして、プロジェクトの source.extension.vsixmanifest ファイル)、VSIX の VSIX マニフェスト デザイナーを開きに移動**の依存関係**:

![言語のサーバー プロトコルのクライアントへの参照を追加します。](media/lsp-reference-lsp-dependency.png)

次のように新しい依存関係を作成します。

![言語サーバー プロトコルのクライアントの依存関係を定義します。](media/lsp-define-lsp-dependency.png)

* **ソース**: 手動で定義されています。
* **名前**: 言語サーバー プロトコル クライアント プレビュー
* **識別子**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **バージョン範囲**: [1.0,2.0)
* **依存関係の解決をどのようには**: ユーザーがインストールされています。
* **URL のダウンロード**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> **ダウンロード URL**ユーザーの拡張機能のインストールが必要な依存関係をインストールする方法を知っているように入力する必要があります。

### <a name="language-server-and-runtime-installation"></a>言語のサーバーとランタイムのインストール

既定では、言語サーバー自体またはそれらを実行するために必要なランタイム Visual Studio の言語の LSP ベースのサーバーをサポートするために作成された拡張機能は含まれません。 拡張機能の開発者は、必要なランタイム言語のサーバーに配布するためです。 そのためにはいくつかの方法があります。

* 言語のサーバーは、コンテンツ ファイルとして VSIX に埋め込むことができます。
* 言語のサーバーをインストールする MSI の作成や、ランタイムが必要です。
* Marketplace をユーザーに伝える上のランタイムと言語のサーバーを取得する方法の手順を説明します。

### <a name="textmate-grammar-files"></a>TextMate 文法ファイル

LSP では、言語のテキストの色づけを提供する方法の仕様は含まれません。 Visual Studio での言語をカスタムの色づけを提供するには、拡張機能の開発者は TextMate 文法ファイルを使用できます。 カスタム TextMate 文法またはテーマのファイルを追加するには、次の手順を実行します。

1. 拡張機能内の「文法」をという名前のフォルダーを作成 (または、選択した任意の名前を指定できます)。

2. 「文法」フォルダー内には、カスタムの色づけを提供するか、*.tmlanguage または *.tmtheme ファイルをインクルードします。

3. クリックし、ファイルを右クリックして**プロパティ**です。 ビルドのアクションを変更する**コンテンツ**と**VSIX に含める**プロパティを true にします。

4. .Pkgdef ファイルを作成し、次のような行を追加します。

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. クリックし、ファイルを右クリックして**プロパティ**です。 ビルドのアクションを変更する**コンテンツ**と**VSIX に含める**プロパティを true にします。

前の手順を完了すると、「文法」フォルダーが、パッケージのインストールに追加リポジトリのソースとしてのディレクトリの名前 'MyLang' ('MyLang' は、あいまいさを排除の名前だけを指定し、一意の文字列を指定できます)。 電位として選択されるすべての文法 (.tmlanguage ファイル) およびテーマ ファイル (.tmtheme) このディレクトリ内および TextMate で提供される組み込みの文法をよりも優先します。 文法ファイルの宣言された拡張機能には、開いているファイルの拡張子が一致する場合、TextMate ステップされます。

## <a name="creating-a-simple-language-client"></a>シンプルな言語のクライアントを作成します。

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>メインのインターフェイスの[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

VSIX プロジェクトを作成した後に、プロジェクトに次の NuGet パッケージを追加します。

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 前の手順を完了したら、NuGet パッケージの依存関係を取得すると、Newtonsoft.Json や StreamJsonRpc パッケージもプロジェクトに追加されます。 **特定のバージョンの Visual Studio でこれらの新しいバージョンをインストールすることがない限り、これらのパッケージを更新しないを拡張機能がターゲット**です。 アセンブリは含まれません--、VSIX の代わりに、それらがから取得される、Visual Studio インストール ディレクトリです。 ユーザーのコンピューターでは、拡張機能 新機能がインストールされているより新しいバージョンのアセンブリを参照しているかどうかは*は機能しません*です。

実装する新しいクラスを作成し、 [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)インターフェイス、言語のクライアント言語の LSP ベース サーバーに接続するためのメイン インターフェイスです。

サンプルを次に示します。

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

実装する必要がある主な方法は[OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017)と[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)です。 [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) Visual Studio の拡張機能が読み込まれ、言語のサーバーが開始する準備ができているときに呼び出されます。 このメソッドを呼び出すことができます、 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)言語サーバーを開始するか、またはことを追加のロジックを実行し、呼び出すことを通知するには、すぐにデリゲート[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)以降。 **言語のサーバーをアクティブ化には、ある時点で StartAsync を呼び出す必要があります。**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)最終的に呼び出すことによって呼び出されるメソッドは、 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委任; 言語サーバーを起動しへの接続を確立するためのロジックが含まれています。 サーバーへの書き込みおよびサーバーから読み取るのためにストリームを含む接続オブジェクトが返される必要があります。 ここでスローされた例外がキャッチされ、Visual Studio での情報バー メッセージを介してユーザーに表示されます。

### <a name="activation"></a>アクティベーション

言語クライアント クラスを実装した場合は、方法は Visual Studio に読み込まれるされ、アクティブ化を定義するのには、次の 2 つの属性を定義する必要があります。

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio を使用して[MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) の機能拡張ポイントを管理します。 [エクスポート](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx)属性は、このクラスを拡張ポイントとしてピックアップあり適切な時に読み込まれることを Visual Studio を示します。

MEF を使用して、VSIX マニフェストのアセットとして MEF を定義することもあります。

VSIX マニフェスト デザイナーを開きに移動、**資産** タブ。

![MEF 資産を追加します。](media/lsp-add-asset.png)

新しい資産を作成する新規をクリックします。

![MEF 資産を定義します。](media/lsp-define-asset.png)

* **型**: [microsoft.visualstudio.mefcomponent]
* **ソース**: 現在のソリューション内のプロジェクト
* **プロジェクト**: [プロジェクト]

### <a name="content-type-definition"></a>コンテンツの種類の定義

現在、LSP ベースの言語拡張を読み込めません唯一の方法は、ファイル コンテンツの種類によってです。 つまり、言語クライアント クラスを定義するときに (を実装する[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)) の型を定義する必要がありますファイルを開くと、拡張機能を読み込むと、ときにします。 定義されているコンテンツの種類に一致するファイルが開いていない場合、拡張機能は読み込まれません。

これは、1 つまたは複数の ContentTypeDefinition クラスの定義を行います。

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

前の例では、コンテンツの種類の定義が作成で終わるファイルを`.bar`ファイル拡張子。 コンテンツの種類の定義が「バー」という名前を指定し、**必要があります**から派生[CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)です。

コンテンツの種類の定義を追加するを定義を言語クライアントの言語のクライアント クラスで拡張機能を読み込むときにできます。

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

LSP 言語のサーバーのサポートを追加することは必要ありませんを Visual Studio で、独自のプロジェクト システムを実装できます。 顧客が Visual Studio で、言語サービスの使用を開始するには、1 つのファイルまたはフォルダーを開くことができます。 実際には、LSP 言語のサーバーが開いているフォルダーまたはファイルのシナリオでのみ動作するように設計をサポートします。 カスタム プロジェクト システムが実装されている場合 (設定) などの一部の機能は機能しません。

## <a name="advanced-features"></a>高度な機能

### <a name="settings"></a>設定

カスタム言語固有サーバーの設定が、Visual Studio での LSP サポートのプレビュー リリースで使用可能ですが、改善が図ら処理中のサポートです。 設定は、どのような言語のサーバーをサポートします。 通常、言語のサーバーがデータを出力する方法を制御に固有です。 たとえば、言語のサーバーには、報告されたエラーの最大数の設定があります。 拡張機能の作成者は、特定のプロジェクトに対してユーザーによって変更できる既定値を定義します。

設定のサポート、LSP 言語サービス拡張機能を追加するのには、以下の手順に従います。

1. 設定とその既定値を格納する、プロジェクトでは、JSON ファイル (たとえば、"MockLanguageExtensionSettings.json") を追加します。 例:

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. JSON ファイルを右クリックし、選択**プロパティ**です。 変更、**ビルド**"Content"アクションおよび"VSIX に含める ' プロパティを true にします。

3. ConfigurationSections を実装し、JSON ファイルで定義されている設定のプレフィックスの一覧を返します (Visual Studio コードで、これにマップ package.json の構成セクション名)。

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. .Pkgdef ファイルをプロジェクトに追加 (新しいテキスト ファイルの追加し、.pkgdef ファイル拡張子を変更)。 Pkgdef ファイルには、この情報を含める必要があります。

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. .Pkgdef ファイルを右クリックし、選択**プロパティ**です。 変更、**ビルド**"Content"と"VSIX に含める"プロパティを true にするアクション。

6. 開き、`source.extension.vsixmanifest`ファイルし、[資産の追加、**資産**] タブ。

  ![vspackage の資産を編集します。](media/lsp-add-vspackage-asset.png)

  * **Type**: Microsoft.VisualStudio.VsPackage
  * **ソース**: ファイルシステム上のファイル
  * **パス**: [pkgdef ファイルのパス]

### <a name="user-editing-of-settings-for-a-workspace"></a>ユーザーが、ワークスペースの設定の編集

1. ユーザーは、サーバーを所有するファイルを含むワークスペースを開きます。
2. ユーザーは、"VSWorkspaceSettings.json"と呼ばれる".vs"フォルダーにファイルを追加します。
3. ユーザーは、サーバーは、設定の VSWorkspaceSettings.json ファイルに行を追加します。 例:

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>診断トレースを有効にします。
クライアントとサーバーで、問題をデバッグするときに役に立ちますの間のすべてのメッセージを出力する診断トレースを有効にすることができます。  診断トレースを有効にするには、次の操作を行います。

1. 開くか、ファイルを作成 ワークスペースの設定"VSWorkspaceSettings.json"(「ユーザーは、ワークスペースの設定の編集」を参照してください)。
2. 設定の json ファイルに次の行を追加します。

```json
{
    "foo.server.trace": "Off"
}
```

トレースの詳細度の 3 つの可能な値です。
* 「無効」: トレースが完全にオフ
* "Messages": オンになっているトレースが唯一の方法の名前と応答の ID がトレースされます。
* "Verbose": 追跡機能をオンにします。全体の rpc メッセージがトレースされます。

コンテンツのトレースが有効になってときは、"%temp%\visualstudio\lsp"ディレクトリ内のファイルに書き込まれます。  名前付け形式に依存して、ログ`[LanguageClientName]-[Datetime Stamp].log`です。  現時点では、トレースは、開いているフォルダーのシナリオを有効にのみにできます。  言語のサーバーをアクティブ化する 1 つのファイルを開いても診断トレースのサポートはありません。

### <a name="custom-messages"></a>カスタム メッセージ

メッセージを渡すと、標準の言語のサーバー プロトコルの一部ではない言語サーバーからの受信側のメッセージを容易にインプレース Api があります。 カスタム メッセージを処理するために実装[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)言語クライアント クラスのインターフェイスです。 [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md)ライブラリは、言語のクライアントとサーバーの言語の間でのカスタム メッセージの送信に使用します。 LSP 言語クライアント拡張機能では、その他の Visual Studio 拡張機能と同様であるため、カスタム メッセージを使用して拡張機能で、(その他の Visual Studio Api を使用して) Visual Studio する (つまり、LSP でサポートされていない) 機能を追加することできます。

#### <a name="receiving-custom-messages"></a>カスタム メッセージの受信

言語のサーバーからのカスタム メッセージを受信するには、実装、 [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017)プロパティ[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)し、カスタム メッセージを処理する方法を認識しているオブジェクトを返します. 次の例:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>カスタム メッセージを送信します。

言語のサーバーにカスタム メッセージを送信するには、実装、 [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017)メソッド[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)です。 言語のサーバーが開始され、メッセージを受信する準備が整ったときに、このメソッドが呼び出されます。 A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs)オブジェクトが、言語を使用してサーバーにメッセージを送信し、保持することができるパラメーターとして渡される[VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Api です。 次の例:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>中間層

ことも、拡張機能の開発者可能性があります言語サーバーから送受信された LSP メッセージを途中受信します。 など、開発者は拡張機能を使用して、特定の LSP メッセージの送信メッセージのパラメーターを変更するして可能性があります。 または LSP 機能 (たとえば完了) の言語のサーバーから返される結果を変更します。 この処理が必要なときに、拡張機能の開発者は、LSP メッセージを中断 MiddleLayer API を使用することができます。

各 LSP メッセージには、傍受のための独自の中間層インターフェイスがあります。 特定のメッセージをインターセプトするには、そのメッセージの中間層インターフェイスを実装するクラスを作成します。 次に、実装、 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)言語クライアント クラスのインターフェイスし、オブジェクトのインスタンスを返す、 [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017)プロパティです。 次の例:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

中間層機能とは、まだ開発中で、まだ包括的なです。

## <a name="sample-lsp-language-server-extension"></a>サンプル LSP 言語のサーバーの拡張機能

Visual Studio で LSP クライアント API を使用して拡張機能のサンプルのソース コードを参照して VSSDK のサンプル拡張機能を参照してください。 [LSP サンプル](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)です。

## <a name="faq"></a>FAQ

**Visual Studio で、豊富な機能のサポートを提供する LSP 言語サーバーを補完するカスタム プロジェクト システムを構築したいと思うことにどのようにしますか?**

Visual Studio でサーバーを LSP ベースの言語のサポートが依存、[フォルダーを開く機能](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/)カスタム プロジェクト システムを必要としないものでは具体的にします。 指示に従って、独自のカスタム プロジェクト システムを構築できます[ここ](https://github.com/Microsoft/VSProjectSystem)が、設定など、一部の機能が動作しない可能性があります。 LSP 言語のサーバーの既定の初期化ロジックは、現在開いているフォルダーのルート フォルダーの場所を渡すのでカスタム プロジェクト システムを使用する場合は、ため、言語のサーバーは初期化中にカスタム ロジックを提供する必要があります。正常に起動します。

**デバッガーのサポートを追加する方法は?**

サポートを提供する予定の[共通のプロトコルをデバッグ](https://code.visualstudio.com/docs/extensionAPI/api-debugging)将来のリリースでします。

**VS サポートされている言語サービス インストールされている (たとえば、JavaScript など) が既にあるを場合は引き続き、LSP 言語サーバー拡張機能のインストール (linting) などの追加機能を提供するしますか。**

[はい] が、すべての機能が正しく機能します。 LSP 言語サーバー拡張機能の最終的な目標は、Visual Studio によってネイティブにサポートされている言語サービスを有効にするのにです。 LSP 言語のサーバーを使用して追加のサポートを提供する拡張機能を作成できますが、一部の機能 (IntelliSense) などがスムーズにできません。 一般に、既存のテーブルを拡張しない、言語の新しいエクスペリエンスを提供するため、LSP 言語サーバー拡張機能を使用することをお勧めします。

**完了した LSP 言語サーバー VSIX を発行する場合ですか。**

Marketplace を参照してください[ここ](walkthrough-publishing-a-visual-studio-extension.md)です。
