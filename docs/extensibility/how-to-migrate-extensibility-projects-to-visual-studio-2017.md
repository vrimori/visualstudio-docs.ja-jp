---
title: '方法: Visual Studio 2017 を機能拡張プロジェクトの移行 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 93f5d663a31d43dc7a52cbd11261ca78134c682a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>方法: Visual Studio 2017 を機能拡張プロジェクトの移行

このドキュメントでは、Visual Studio 2017 に機能拡張プロジェクトをアップグレードする方法について説明します。 プロジェクト ファイルを更新する方法を記述するだけでなく、新しいバージョン 3 VSIX マニフェスト形式 (VSIX v3) に拡張機能マニフェスト バージョン 2 (VSIX v2) からアップグレードする方法も説明します。

## <a name="install-visual-studio-2017-with-required-workloads"></a>必要なワークロードでの Visual Studio 2017 をインストールします。

インストールでは、次のワークロードを確認します。

* .NET デスクトップ開発
* Visual Studio 拡張機能の開発

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017 で開いている VSIX ソリューション

すべての VSIX プロジェクトには、Visual Studio 2017 にメジャー バージョン一方向のアップグレードが必要です。

プロジェクト ファイル (たとえば *.csproj) が更新されます。

* MinimumVisualStudioVersion - 15.0 に設定されています
* OldToolsVersion (場合以前存在)-14.0 に設定されています

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.VSSDK.BuildTools NuGet パッケージを更新します。

>**注:**ソリューションが Microsoft.VSSDK.BuildTools NuGet パッケージを参照していない場合は、この手順をスキップすることができます。

新しい VSIX v3 で拡張機能を構築するために (バージョン 3) の形式で、ソリューションは新しい VSSDK ビルド ツールを使用して構築する必要があります。 これは、Visual Studio 2017、と共にインストールされますが、NuGet 経由で以前のバージョンへの参照を VSIX v2 の拡張機能を保持する場合があります。 その場合、ソリューションの Microsoft.VSSDK.BuildTools NuGet パッケージの更新を手動でインストールする必要があります。

Microsoft.VSSDK.BuildTools へ NuGet の参照を更新するには。

* ソリューションを右クリックし、**[ソリューションの NuGet パッケージの管理...]** を選択します。
* 移動し、**更新**タブです。
* Microsoft.VSSDK.BuildTools (最新バージョン) を選択します。
* キーを押して**更新**です。

