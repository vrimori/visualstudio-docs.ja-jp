---
title: 'チュートリアル: コマンドラインを使用して、Visual Studio 拡張機能の発行 |Microsoft Docs'
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb35365220ade512defc180b06e46b95999dfa7b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857216"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>チュートリアル: コマンドラインを使用して Visual Studio 拡張機能を公開

このチュートリアルでは、Visual Studio 拡張機能を Visual Studio Marketplace に発行する方法、コマンドラインを使用します。 開発者が使用できる、拡張機能を Marketplace に追加すると、 [**拡張機能と更新**](../ide/finding-and-using-visual-studio-extensions.md)ダイアログを新規および更新された拡張機能の参照があります。

VsixPublisher.exe は、Marketplace への発行の Visual Studio 拡張機能のコマンド ライン ツールです。 ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe からアクセスできます。 このツールで使用できるコマンドが:**発行**、 **createPublisher**、 **deletePublisher**、 **deleteExtension**、 **ログイン**、**ログアウト**します。

## <a name="commands"></a>コマンド

### <a name="publish"></a>publish

拡張機能を Marketplace に発行します。 拡張機能は、vsix、exe/msi ファイル、またはリンクできます。 同じバージョンの拡張機能が既に存在する場合、拡張機能が上書きされます。 拡張機能が存在しない場合、新しい拡張機能が作成されます。

|コマンド オプション |説明 |
|---------|---------|
|ペイロード (必須) | いずれかのパスを発行するペイロードまたは"詳細情報の URL"として使用するリンク。 |
|publishManifest (必須) | 発行へのパスはマニフェストを使用するファイルです。 |
|ignoreWarnings | 拡張機能を発行するときに無視する警告の一覧。 これらの警告は、拡張機能を発行するときに、コマンド ライン メッセージとして表示されます。 (たとえば、"VSIXValidatorWarning01、VSIXValidatorWarning02")  
|personalAccessToken | 個人用アクセス トークン (PAT)、発行元を認証するために使用します。 指定しない場合、PAT、ログインしているユーザーから取得されます。 |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Marketplace で発行元を作成します。 将来的なアクション (たとえば、拡張機能の削除/公開) のマシンにも、パブリッシャーを記録します。

|コマンド オプション |説明 |
|---------|---------|
|displayName (必須) | パブリッシャーの名前を表示します。 |
|publisherName (必須) | パブリッシャー (たとえば、"識別子") の名前。 |
|personalAccessToken (必須) | 個人用アクセス トークンを発行元を認証するために使用します。 |
|shortDescription | パブリッシャー (ファイルではありません) の簡単な説明。 |
|longDescription | パブリッシャー (ファイルではありません) の詳しい説明。 |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Marketplace でのパブリッシャーを削除します。

|コマンド オプション |説明 |
|---------|---------|
|publisherName (必須) | パブリッシャー (たとえば、"識別子") の名前。 |
|personalAccessToken (必須) | 個人用アクセス トークンを発行元を認証するために使用します。 |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Marketplace から拡張機能を削除します。

|コマンド オプション |説明 |
|---------|---------|
|extensionName (必須) | 削除する拡張機能の名前。 |
|publisherName (必須) | パブリッシャー (たとえば、"識別子") の名前。 |
|personalAccessToken | 個人用アクセス トークンを発行元を認証するために使用します。 指定しない場合、pat、ログインしているユーザーから取得されます。 |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>ログイン

パブリッシャーをコンピューターにログインします。

