---
title: '方法: Visual Studio 2017 の機能拡張プロジェクトの移行 |Microsoft Docs'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3726ee6995e770d89e5916a922c0546439c3ba14
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953511"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>方法: 機能拡張プロジェクトを Visual Studio 2017 に移行します。

このドキュメントでは、機能拡張プロジェクトを Visual Studio 2017 にアップグレードする方法について説明します。 プロジェクト ファイルを更新する方法を記述するだけでなく、新しいバージョン 3 VSIX マニフェスト形式 (VSIX v3) に拡張機能マニフェストのバージョン 2 (v2) VSIX からアップグレードする方法も説明します。

## <a name="install-visual-studio-2017-with-required-workloads"></a>必要なワークロードでの Visual Studio 2017 をインストールします。

環境に、次のワークロードを確認します。

* .NET デスクトップ開発
* Visual Studio 拡張機能の開発

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017 で開いている VSIX ソリューション

すべての VSIX プロジェクトには、Visual Studio 2017 へのメジャー バージョンの一方向アップグレードが必要です。

プロジェクト ファイル (たとえば **.csproj*) が更新されます。

* MinimumVisualStudioVersion - を 15.0 に設定するようになりました
* OldToolsVersion (場合以前存在)-14.0 に設定されました

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.VSSDK.BuildTools NuGet パッケージを更新します。

>**注:** ソリューションは、Microsoft.VSSDK.BuildTools NuGet パッケージを参照していない場合は、この手順をスキップすることができます。

新しい VSIX v3 で拡張機能をビルドするには (バージョン 3) の形式で、ソリューションは新しい VSSDK のビルド ツールで構築する必要があります。 これは、Visual Studio 2017 でインストールされますが、NuGet を使用して以前のバージョンへの参照を VSIX v2 の拡張機能を保持する可能性があります。 そうである場合は、ソリューションに Microsoft.VSSDK.BuildTools NuGet パッケージの更新プログラムを手動でインストールする必要があります。

Microsoft.VSSDK.BuildTools NuGet 参照を更新するには。

* ソリューションを右クリックし、選択**ソリューションの NuGet パッケージの管理**します。
* 移動し、**更新**タブ。
* 選択**Microsoft.VSSDK.BuildTools (最新バージョン)** します。
* キーを押して**Update**します。

