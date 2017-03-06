---
title: "方法: Visual Studio 2017 を機能拡張プロジェクトの移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4f93b8c1db59dd8d8a407c82002240641be43018
ms.openlocfilehash: 1f9248442357c4447703ac6d6dac8a27934904e8
ms.lasthandoff: 03/01/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>方法: 機能拡張プロジェクトを Visual Studio 2017 に移行

>**注:**このドキュメントは暫定版であり、Visual Studio 2017 RC リリースに基づいています。

このドキュメントでは、Visual Studio 2017 に機能拡張プロジェクトをアップグレードする方法について説明します。 プロジェクト ファイルを更新する方法を説明するだけでなく、新しいバージョン 3 VSIX マニフェスト形式 (VSIX v3) に拡張機能マニフェストのバージョン 2 (VSIX v2) からアップグレードする方法も説明します。

## <a name="install-visual-studio-2017-rc-with-required-workloads"></a>必要なワークロードで Visual Studio 2017 RC をインストールします。

環境に、次のワークロードを確認します。

* .NET デスクトップ開発
* Visual Studio 拡張機能の開発

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017 で開いている VSIX ソリューション

すべての VSIX プロジェクトには、Visual Studio 2017 にメジャー バージョン一方向のアップグレードが必要です。

プロジェクト ファイル (たとえば *.csproj) が更新されます。

* MinimumVisualStudioVersion - 15.0 に設定されています
* OldToolsVersion (場合は既に存在する)-14.0 に設定されています

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.VSSDK.BuildTools NuGet パッケージを更新します。

>**注:**ソリューションが Microsoft.VSSDK.BuildTools NuGet パッケージを参照していない場合は、この手順をスキップすることができます。

新しい VSIX v3 で拡張機能を構築するために (バージョン 3) の形式で、ソリューションは新しい VSSDK ビルド ツールを使用してビルドする必要があります。 これは Visual Studio の 2017 RC でインストールされますが、NuGet 経由で以前のバージョンへの参照を VSIX v2 の拡張機能を保持することがあります。 その場合は、ソリューションの Microsoft.VSSDK.BuildTools NuGet パッケージの更新を手動でインストールする必要があります。 RC のリリース時に、このパッケージを「プレリリース」状態になります。

NuGet を更新するには、Microsoft.VSSDK.BuildTools を参照します。

* ソリューションを右クリックし、選択**ソリューションの NuGet パッケージを管理しています.**
* 移動し、**更新** タブをクリックします。
* チェック ボックスをオン**プレリリースを含める**します。
* Microsoft.VSSDK.BuildTools (最新バージョン) を選択します。
* キーを押して**更新**します。

![VSSDK ビルド ツール](media/vssdk-build-tools.png)

>**注:**スクリーン ショット、BuildTools の別のバージョンを示しています。 RC 版を選択してください。

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX 拡張機能マニフェストを変更をします。

Visual Studio のユーザーのインストールの拡張機能を実行するために必要なすべてのアセンブリであることを確認するには、拡張機能マニフェスト ファイルのすべての前提条件となるコンポーネントまたはパッケージを指定します。 ユーザーが、拡張機能をインストールしようとすると、すべての前提条件がインストールされていないかどうか、VSIXInstaller が確認されます。 一部が見つからない場合は、ユーザーは拡張機能のインストール プロセスの一環として必要なコンポーネントをインストールするように求められます。

>**注:**には、少なくともすべての拡張機能は、前提条件として Visual Studio の中核となるエディター コンポーネントを指定する必要があります。

