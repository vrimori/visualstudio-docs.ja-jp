---
title: 拡張機能のラウンドト リップする方法
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 809ca83d164b4cb589f19438b1fc5672cc1b4b8e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880953"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>方法: Visual Studio 2017 と Visual Studio 2015 と互換性のある拡張機能を作成します。

このドキュメントでは、拡張機能プロジェクトを Visual Studio 2015 と Visual Studio 2017 間でラウンドトリップさせる方法について説明します。 このアップグレードを完了すると、Visual Studio 2015 と Visual Studio 2017 の両方でプロジェクトを開いてビルド、インストール、および実行できるようになります。 参考として、Visual Studio 2015 と Visual Studio 2017 の間でラウンドト リップできるいくつかの拡張で見つかる、 [VS SDK 拡張機能サンプル](https://github.com/Microsoft/VSSDK-Extensibility-Samples)します。

Visual Studio 2017 でビルドが Visual Studio 2015 と Visual Studio 2017 の両方で VSIX を出力する場合を参照し、[拡張機能の移行のドキュメント](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)します。

> [!NOTE]
> Visual Studio のバージョン間の変更、により、1 つのバージョンで動作していたものは、別の機能しません。 アクセスしようとしている機能は、両方のバージョンで使用または拡張機能は必要があります。 予期しない結果。

VSIX をラウンドトリップするためにこのドキュメントで実行する手順の概要を以下に示します。

1. 適切な NuGet パッケージをインポートします。
2. 拡張機能マニフェストを更新します。
    * インストールの対象
    * 必須コンポーネント
3. CSProj を更新します。
    * `<MinimumVisualStudioVersion>` を更新します。
    * `<VsixType>` プロパティを追加します。
    * デバッグ プロパティ `($DevEnvDir)` を 3 回追加します。
    * ビルド ツールをインポートするための条件と対象を追加します。

4. ビルドとテストを行います。

## <a name="environment-setup"></a>環境のセットアップ

このドキュメントは、コンピューターに以下をインストール済みであることを前提としています。

* VS SDK がインストールされた Visual Studio 2015
* 拡張機能ワークロードがインストールされた Visual Studio 2017

## <a name="recommended-approach"></a>推奨されるアプローチ

このアップグレードは、Visual Studio 2017 ではなく、Visual Studio 2015 で開始することを強くお勧めします。 Visual Studio 2015 で開発を行う主な利点は、Visual Studio 2015 で利用できないアセンブリの参照を確実に排除できるという点です。 Visual Studio 2017 で開発を行うと、Visual Studio 2017 にのみ存在するアセンブリへの依存関係を導入してしまうリスクがあります。

## <a name="ensure-there-is-no-reference-to-projectjson"></a>project.json への参照を確実に排除する

このドキュメントの後半に条件付きインポート ステートメントを挿入、**.csproj*ファイル。  これで、NuGet 参照が格納されている場合は機能しません*project.json*します。 そのため、すべての NuGet 参照への移動お勧め、 *packages.config*ファイル。
プロジェクトが含まれている場合、 *project.json*ファイル。

* 内の参照をメモに取ります*project.json*します。
* **ソリューション エクスプ ローラー**、削除、 *project.json*プロジェクトからのファイル。 これにより、削除、 *project.json*ファイルを開き、プロジェクトから削除されます。
* NuGet 参照をプロジェクトに再度追加します。
    * 右クリックし、**ソリューション**選択**ソリューションの NuGet パッケージの管理**します。
    * Visual Studio が自動的に作成、 *packages.config*ファイル。

> [!NOTE]
> プロジェクトに EnvDTE パッケージが含まれている場合は、右クリックして追加する必要がある**参照**選択**参照の追加**適切な参照を追加するとします。  NuGet パッケージを使用すると、プロジェクトのビルドを試みたときにエラーが発生する可能性があります。

## <a name="add-appropriate-build-tools"></a>適切なビルド ツールを追加します。

ビルドとデバッグを正しく実行できるビルド ツールを確実に追加する必要があります。 そのために、Microsoft は Microsoft.VisualStudio.Sdk.BuildTasks というアセンブリを作成しました。

Visual Studio 2015 と 2017 の両方で VSIXv3 をビルドして展開するには、次の NuGet パッケージが必要となります。

Version | ビルド ツール
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

次の手順に従います。

* NuGet パッケージ Microsoft.VisualStudio.Sdk.BuildTasks.14.0 をプロジェクトに追加します。
* プロジェクトに Microsoft.VSSDK.BuildTools が含まれていない場合は、追加します。
* Microsoft.VSSDK.BuildTools のバージョンが 15.x 以上であることを確認します。

## <a name="update-extension-manifest"></a>拡張機能マニフェストを更新します。

### <a name="1-installation-targets"></a>1.インストールの対象

VSIX をビルドする対象のバージョンを Visual Studio に指示する必要があります。  通常、これらの参照は、バージョン 14.0 (Visual Studio 2015) またはバージョン 15.0 (Visual Studio 2017) への参照です。  ここでは、両方に対応する拡張機能をインストールする VSIX をビルドしたいので、両方のバージョンを対象にする必要があります。  14.0 より前のバージョンで VSIX をビルドおよびインストールしたい場合は、前のバージョン番号を設定すれば可能です。ただし、10.0 以前のバージョンはサポートされていません。

* 開く、 *source.extension.vsixmanifest* Visual Studio でのファイル。
* **[Install Targets]\(インストールの対象)\** タブを開きます。
* **[バージョン範囲]** を [14.0, 16.0) 変更します。  '[' は、14.0 とそれより前のすべてのバージョンを含めるよう Visual Studio に指示します。  ')' は、15.0 までのすべてのバージョンを含めるが、バージョン 16.0 は含めないように Visual Studio に指示します。
* すべての変更を保存し、Visual Studio のすべてのインスタンスを閉じます。

![インストールの対象の画像](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2.必須コンポーネントを追加、 *extension.vsixmanifest*ファイル

必須コンポーネントは、Visual Studio 2017 からの新しい機能です。  ここでは、必須コンポーネントとして Visual Studio のコア エディターが必要です。 Visual Studio 2015 の VSIX デザイナーでは新しい `Prerequisites` セクションを処理しないため、XML コードでこの部分を 手動で編集する必要があります。  または、Visual Studio 2017 を開き、更新されたマニフェスト デザイナーを使用して必須コンポーネントを挿入することもできます。

この操作を手動で行うには、次の手順に従います。

* エクスプローラーでプロジェクト ディレクトリに移動します。
* 開く、 *extension.vsixmanifest*ファイルをテキスト エディターでします。
* 次のタグを追加します。

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* ファイルを保存して閉じます。

> [!NOTE]
> これを実現する Visual Studio 2017 の VSIX デザイナーで選択した場合は、Visual Studio 2017 のすべてのバージョンと互換性があることを確認する前提条件のバージョンを手動で編集する必要があります。  なぜならば、デザイナーは最小バージョンをVisual Studio の現在のバージョンとして挿入するからです (例: 15.0.26208.0)。  しかし、他のユーザーがそれより前のバージョンを使用している可能性があるため、これを 15.0 に編集する必要があります。

この時点で、マニフェスト ファイルは次のようになります。

![必須コンポーネントの例](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>プロジェクト ファイル (myproject.csproj) を変更する

この手順を実行する間、変更した .csproj への参照を開いておくことを強くお勧めします。  [ここ](https://github.com/Microsoft/VSSDK-Extensibility-Samples)でいくつかの例を入手できます。  拡張機能のサンプルを選択し、検索、 *.csproj*参照のファイルを開き、次の手順を実行します。

* プロジェクト ディレクトリに移動します**ファイル エクスプ ローラー**します。
* 開く、 *myproject.csproj*ファイルをテキスト エディターでします。

### <a name="1-update-the-minimumvisualstudioversion"></a>1.MinimumVisualStudioVersion を更新する

* Visual Studio の最小バージョンを `$(VisualStudioVersion)` に設定し、その条件付きステートメントを追加します。  以下のタグが存在しない場合は、追加します。  タグが次のように設定されていることを確認してください。

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2.VsixType プロパティを追加します。

* プロパティ グループに次のタグ `<VsixType>v3</VsixType>` を追加します。

> [!NOTE]
> これを追加することをお勧めの下、`<OutputType></OutputType>`タグ。

### <a name="3-add-the-debugging-properties"></a>3.デバッグ プロパティを追加する

* 次のプロパティ グループを追加します。

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* 次のコード例からのすべてのインスタンスを削除、 *.csproj*ファイルおよび *. csproj.user*ファイル。

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4.ビルド ツールのインポートに条件を追加する

* Microsoft.VSSDK.BuildTools 参照を含んでいる `<import>` タグに、その他の条件付きステートメントを追加します。  挿入`'$(VisualStudioVersion)' != '14.0' And`条件文の先頭にあります。  これらのステートメントは、csproj ファイルのヘッダーとフッターに表示されます。

例:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Microsoft.VisualStudio.Sdk.BuildTasks.14.0 を含んでいる `<import>` タグに、その他の条件付きステートメントを追加します。 挿入`'$(VisualStudioVersion)' == '14.0' And`条件文の先頭にあります。 これらのステートメントは、csproj ファイルのヘッダーとフッターに表示されます。

例:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Microsoft.VSSDK.BuildTools 参照を含んでいる `<Error>` タグに、その他の条件付きステートメントを追加します。  これを行うには、条件付きステートメントの前に `'$(VisualStudioVersion)' != '14.0' And` を挿入します。 これらのステートメントは、csproj ファイルのフッターに表示されます。

例:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Microsoft.VisualStudio.Sdk.BuildTasks.14.0 を含んでいる `<Error>` タグに、その他の条件付きステートメントを追加します。  挿入`'$(VisualStudioVersion)' == '14.0' And`条件文の先頭にあります。 これらのステートメントは、csproj ファイルのフッターに表示されます。

例:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* csproj ファイルを保存して閉じます。

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 と Visual Studio 2017 で拡張機能のインストールをテストする

この時点で、プロジェクトは Visual Studio 2015 と Visual Studio 2017 の両方にインストール可能な VSIXv3 をビルドできる状態になっているはずです。

* Visual Studio 2015 でプロジェクトを開きます。
* プロジェクトをビルドし、確認、VSIX が正しくビルド出力します。
* プロジェクト ディレクトリに移動します。
* 開く、 *\bin\Debug* フォルダー。
* VSIX ファイルをダブルクリックし、Visual Studio 2015 と Visual Studio 2017 で拡張機能をインストールします。
* 拡張機能を表示できることを確認**ツール** > **拡張機能と更新**で、**インストール済み**セクション。
* それが動作するかを確認する拡張機能の実行/使用しようとします。

![VSIX を検索します。](media/finding-a-VSIX-example.png)

> [!NOTE]
> メッセージで、プロジェクトがハングした場合**ファイルを開く**、強制的にシャット ダウンは、Visual Studio、プロジェクト ディレクトリに移動し、非表示のフォルダーを表示および削除、 *.vs*フォルダー。