![VSSDK ビルド ツール](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX 拡張機能マニフェストを変更をします。

Visual Studio のユーザーのインストールは、拡張機能を実行するために必要なすべてのアセンブリを持つようにするため、拡張機能マニフェスト ファイルですべての前提条件コンポーネントまたはパッケージを指定します。 ユーザーが、拡張機能をインストールしようとしたとき、VSIXInstaller はすべての前提条件がインストールされているかどうかを確認します。 一部が見つからない場合は、拡張機能のインストール プロセスの一環として、見つからないコンポーネントをインストールするユーザーが求められます。

>**注:**には、少なくともすべての拡張機能は、前提条件として、Visual Studio のコア エディターのコンポーネントを指定する必要があります。

* (Source.extension.vsixmanifest と通常呼ばれる) 拡張機能マニフェスト ファイルを編集します。
* 確認`InstallationTarget`15.0 が含まれています。
* (次の例で示す) のように、必要なインストール前提条件を追加します。
  * インストールの前提条件コンポーネントの Id のみを指定することをお勧めします。
  * このドキュメントの最後を参照してください[コンポーネントの Id を識別する方法について](#finding-component-ids)です。

例:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>オプション: デザイナーを使用して VSIX 拡張機能マニフェストを変更します。

マニフェストの XML を直接編集する代わりに、マニフェスト デザイナーにある**新しい前提条件**を使用して、前提条件を選択し、XML を更新することができます。

>**注:**マニフェスト デザイナーはのみを許可すると、現在の Visual Studio インスタンスにインストールされているコンポーネント (ワークロードやパッケージ) を選択します。 ワークロード、パッケージ、または現在インストールされていないコンポーネントの前提条件を追加する必要がある場合は、マニフェスト XML を直接編集します。

* [デザイン] source.extension.vsixmanifest ファイルを開きます。
* 選択**の前提条件**タブとキーを押して**新規**ボタンをクリックします。

  ![VSIX マニフェスト デザイナー](media/vsix-manifest-designer.png)

* **新しい前提条件の追加**ウィンドウが開きます。

  ![vsix の前提条件を追加します。](media/add-vsix-prerequisite.png)

* **[名前]** のドロップダウンをクリックして、必要な前提条件を選択します。
* 必要な場合は、バージョンを更新します。

  >注: バージョン フィールドがあらかじめ設定されます、範囲の最大またがりメモリ割り当て (は含まれません) を持つ、現在インストールされているコンポーネントのバージョンとコンポーネントの次のメジャー バージョン。

  ![roslyn 前提条件を追加します。](media/add-roslyn-prerequisite.png)

* **[OK]** を押します。

## <a name="update-debug-settings-for-project"></a>プロジェクトのデバッグの設定を更新します。

Visual Studio の実験用インスタンスで拡張機能をデバッグする場合、以下のことを確認のプロジェクト設定**デバッグ** > **開始アクション**が、**外部開始プログラム:**値は、Visual Studio 2017 インストールの devenv.exe ファイルに設定します。

ようになります。

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![外部プログラムを開始します。](media/start-external-program.png)

>**注:**デバッグの開始操作が通常に格納されている、。 csproj.user ファイル。 このファイルは、.gitignore ファイルに通常含まれており、そのため、通常で保存されていない他のプロジェクト ファイルをソース管理にコミットされたときに。 そのため、新しいソース管理からソリューションを抜粋したいると、プロジェクトには 開始動作の設定値はありません可能性があります。 Visual Studio 2017 年 1 で作成した新しい VSIX プロジェクトには、です。 現在の Visual Studio インストール ディレクトリを指す既定の設定で作成した csproj.user ファイル。 ただし場合 v2 VSIX 拡張機能を移行する場合は、可能性がありますする、。 csproj.user ファイルには、Visual Studio の以前のバージョンのインストール ディレクトリへの参照はが含まれます。 値の設定**デバッグ** > **開始アクション**拡張機能をデバッグしようとしたときに起動する適切な Visual Studio の実験用インスタンスを許可します。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>拡張機能が正しく (VSIX v3) としてビルドされることを確認します。

* VSIX プロジェクトをビルドします。
* 生成された VSIX を解凍します。
  * 既定では、VSIX ファイル生活がどれほど Bin/debug 内または [YourCustomExtension] .vsix として箱/リリースします。
  * .Vsix を簡単に内容を表示する .zip に変更します。
* 3 つのファイルの存在を確認します。
  * extension.vsixmanifest
  * manifest.json
  * catalog.json

## <a name="check-when-all-required-prerequisites-are-installed"></a>すべての必要な前提条件がインストールされている場合はチェック

VSIX と共にインストールされますが正常にコンピューターにインストールされているすべての必要な前提条件をテストします。

>**注:**任意の拡張機能をインストールする前にシャット ダウンしてください Visual Studio のすべてのインスタンス。

拡張機能をインストールしようとしてください。

* Visual Studio 2017 上

![Visual Studio 2017 で VSIX インストーラー](media/vsixinstaller-vs-2017.png)

* 省略可能: Visual Studio の以前のバージョンを確認します。
  * 旧バージョンとの互換性を証明します。
  * Visual Studio 2012、Visual Studio 2013、Visual Studio 2015 の機能する必要があります。
* 省略可能: VSIX インストーラーのバージョン チェックがバージョンの選択肢を提供することを確認します。
  * (インストールされている) 場合は、Visual Studio の以前のバージョンに含まれています。
  * Visual Studio 2017 が含まれます。

Visual Studio が開かれた最近場合は、次のように、ダイアログ ボックスを参照してください可能性があります。

![vs のプロセスを実行します。](media/vs-running-processes.png)

シャット ダウンにプロセスを待つか、手動でタスクを終了します。 一覧表示名、またはかっこで囲んで表示されている PID のプロセスが表示されます。

>**注:**これらのプロセスが自動的にシャット ダウンしない Visual Studio のインスタンスの実行中にします。 他のユーザーのものを含む、コンピューター上の Visual Studio のすべてのインスタンスをシャット ダウンしたし、再試行を続行することを確認します。

## <a name="check-when-missing-the-required-prerequisites"></a>必要な前提条件がない場合の確認します。

* 拡張機能をインストール、コンピューター上で Visual Studio 2017 ことはない CONTAIN (上記) の前提条件で定義されているすべてのコンポーネントしようとしてください。
* インストールが不足しているコンポーネント/秒を識別し、それらを一覧表示、VSIXInstaller の前提条件としてを確認してください。
* 注: 昇格は必要前提条件は、拡張機能と共にインストールする必要がある場合です。

![vsixinstaller 不足している前提条件](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>コンポーネントを決定します。

依存関係の検索、時に、1 つの依存関係が複数のコンポーネントをマップでしたが表示されます。 どの依存関係の前提条件として指定する必要がありますが、拡張機能に類似の機能を持つコンポーネントを選択することをお勧めし、も、ユーザーやを検討するコンポーネントの種類は、おそらくインストールされているを確認するか、考えないからインストールすることに注意します。 ビルドが必要な前提条件が、拡張機能を実行できる最小値のみを満たす方法で、追加の機能には、拡張機能がある特定のコンポーネントが検出されなかった場合は、休止することもお勧めします。

さらにガイダンスを提供するには、いくつかの一般的な拡張機能の種類とその推奨される前提条件を特定しました。

拡張機能の種類 | 表示名 | ID
--- | --- | ---
エディター | Visual Studio のコア エディター  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# および Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed Desktop Workload コア | Microsoft.VisualStudio.Component.ManagedDesktop.Core
デバッガー | Just-In-Time デバッガー | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>コンポーネントの Id を検索します。

Visual Studio 製品で並べ替えコンポーネントの一覧に[Visual Studio 2017 作業負荷とコンポーネントの Id](https://aka.ms/vs2017componentIDs)です。 マニフェストで前提条件となる id が、これらのコンポーネントの Id を使用します。

特定のバイナリ、ダウンロードがどのコンポーネントに含まれていることを確認していない場合は、[コンポーネント バイナリのマッピングのスプレッドシート]-> [](https://aka.ms/vs2017componentid-binaries)です。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Excel シートに 4 つの列がある:**コンポーネント名**、 **ComponentId**、**バージョン**、および**バイナリ/ファイル名**です。  特定のコンポーネントとバイナリを検索するフィルターを使用することができます。

について、すべての参照では、まずコア エディター (Microsoft.VisualStudio.Component.CoreEditor) コンポーネントであるを決定します。  少なくとも、コア エディターのコンポーネントをすべての拡張機能の前提条件として指定する必要があります。 コア エディターに含まれていないのは、残っている参照、追加のフィルター、**バイナリ/ファイル名** セクションをこれらの参照のサブセットのいずれかのコンポーネントを参照します。

次に例を示します。

* デバッガー拡張機能をした VSDebugEng.dll および VSDebug.dll への参照をプロジェクトにいる場合はクリックして [フィルター] ボタン、**バイナリ/ファイル名**ヘッダー。  "VSDebugEng.dll"を検索し、[ok] を選択します。  次に、フィルターのボタンをクリックして、**バイナリ/ファイル名**ヘッダーをもう一度して"VSDebug.dll"を検索します。  「Add 現在の選択項目をフィルター処理する」のチェック ボックスを選択し、[ok] を選択します。  なります、**コンポーネント名**ほとんどは、コンポーネントを検索する拡張機能の種類に関連します。 この例では、ジャスト イン タイムを選択したがデバッガーし、vsixmanifest に追加します。
* プロジェクトがデバッガー要素を処理する場合は、どのようなコンポーネントには、その名前でデバッガーが含まれているフィルターの検索ボックスに「デバッガー」を検索できます。

## <a name="specifying-a-visual-studio-2017-release"></a>Visual Studio 2017 リリースを指定します。

拡張機能は、Visual Studio 2017 の特定のバージョンを必要とする場合、15.3 でリリースされた機能に依存しているなどの VSIX にビルド番号を指定する必要があります**は InstallationTarget**です。 たとえば、15.3 のリリースでは、'15.0.26730.3' のビルド番号があります。 リリース ビルドの番号へのマッピングを確認できます[ここ](../install/visual-studio-build-numbers-and-release-dates.md)です。 リリース番号 '15.3' を使用してについては、正しく機能しません。

拡張機能 15.3 や以降では、宣言する場合、**は InstallationTarget バージョン**として [15.0.26730.3, 16.0)。

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```