* (通常、source.extension.vsixmanifest と呼ばれます)、拡張機能マニフェスト ファイルを編集します。
* ように`InstallationTarget`15.0 が含まれています。
* (次の例で示すように) とは、必要なインストール前提条件を追加します。
  * インストールの前提条件コンポーネントの Id のみを指定することをお勧めします。
  * このドキュメントの最後のセクションを参照してください[コンポーネントの Id を識別する方法について](#finding-component-ids)します。

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>方法: デザイナーを使用して VSIX 拡張機能マニフェストを変更する

マニフェストの XML を直接編集するには、代わりに、新しい使える**の前提条件** タブで、マニフェスト デザイナー、前提条件を選択して、XML が更新されます。

>**注:**マニフェスト デザイナーはできるだけ現在の Visual Studio インスタンスにインストールされているコンポーネント (ワークロードまたはパッケージ) を選択します。 ワークロード、パッケージ、または現在インストールされていないコンポーネントの前提条件を追加する必要がある場合は、マニフェスト XML を直接編集します。

* [デザイン] source.extension.vsixmanifest ファイルを開きます。
* 選択**の前提条件** タブをクリックし、キーを押して**新規** ボタンをクリックします。

  ![VSIX マニフェスト デザイナー](media/vsix-manifest-designer.png)

* **追加新しい前提条件となる**ウィンドウが開きます。

  ![vsix の前提条件を追加します。](media/add-vsix-prerequisite.png)

* ドロップダウンをクリックして**名前**し、必要な前提条件を選択します。
* 必要な場合は、バージョンを更新します。

  >注: バージョン フィールドが、範囲の最大またがりメモリ割り当て (ただしを除く) で、現在インストールされているコンポーネントのバージョンでは、あらかじめ設定されているとするコンポーネントの次のメジャー バージョン。

  ![roslyn の前提条件を追加します。](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>プレビュー 4 または 5 のプレビューから移行する場合

* 置換`SetupDependencies`と`Prerequisites`の要素を移動して、`Installer`要素。 `Prerequisites`直接の内側は今すぐ、`PackageManifest`要素。
* [省略可能]削除、`GenerateVsixV3`要素。 (これが 5 のプレビューでのみ必要です。)`GenerateVsixV3`プレビュー 5 を超えるバージョンでの要素は無視されます。

## <a name="update-debug-settings-for-project"></a>プロジェクトのデバッグ設定を更新します。

Visual Studio の実験用インスタンスで拡張機能をデバッグする場合は、以下のことを確認してプロジェクト設定**デバッグ** > **[開始動作]**が、**外部プログラムの開始:**値は、Visual Studio 2017 インストールの devenv.exe のファイルに設定します。

ようになります。

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![外部プログラムを開始します。](media/start-external-program.png)

>**注:**デバッグの開始アクションは一般に格納します。 csproj.user ファイルです。 このファイルは、.gitignore ファイルに含まれる通常し、そのため、通常で保存されていないソース管理にコミットする場合は、他のプロジェクト ファイル。 そのため、ソース管理から新しいソリューションを取得した場合、可能性の高いプロジェクトには 開始動作の設定値はありませんが。 Visual Studio 2017 年 1 で作成された新しい VSIX プロジェクトがある、。 現在の Visual Studio インストール ディレクトリを指す既定の設定で作成した csproj.user ファイルです。 しかし VSIX v2 の拡張機能を移行する場合は通常を。 csproj.user ファイルは、Visual Studio の以前のバージョンのインストール ディレクトリへの参照を含まれます。 値の設定**デバッグ** > **[開始動作]**拡張機能をデバッグしようとするときに起動する適切な Visual Studio の実験用インスタンスを許可します。

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>拡張機能が正しく (VSIX v3) としてビルドされることを確認します。

* VSIX プロジェクトをビルドします。
* 生成される VSIX に解凍します。
  * 既定では Bin/debug 内 VSIX ファイル生活がどれほどまたは Bin/release [YourCustomExtension] .vsix として。
  * .Vsix を簡単に内容を表示する .zip に変更します。
* 3 つのファイルの存在を確認します。
  * extension.vsixmanifest
  * manifest.json
  * catalog.json

## <a name="check-when-all-required-prerequisites-are-installed"></a>すべての必須コンポーネントがインストールされている場合はチェック

VSIX は、正常にインストールされますマシンにインストールされているすべての必要な前提条件の下をテストします。

>**注:**任意の拡張機能をインストールする前にしてください。 は、シャット ダウンは、Visual Studio のすべてのインスタンス。

拡張機能をインストールしようとします。

* Visual Studio 2017 RC に

![VSIX インストーラーは Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* 省略可能: Visual Studio の以前のバージョンを確認します。
  * 下位互換性を証明します。
  * Visual Studio 2012、Visual Studio 2013、Visual Studio 2015 の動作する必要があります。
* 省略可能: VSIX インストーラーのバージョン チェックがバージョンの選択肢を提供することを確認します。
  * (インストールされている) 場合は、Visual Studio の以前のバージョンに含まれています。
  * Visual Studio 2017 RC が含まれます。

Visual Studio が開かれた最近場合は、次のようなダイアログ ボックスを表示する可能性があります。

![vs のプロセスを実行します。](media/vs-running-processes.png)

プロセスのシャット ダウンを待機するか、手動でタスクを終了します。 表示されている名前などのかっこに示されている PID プロセスが表示されます。

>**注:**これらのプロセスが自動的にシャット ダウンしない Visual Studio のインスタンスの実行中にします。 – 他のユーザーからも含め、マシンでの Visual Studio のすべてのインスタンスをシャット ダウンしたし、再試行し続けることを確認します。

## <a name="check-when-missing-the-required-prerequisites"></a>必要な前提条件が欠けている場合にチェック

* 拡張機能をインストール、コンピューターに Visual Studio 2017 rc ことはない CONTAIN (上記) の前提条件で定義されているすべてのコンポーネントしようとしてください。
* インストールが不足しているコンポーネント/秒を識別して、それらが、VSIXInstaller の前提条件として一覧表示を確認してください。
* 注: 昇格が必要に前提条件を拡張機能と共にインストールされている必要があります。

![vsixinstaller 前提条件がないです。](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>コンポーネントを決定します。

検索する場合、依存関係を複数のコンポーネントを&1; つの依存関係をマッピングできますが表示されます。 どの依存関係を確認するを拡張機能と同様の機能を持つコンポーネントを選択しも、ユーザーとコンポーネントの種類は考慮してください、おそらくインストールされていることをお勧めの前提条件として指定する必要がありますか、インストールしないことに注意します。 ビルドが必要な前提条件が、拡張機能を実行すると、最小値のみを満たす方法で、追加の機能には、拡張機能がある特定のコンポーネントが検出されなかった場合に非アクティブにすることもお勧めします。

さらにガイダンスを提供するには、いくつかの一般的な拡張機能の種類とその推奨される前提条件を確認しています。

拡張機能の種類 | 表示名 |    ID
--- | --- | ---
エディター | Visual Studio コア エディター    | Microsoft.VisualStudio.CoreEditor
Roslyn | C# および Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | マネージ デスクトップ ワークロード コア | Microsoft.VisualStudio.Component.ManagedDesktop.Core
デバッガー | ジャストイン タイム デバッガー | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>コンポーネントの Id を検索します。

Visual Studio 製品で並べ替えコンポーネントの一覧は、「 [Visual Studio 2017 ワークロードとコンポーネント Id](https://aka.ms/vs2017componentIDs)します。 マニフェストで前提条件となる id が、これらのコンポーネント Id を使用します。

どのコンポーネントに特定のバイナリ、ダウンロードが含まれていることを確認していない場合は、 [-> バイナリのマッピングのスプレッドシート コンポーネント](https://aka.ms/vs2017componentid-binaries)します。

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Excel シートに&4; つの列がある:**コンポーネント名**、 **ComponentId**、**バージョン**、および**バイナリ/ファイル名**します。  フィルターを使用して、特定のコンポーネントとバイナリを検索することができます。

すべての参照の場合は、まずコア エディター (Microsoft.VisualStudio.Component.CoreEditor) コンポーネントでられるかを特定します。  少なくとも、中核となるコンポーネントであるエディター、すべての拡張機能の前提条件として指定する必要があります。 内のフィルターを追加、参照のままになっているコア エディターに含まれていない、**バイナリ/ファイル名**セクションがそれらの参照のサブセットのいずれかのコンポーネントを検索します。

次に例を示します。

* デバッガー拡張機能を用意し、プロジェクトが VSDebugEng.dll および VSDebug.dll への参照を確認すると場合、は、[フィルター] ボタンをクリックして、**バイナリ/ファイル名**ヘッダー。  "VSDebugEng.dll"を検索し、[ok] を選択します。  次に [フィルター] ボタンをクリックして、**バイナリ/ファイル名**ヘッダーをもう一度して"VSDebug.dll"を検索します。  「追加現在の選択項目をフィルター処理する」チェック ボックスを選択し、[ok] を選択します。  ここで探す、**コンポーネント名**が最も多くのコンポーネントを検索する拡張機能の種類に関連します。 この例では、ジャスト イン タイムを選択したデバッガーし、vsixmanifest に追加します。
* デバッガーの要素を持つプロジェクトを取り扱うことがわかっている場合は、どのようなコンポーネントには、デバッガーがその名前が含まれているフィルターの検索ボックスに「デバッガー」を検索できます。