|コマンド オプション |説明 |
|---------|---------|
|(必須 personalAccessToken | 個人用アクセス トークンを発行元を認証するために使用します。 |
|publisherName (必須) | パブリッシャー (たとえば、"識別子") の名前。 |
|上書き | 新しい個人用アクセス トークンを使用して、既存のパブリッシャーが上書きされることを指定します。 |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>ログアウト

マシンからの発行元のログを記録します。

|コマンド オプション |説明 |
|---------|---------|
|publisherName (必須) | パブリッシャー (たとえば、"識別子") の名前。 |
|ignoreMissingPublisher | 指定されたパブリッシャーは、既にログに記録-にない場合、ツールがエラーではなく必要があるを指定します。 |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest ファイル

PublishManifest ファイルによって使用されます、**発行**コマンド。 Marketplace を知る必要がある拡張機能に関するすべてのメタデータを表します。 アップロードされている拡張機能を VSIX 拡張機能の場合は、"identity"プロパティは設定"internalName"をのみが必要です。 これは、"identity"プロパティの残りの部分は vsixmanifest ファイルから生成できるためです。 拡張機能は、msi と exe またはリンク拡張機能には、ユーザーは"identity"プロパティで必要なフィールドを指定する必要があります。 マニフェストの残りの部分には、Marketplace に固有の情報が含まれています (たとえば、カテゴリ、Q & A が有効かどうなど。)。

VSIX 拡張機能 publishManifest ファイルのサンプル:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI と EXE またはリンクの publishManifest ファイル サンプル:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>資産ファイル

Readme ファイルのイメージなどを埋め込むため、資産ファイルを指定できます。 たとえば、拡張機能がある次の「概要」Markdown のドキュメントとします。

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

前の例では、"images/testlogo.png"を解決するには、ユーザーで"を構成する assetFiles"を提供できます、発行の下のようにマニフェスト。

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>発行のチュートリアル

### <a name="prerequisites"></a>必須コンポーネント

このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。

### <a name="create-a-visual-studio-extension"></a>Visual Studio 拡張機能を作成します。

この場合は、既定の VSPackage の拡張機能は使用しますが、同じ手順は、すべての種類の拡張機能の有効です。

1. メニュー コマンドが"TestPublish"という名前の c# で VSPackage を作成します。 詳細については、次を参照してください。[初めての拡張機能を作成します。Hello World](../extensibility/extensibility-hello-world.md)します。

### <a name="package-your-extension"></a>拡張機能をパッケージ化します。

1. 製品名、作成者、およびバージョンの詳細については、正しい情報には、拡張機能 vsixmanifest を更新します。

   ![更新プログラムの拡張機能の vsixmanifest](media/update-extension-vsixmanifest.png)

2. 拡張機能を構築**リリース**モード。 これで、拡張機能は \bin\Release フォルダーで、VSIX としてパッケージ化されます。

3. インストールを確認する VSIX をダブルクリックすることができます。

### <a name="test-the-extension"></a>拡張機能をテストします。

 拡張機能を配布する前に、ビルド、およびテストを Visual Studio の実験用インスタンスで正しくインストールされていることを確認します。

1. Visual Studio でデバッグを開始します。 Visual Studio の実験用インスタンスを開きます。

2. 実験用のインスタンスに移動、**ツール**メニューをクリックします**拡張機能と更新しています.**.TestPublish 拡張機能では、中央のウィンドウに表示する必要があり、有効にします。

3. **ツール** メニューの テスト コマンドを表示するかどうかを確認します。

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>コマンドラインを使用して Marketplace に拡張機能を公開します。

1. 拡張機能のリリース バージョンが組み込まれているし、最新の状態であるようにします。

2. Publishmanifest.json と overview.md ファイルを作成したことを確認します。

3. コマンドラインを開き、${VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\ ディレクトリに移動します。

4. 新しいパブリッシャーを作成するには、次のコマンドを使用します。

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. パブリッシャーの作成に成功、次のコマンド ライン メッセージが表示されます。

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. 移動して作成した新しい発行元を確認できる[Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. 新しい拡張機能を公開するには、次のコマンドを使用します。

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. パブリッシャーの作成に成功、次のコマンド ライン メッセージが表示されます。

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. 移動して発行された新しい拡張機能を確認する[Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace から拡張機能をインストールします。

これで、拡張機能を公開すると、Visual Studio にインストールし、テストします。

1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新しています.**.

2. クリックして**オンライン**TestPublish し検索します。

3. **[ダウンロード]** をクリックします。 拡張機能は、インストールのスケジュールされます。

4. インストールを完了するには、Visual Studio のすべてのインスタンスを閉じます。

## <a name="remove-the-extension"></a>拡張機能を削除します。

お使いのコンピューターと、Visual Studio Marketplace から拡張機能を削除できます。

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>コマンドラインを使用して Marketplace から拡張機能を削除するには

1. 拡張機能を削除する場合は、次のコマンドを使用します。

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. 拡張機能が正常に削除するには、次のコマンド ライン メッセージが表示されます。

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>お使いのコンピューターから、拡張機能を削除するには

1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新しています.**.

2. "MyVsixExtension"を選択し、クリックして**アンインストール**します。 拡張機能は、アンインストールにスケジューリングされます。

3. アンインストールを完了するには、Visual Studio のすべてのインスタンスを閉じます。
