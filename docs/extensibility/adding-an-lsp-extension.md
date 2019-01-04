---
title: 言語サーバー プロトコルの拡張機能の追加 |Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad112d34c8f23a7738137f148f00a38a27335424
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966561"
---
# <a name="add-a-language-server-protocol-extension"></a>言語サーバー プロトコルの拡張機能を追加します。

言語サーバー プロトコル (LSP) は、JSON RPC v2.0 では、言語のさまざまなコード エディターにサービスの機能を提供するために使用の形式での一般的なプロトコルです。 プロトコルを使用して、言語の IntelliSense、エラーの診断のようなサービスの機能を提供する、すべての参照、お客様の LSP をサポートするさまざまなコード エディターになどを検索するサーバーを 1 つの言語を記述できます。 Visual Studio での言語サービスを追加して、いずれかでこれまでは、構文の強調表示など、または Visual Studio 機能拡張 Api の完全なセットを使用してカスタム言語サービスを記述することで、基本的な機能を提供する TextMate 文法ファイルを使用するには高度なデータを提供します。 お客様の LSP は、3 番目のオプション、サポートします。

![Visual Studio での言語サーバー プロトコルのサービス](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>言語サーバー プロトコル

![言語サーバー プロトコルの実装](media/lsp-implementation.png)

この記事では、LSP に基づく言語を使用している Visual Studio 拡張機能を作成する方法について説明します。 LSP ベースの言語、サーバーが既に開発し、Visual Studio に統合することが想定しています。

Visual Studio 内でサポートについては、言語のサーバーは、ストリーム ベースの転送メカニズムを使用して、クライアント (Visual Studio) との通信できます。

* 標準の入力/出力ストリーム
* 名前付きパイプ
* ソケット (TCP のみ)

LSP と Visual Studio でのサポートの目的は、Visual Studio 製品の一部ではない言語のオンボード サービスです。 (C# のような) Visual Studio での既存の言語サービスを拡張するものではありません。 既存の言語を拡張するには、言語サービスの機能拡張ガイドを参照してください (たとえば、 ["Roslyn".NET コンパイラ プラットフォーム](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md))。

ドキュメントを参照して、プロトコル自体の詳細については、[ここ](https://github.com/Microsoft/language-server-protocol)します。

作成する方法の詳細については、サンプルの言語のサーバーまたは Visual Studio のコードに既存言語のサーバーを統合する方法ドキュメントを参照して、[ここ](https://code.visualstudio.com/docs/extensions/example-language-server)します。

## <a name="language-server-protocol-features-supported"></a>言語サーバー プロトコルの機能がサポートされています

次の LSP 機能は、これまでに Visual Studio でサポートされます。

メッセージ | Visual Studio でサポートされています
--- | ---
初期化します。 | 可
初期化済み | 可
シャットダウン | 可
終了 | 可
$/cancelRequest | 可
window/showMessage | 可
window/showMessageRequest | 可
ウィンドウ/logMessage | 可
製品利用統計情報/イベント |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | 可
workspace/didChangeWatchedFiles | 可
ワークスペース、またはシンボル | 可
workspace/executeCommand | 可
workspace/applyEdit | 可
textDocument/publishDiagnostics | 可
textDocument/didOpen | 可
textDocument/didChange | 可
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | 可
textDocument/didClose | 可
textDocument/完了 | 可
完了/解決 | 可
textDocument/hover | 可
textDocument/signatureHelp | 可
textDocument/参照 | 可
textDocument/documentHighlight | 可
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

> [!NOTE]
> 以降では、Visual Studio 15.8 Preview 3、一般的な言語サーバー プロトコルのサポートは、Visual Studio に組み込まれています。  LSP 拡張機能のプレビューを使用して構築した場合[言語サーバー クライアントの VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)バージョンについてに 15.8 Preview 3 以降にアップグレードした後の操作停止されます。  再度動作している LSP 拡張機能を取得するには、次を実行する必要があります。
>
> 1. Microsoft Visual Studio の言語サーバー プロトコル Preview VSIX をアンインストールします。  15.8 Preview 4 以降、Visual Studio で、アップグレードを実行するたびに自動的に検出しのアップグレード処理中に VSIX のプレビューの削除します。
>
> 2. Nuget 参照を最新の非プレビュー バージョンに更新[LSP パッケージ](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)します。
>
> 3. VSIX マニフェストで、Microsoft Visual Studio 言語サーバー プロトコル プレビュー VSIX への依存関係を削除します。
>
> 4. VSIX は、インストール先の下限の境界として Visual Studio 15.8 Preview 3 を指定することを確認します。
>
> 5. 再構築し、再デプロイします。

### <a name="create-a-vsix-project"></a>VSIX プロジェクトを作成します。

LSP に基づく言語サーバーを使用して、言語サービス拡張を作成するには、最初に確認がある、 **Visual Studio 拡張機能の開発**ワークロードの VS インスタンスをインストールします。

次に移動して新しい空白 VSIXProject を作成**ファイル** > **新しいプロジェクト** > **Visual c#**  >  **機能拡張** > **VSIX プロジェクト**:

![vsix プロジェクトを作成します。](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>言語のサーバーとランタイムのインストール

既定では、言語もサーバー自体またはそれらを実行するために必要なランタイムで、Visual Studio の言語の LSP ベースのサーバーをサポートするために作成した拡張機能は含まれません。 拡張機能の開発者は、言語のサーバーおよび必要なランタイムを配布する責任を負います。 そのためにはいくつかの方法はあります。

* 言語のサーバーは、コンテンツ ファイルとして VSIX に埋め込むことができます。
* 言語サーバーをインストールする MSI の作成や、ランタイムが必要です。
* Marketplace をユーザーに伝えるのランタイムと言語のサーバーを取得する方法の手順を説明します。

### <a name="textmate-grammar-files"></a>TextMate 文法ファイル

お客様の LSP では、言語のテキストの色づけを提供する方法の仕様は含まれません。 カスタムの色づけの Visual Studio での言語を提供するには、拡張機能の開発者は、TextMate の文法ファイルを使用できます。 カスタム TextMate 文法またはテーマ ファイルを追加するには、次の手順を実行します。

1. 拡張機能内で"Grammars"をという名前のフォルダーの作成 (または、選択した任意の名前であることができます)。

2. 内で、*文法*フォルダーが含まれて *\*.tmlanguage*、  *\*.plist*、  *\*.tmtheme*、または *\*.json*するカスタムの色づけを提供するファイル。

3. クリックし、ファイルを右クリックして**プロパティ**します。 変更、**ビルド**アクションを**コンテンツ**と**VSIX に含める**プロパティを true にします。

4. 作成、 *.pkgdef*ファイルし、次のように行を追加します。

   ```xml
   [$RootKey$\TextMate\Repositories]
   "MyLang"="$PackageFolder$\Grammars"
   ```

5. クリックし、ファイルを右クリックして**プロパティ**します。 変更、**ビルド**アクションを**コンテンツ**と**VSIX に含める**プロパティを true にします。

前の手順が完了したら、*文法*フォルダー、パッケージのインストールに追加されますリポジトリ ソースとしてのディレクトリの名前 'MyLang' ('MyLang' 曖昧性除去の名ですし、一意の文字列を指定できます)。 すべての文法 (*.tmlanguage*ファイル) とテーマ ファイル (*.tmtheme*ファイル) この directory が電位として選択し、TextMate で提供される組み込みの文法によりも優先されます。 文法ファイルの宣言された拡張機能が開かれているファイルの拡張子に一致する場合は、TextMate は進みます。

## <a name="create-a-simple-language-client"></a>単純な言語のクライアントを作成します。

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>メイン インターフェイス - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

VSIX プロジェクトを作成した後は、次の NuGet パッケージをプロジェクトに追加します。

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 前の手順が完了したら、NuGet パッケージの依存関係を取得すると、Newtonsoft.Json および StreamJsonRpc パッケージもプロジェクトに追加されます。 **特定のバージョンの Visual Studio でこれらの新しいバージョンをインストールすることがない場合に、これらのパッケージを更新できませんが、拡張機能のターゲット**します。 アセンブリを含めることができません--、VSIX の代わりに、それらを集荷する Visual Studio のインストール ディレクトリから。 かどうか、拡張機能であるユーザーのコンピューターにインストールされている内容よりも新しいバージョンのアセンブリを参照している*は機能しません*します。

実装する新しいクラスを作成し、 [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)インターフェイス、言語のクライアント言語の LSP ベース サーバーに接続するのに必要なメイン インターフェイスです。

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
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

実装する必要がある主な方法は[OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017)と[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)します。 [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) Visual Studio の拡張機能が読み込まれ、言語のサーバーを開始する準備がときに呼び出されます。 このメソッドで呼び出すことができます、 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)言語サーバーを起動する必要があります、または追加ロジックを実行し、呼び出すことができますを通知するには、すぐにデリゲート[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)以降。 **言語のサーバーを有効にするには、ある時点で StartAsync を呼び出す必要があります。**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)最終的に呼び出すことによって呼び出されたメソッドには、 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委任; 言語のサーバーを起動し、それへの接続を確立するためのロジックが含まれています。 サーバーへの書き込みと、サーバーから読み取るのためのストリームを含む接続オブジェクトを返す必要があります。 ここでスローされた例外がキャッチされ、Visual Studio での情報バー メッセージを使用してユーザーに表示されます。

### <a name="activation"></a>アクティベーション

言語クライアント クラスが実装されると、その方法は Visual Studio に読み込まれるされ、アクティブ化を定義する 2 つの属性を定義する必要があります。

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio を使用して[MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) の機能拡張ポイントを管理します。 [エクスポート](/dotnet/api/system.componentmodel.composition.exportattribute)属性は、このクラスを拡張ポイントとして選択し、適切な時に読み込まれることを Visual Studio を示します。

MEF を使用して、VSIX マニフェストで、資産として MEF を定義することもあります。

VSIX マニフェスト デザイナーを開きに移動、**資産** タブ。

![MEF の資産を追加します。](media/lsp-add-asset.png)

新しい資産を作成する新規をクリックします。

![MEF の資産を定義します。](media/lsp-define-asset.png)

* **型**:Microsoft.VisualStudio.MefComponent
* **ソース**:現在のソリューション内のプロジェクト
* **プロジェクト**: [プロジェクト]

### <a name="content-type-definition"></a>コンテンツ タイプの定義

現在、LSP に基づく言語拡張を読み込めません唯一の方法は、ファイル コンテンツの種類ことです。 つまり、言語クライアント クラスを定義するときに (実装[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)) の型を定義する必要がありますファイルを開くと、により、拡張機能を読み込むときにします。 定義されている、コンテンツの種類に一致するファイルは開かれず、拡張機能は読み込まれません。

これは、1 つまたは複数の ContentTypeDefinition クラスの定義を通じて実行されます。

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

終わるファイルのコンテンツ タイプの定義を作成する前の例では、 *.bar*ファイル拡張子。 コンテンツ タイプの定義が"bar"という名前を指定し、**する必要があります**から派生[CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)します。

コンテンツ タイプの定義を追加した後に言語クライアント クラスの拡張機能の言語クライアントを定義することができますし。

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

LSP 言語のサーバーのサポートの追加の場合、Visual Studio で独自のプロジェクト システムを実装するためにする必要はありません。 顧客は、Visual Studio で、言語サービスの使用を開始する 1 つのファイルまたはフォルダーを開くことができます。 実際には、LSP 言語のサーバーが開いているフォルダーまたはファイルのシナリオでのみ動作するように設計をサポートします。 カスタム プロジェクト システムが実装されている場合 (設定) などの一部の機能は機能しません。

## <a name="advanced-features"></a>高度な機能

### <a name="settings"></a>設定

カスタム言語固有サーバーの設定のサポートが使用可能なには、改善されて処理中です。 設定は、特定の言語のサーバーでサポートを通知し、通常、言語のサーバーがデータを出力する方法を制御します。 たとえば、言語サーバーには、報告されたエラーの最大数の設定があります。 拡張機能の作成者は、特定のプロジェクトに対してユーザーによって変更できる既定値を定義します。

LSP 言語サービス拡張機能への設定のサポートを追加する以下の手順に従います。

1. JSON ファイルを追加 (たとえば、 *MockLanguageExtensionSettings.json*) 設定とその既定値を含むプロジェクト。 例:

   ```json
   {
    "foo.maxNumberOfProblems": -1
   }
   ```
2. JSON ファイルを右クリックし、選択**プロパティ**します。 変更、**ビルド**アクションを「コンテンツ」、"VSIX に含める ' プロパティを true にします。

3. ConfigurationSections を実装し、JSON ファイルで定義された設定のプレフィックスの一覧を返します (Visual Studio Code で、これにマップ package.json 内の構成セクション名)。

   ```csharp
   public IEnumerable<string> ConfigurationSections
   {
      get
      {
          yield return "foo";
      }
   }
   ```

4. .Pkgdef ファイルをプロジェクトに追加する (新しいテキスト ファイルを追加して、.pkgdef ファイル拡張子を変更)。 Pkgdef ファイルには、この情報を含める必要があります。

   ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
   ```

    サンプル:
    ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. .Pkgdef ファイルを右クリックし、選択**プロパティ**します。 変更、**ビルド**アクションを**コンテンツ**と**VSIX に含める**プロパティを true にします。

6. 開き、 *source.extension.vsixmanifest*ファイルを開き、資産を追加、**資産** タブ。

   ![vspackage の資産を編集します。](media/lsp-add-vspackage-asset.png)

   * **型**:Microsoft.VisualStudio.VsPackage
   * **ソース**:ファイル システム上のファイルします。
   * **パス**: [へのパス、 *.pkgdef*ファイル]

### <a name="user-editing-of-settings-for-a-workspace"></a>ユーザーのワークスペースの設定の編集

1. ユーザーは、サーバーを所有するファイルを含むワークスペースを開きます。
2. ユーザーが内のファイルを追加、 *.vs*という名前のフォルダー *VSWorkspaceSettings.json*します。
3. ユーザーは、線を追加、 *VSWorkspaceSettings.json*ファイルの設定、サーバーを提供します。 例:

   ```json
   {
    "foo.maxNumberOfProblems": 10
   }
   ```
   ### <a name="enabling-diagnostics-tracing"></a>診断トレースを有効にします。
   クライアントとサーバーで、問題をデバッグするときに役に立ちます間のすべてのメッセージを出力する診断トレースを有効にすることができます。  診断トレースを有効にするには、次の操作を行います。

4. 開くか、ワークスペースの設定ファイルを作成する*VSWorkspaceSettings.json* (「ユーザーのワークスペースの設定の編集」を参照してください)。
5. 設定の json ファイルでは、次の行を追加します。

```json
{
    "foo.trace.server": "Off"
}
```

トレースの詳細度の 3 つの値があります。
* オフ: トレースは完全にオフ
* "Messages": トレースをオンが唯一のメソッドの名前、および応答の ID がトレースされます。
* "Verbose"トレースを有効にする場合。全体の rpc メッセージがトレースされます。

内のファイルに書き込まれるコンテンツにトレースを有効にする場合、 *%temp%\VisualStudio\LSP*ディレクトリ。  名前付け形式に依存して、ログ *[LanguageClientName]-[時刻のタイムスタンプ] .log*します。  現時点では、トレースは、フォルダーを開く場合のみ有効にできます。  言語サーバーをアクティブ化する 1 つのファイルを開くしても、診断トレースのサポートはありません。

### <a name="custom-messages"></a>カスタム メッセージ

メッセージを渡すと、標準の言語サーバー プロトコルの一部ではない言語のサーバーから受信側のメッセージを容易にインプレース Api があります。 カスタム メッセージを処理するために実装[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)言語クライアント クラスのインターフェイス。 [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md)ライブラリ、言語のクライアントとサーバーの言語の間でのカスタム メッセージの送信に使用されます。 LSP 言語クライアント拡張機能では、その他の Visual Studio 拡張機能と同様であるため (その他の Visual Studio Api を使用して) Visual Studio に、カスタム メッセージを介して、拡張機能の追加の機能 (お客様の LSP でサポートされていない) を追加するを決定できます。

#### <a name="receiving-custom-messages"></a>カスタム メッセージの受信

言語サーバーからのカスタム メッセージを受信するには、実装、 [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017)プロパティ[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)カスタム メッセージを処理する方法を認識しているオブジェクトを返す. 次の例:

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

言語サーバーにカスタム メッセージを送信するには、実装、 [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017)メソッド[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)します。 言語のサーバーが開始され、メッセージを受信する準備がこのメソッドが呼び出されます。 A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs)オブジェクトが、言語を使用してサーバーにメッセージを送信し、保持することができますをパラメーターとして渡される[VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Api。 次の例:

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

場合によって、拡張機能の開発者は、言語のサーバーから送受信 LSP メッセージを途中受信する可能性があります。 など、拡張機能、開発者は、LSP メッセージを特定するには、送信されるメッセージ パラメーターを変更するまたは LSP 機能 (たとえば、入力候補) の言語のサーバーから返される結果を変更する可能性があります。 これが必要な場合、拡張機能の開発者は、LSP メッセージを先に MiddleLayer API を使用できます。

各 LSP メッセージには、傍受のための独自の中間層インターフェイスがあります。 特定のメッセージを受信するには、そのメッセージを中間層インターフェイスを実装するクラスを作成します。 次に、実装、 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)言語クライアント クラスのインターフェイスし、で、オブジェクトのインスタンスを返す、 [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017)プロパティ。 次の例:

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

中間層機能は、まだ開発中とまだ包括的なです。

## <a name="sample-lsp-language-server-extension"></a>LSP 言語サーバー拡張機能のサンプル

Visual Studio での LSP クライアント API を使用して拡張機能のサンプルのソース コードについては、VSSDK のサンプル拡張機能を参照してください。 [LSP サンプル](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)します。

## <a name="faq"></a>FAQ

**Visual Studio より豊富な機能のサポートを提供するために LSP 言語サーバーを補足するカスタム プロジェクト システムを構築したいこと移動する方法でしょうか。**

Visual Studio でサーバーを LSP ベースの言語のサポートに依存、[フォルダーを開く機能](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/)カスタム プロジェクト システムを必要としないものでは具体的には。 次の手順については、独自のカスタム プロジェクト システムを構築できます[ここ](https://github.com/Microsoft/VSProjectSystem)、設定など、一部の機能は機能しません。 LSP 言語のサーバーの既定の初期化ロジックがカスタム プロジェクト システムを使用する場合は、言語、サーバーはことを確認するために初期化中にカスタム ロジックを提供する必要がありますので、現在開いているフォルダーのルート フォルダーの場所で渡すには正常に起動します。

**デバッガーのサポートを追加する方法はありますか**

サポートを提供する、[共通のプロトコルをデバッグ](https://code.visualstudio.com/docs/extensionAPI/api-debugging)将来のリリースでします。

**VS サポートされている言語サービス インストールされている (たとえば、JavaScript など) が既にあるを場合できますはまだ LSP 言語サーバー拡張機能のインストール (lint 処理) などの他の機能を提供するでしょうか。**

[はい] が、すべての機能は正常に動作します。 LSP 言語サーバー拡張機能の最終的な目標は、Visual Studio でネイティブにサポートされている言語サービスを有効にします。 LSP 言語のサーバーを使用して追加のサポートを提供する拡張機能を作成することができますが、一部の機能 (IntelliSense) などには、滑らかなエクスペリエンスはできません。 一般に、LSP 言語サーバー拡張機能がない既存の拡張する、言語の新しいエクスペリエンスを提供することで使用することをお勧めします。

**完了 LSP 言語サーバー VSIX を発行場所ですか。**

Marketplace を参照してください[ここ](walkthrough-publishing-a-visual-studio-extension.md)します。