![VSSDK のビルド ツール](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX 拡張機能マニフェストを変更をします。

Visual Studio のユーザーのインストールは、拡張機能を実行するために必要なすべてのアセンブリを持つようにするため、拡張機能マニフェスト ファイルで、すべての前提条件コンポーネントまたはパッケージを指定します。 ユーザーが拡張機能をインストールしようとすると、すべての前提条件がインストールされているかどうかの VSIXInstaller が確認されます。 いくつかが存在しない場合は、拡張機能のインストール プロセスの一環として、見つからないコンポーネントをインストールするユーザーにメッセージが表示します。

>**注:** 少なくともすべての拡張機能は、前提条件として、Visual Studio コア エディター コンポーネントを指定する必要があります。

* 拡張機能マニフェスト ファイルを編集 (通称、 *source.extension.vsixmanifest*)。
* 確認`InstallationTarget`15.0 が含まれています。
* (次の例で示す) のように、必要なインストール前提条件を追加します。
  * インストールの前提条件のコンポーネント Id のみを指定することをお勧めします。
  * このドキュメントの最後のセクションを参照してください。[コンポーネント Id を識別する方法について](#find-component-ids)します。

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>オプション:デザイナーを使用して、VSIX 拡張機能マニフェストを変更します。

マニフェストの XML を直接編集する代わりに、マニフェスト デザイナーにある**新しい前提条件**を使用して、前提条件を選択し、XML を更新することができます。

>**注:** マニフェスト デザイナーを使用して、現在の Visual Studio インスタンスにインストールされているコンポーネント (ワークロードやパッケージ) を選択することはのみ。 ワークロード、パッケージ、または現在インストールされていないコンポーネントの前提条件を追加する必要がある場合は、マニフェスト XML を直接編集します。

* 開いている*source.extension.vsixmanifest [デザイン]* ファイル。
* 選択**の前提条件**タブ キーを押します**新規**ボタンをクリックします。

  ![VSIX マニフェスト デザイナー](media/vsix-manifest-designer.png)

* **新しい前提条件の追加**ウィンドウが開きます。

  ![vsix の前提条件を追加します。](media/add-vsix-prerequisite.png)

* **[名前]** のドロップダウンをクリックして、必要な前提条件を選択します。
* 必要な場合は、バージョンを更新します。

  >メモ:バージョン フィールドは、範囲の最大またがりメモリ割り当て (ただしを除く) で、現在インストールされているコンポーネントのバージョンでは、あらかじめ設定されているとするコンポーネントの次のメジャー バージョン。

  ![roslyn の前提条件を追加します。](media/add-roslyn-prerequisite.png)

* **[OK]** を押します。

## <a name="update-debug-settings-for-the-project"></a>プロジェクトのデバッグ設定を更新します。

Visual Studio の実験用インスタンスで拡張機能をデバッグする場合、以下のことを確認のプロジェクト設定**デバッグ** > **開始アクション**が、**外部開始プログラム:** 値に設定、 *devenv.exe* Visual Studio 2017 インストールのファイル。

ようになります。*C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![外部プログラムを開始します。](media/start-external-program.png)

>**注:** デバッグの開始操作が通常に格納されている、 *. csproj.user*ファイル。 このファイルに通常含まれて、 *.gitignore*ファイルを開き、そのため、通常で保存されていない他のプロジェクト ファイルをソース管理にコミットされたときにします。 そのため、ソース管理から新しいソリューションを取得しましたをプロジェクトには開始動作の設定値はありませんが高くなります。 Visual Studio 2017 で作成した新しい VSIX プロジェクトには、 *. csproj.user*ファイルの現在の Visual Studio インストール ディレクトリを指す既定値で作成します。 ただし場合 v2 VSIX 拡張機能を移行する可能性がありますが、 *. csproj.user*ファイルは、Visual Studio の以前のバージョンのインストール ディレクトリへの参照が格納されます。 値の設定**デバッグ** > **開始アクション**拡張機能をデバッグしようとするときに起動する正しい Visual Studio の実験用インスタンスを許可します。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>拡張機能が正しく (VSIX v3) としてビルドされるかを確認します。

* VSIX プロジェクトをビルドします。
* 生成した VSIX を解凍します。
  * 既定では、VSIX ファイルの存在の内部*Bin/debug*または*Bin/release*として *[YourCustomExtension] .vsix*します。
  * 名前を変更 *.vsix*に *.zip*を簡単に内容を表示します。
* 3 つのファイルの存在を確認します。
  * *extension.vsixmanifest*
  * *manifest.json*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>すべての必要な前提条件がインストールされているときに確認します。

VSIX が正常にインストール、マシンに必要なすべての前提条件のインストールをテストします。

>**注:** 任意の拡張機能をインストールする前に、Visual Studio のすべてのインスタンスをシャット ダウンしてください。

拡張機能をインストールしようとしてください。

* Visual Studio 2017 で

![Visual Studio 2017 の VSIX インストーラー](media/vsixinstaller-vs-2017.png)

* 省略可能:Visual Studio の以前のバージョンを確認します。
  * 旧バージョンとの互換性を証明します。
  * Visual Studio 2012、Visual Studio 2013、Visual Studio 2015 の機能する必要があります。
* 省略可能:VSIX インストーラーのバージョン チェックがバージョンの選択肢を提供することを確認します。
  * (インストールされている) 場合は、Visual Studio の以前のバージョンが含まれています。
  * Visual Studio 2017 が含まれています。

Visual Studio が開かれた最近場合は、このようなダイアログ ボックスを表示する可能性があります。

![vs のプロセスを実行します。](media/vs-running-processes.png)

プロセスがシャット ダウンするまで待つか、タスクを手動で終了します。 表示されている名、またはかっこで囲まれた表示 PID のプロセスが表示されます。

>**注:** これらのプロセスに自動的にシャット ダウンしない Visual Studio のインスタンスの実行中にします。 他のユーザーのものを含むのコンピューター上の Visual Studio のすべてのインスタンスをシャット ダウンしたし、再試行を続行することを確認します。

## <a name="check-when-missing-the-required-prerequisites"></a>必要な前提条件が不足しているときに確認します。

* 拡張機能をインストール、マシンで Visual Studio 2017 ことはない CONTAIN (上記) の前提条件で定義されているすべてのコンポーネントしようとしてください。
* インストールが不足しているコンポーネント/秒を識別して、それら、VSIXInstaller で前提条件として一覧表示を確認します。
* メモ:前提条件は、拡張機能と共にインストールする必要がある場合、昇格が必要になります。

![vsixinstaller 前提条件がありません。](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>コンポーネントを決定します。

依存関係を調べるときに、1 つの依存関係が複数のコンポーネントにマッピングできることが表示されます。 どの依存関係は、の前提条件として指定する必要がありますが、拡張機能のような機能を備えたコンポーネントを選択することをお勧めし、も、ユーザーとコンポーネントの種類を考慮するインストール ファイルまたはほとんどの場合を判断するまたはインストールに注意してください。 ビルドが必要な前提条件が、拡張機能を実行すると、最小値のみを満たす方法で、追加の機能には、拡張機能がある特定のコンポーネントが検出されなかった場合は、休止することも推奨されます。

さらにガイダンスを提供するには、いくつかの一般的な拡張機能の種類と推奨される前提条件を特定しました。

拡張機能の種類 | 表示名 | ID
--- | --- | ---
エディター | Visual Studio のコア エディター  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# および Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Managed Desktop Workload コア | Microsoft.VisualStudio.Component.ManagedDesktop.Core
デバッガー | Just-In-Time デバッガー | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>コンポーネント Id を検索します。

Visual Studio 製品ごとに並べ替えコンポーネントの一覧は、「 [Visual Studio 2017 のワークロードとコンポーネント Id](https://aka.ms/vs2017componentIDs)します。 マニフェストでは、前提条件となる Id には、これらのコンポーネント Id を使用します。

どのコンポーネントには、特定のバイナリが含まれていますが不明な場合は、ダウンロード、[コンポーネント バイナリ マッピング スプレッドシート](https://aka.ms/vs2017componentid-binaries) します。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Excel シートには、4 つの列があります。**コンポーネント名**、 **ComponentId**、**バージョン**、および**バイナリ ファイル名/** します。  特定のコンポーネントおよびバイナリを検索するフィルターを使用できます。

すべての参照のため最初コア エディター (Microsoft.VisualStudio.Component.CoreEditor) コンポーネントはどれを確認します。  少なくとも、コア エディター コンポーネントをすべての拡張機能の前提条件として指定する必要があります。 内のフィルターを追加、参照のままになっているのコア エディターが含まれていない、**バイナリ/ファイル名**セクションにこれらの参照のサブセットのいずれかのコンポーネントを検索します。

次に例を示します。

* プロジェクトを参照していることを理解しているデバッガー拡張機能がある場合*VSDebugEng.dll*と*VSDebug.dll*、[フィルター] ボタンをクリックして、**バイナリ/ファイル名**ヘッダー。  "VSDebugEng.dll"を検索して選択*OK*します。  次のフィルター ボタンをクリックして、**バイナリ/ファイル名**ヘッダーをもう一度と"VSDebug.dll"を検索します。  チェック ボックスをオン**をフィルター処理の現在の選択を追加する**選択と**OK**。  なります。、**コンポーネント名**ほとんどは、コンポーネントを検索する拡張機能の種類に関連します。 この例では、Just ポイントイン タイムを選択したデバッガーし、vsixmanifest に追加します。
* プロジェクトがデバッガー要素で処理される場合は、どのようなコンポーネントには、その名前でデバッガーが含まれている、フィルター検索ボックスに「デバッガー」を検索できます。

## <a name="specify-a-visual-studio-2017-release"></a>Visual Studio 2017 リリースを指定します。

拡張機能には、特定のバージョンの Visual Studio 2017 が必要とする場合など、15.3 でリリースされた機能に依存、VSIX のビルド番号を指定する必要があります**InstallationTarget**します。 たとえば、15.3 のリリースでは、'15.0.26730.3' のビルド番号があります。 ビルド番号のリリースのマッピングを確認できます[ここ](../install/visual-studio-build-numbers-and-release-dates.md)します。 リリース番号 '15.3' の使用については、正しく機能しません。

拡張機能が 15.3 が必要ですか、以降では、宣言する場合、 **InstallationTarget バージョン**として [15.0.26730.3, 16.0)。

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
