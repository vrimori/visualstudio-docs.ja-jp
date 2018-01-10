---
title: "方法: Visual Studio の拡張機能をラウンドト リップ |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
caps.latest.revision: "1"
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.workload: willbrown
ms.openlocfilehash: b51673daa7a8c3526ad7de7f7cfdeac6a91d3b4b
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>方法: Visual Studio 2017 と Visual Studio 2015 と互換性のある拡張機能も作成

このドキュメントでは、Visual Studio 2015 と Visual Studio 2017 間のラウンド トリップ機能拡張プロジェクトを作成する方法について説明します。 このアップグレードを完了すると、プロジェクトは開く、ビルド、インストール、および Visual Studio 2015 と Visual Studio 2017 の両方で実行することになります。  Visual Studio 2015 と Visual Studio 2017 間のラウンドト リップできる一部の拡張機能の検出された、参照として[ここ](https://github.com/Microsoft/VSSDK-Extensibility-Samples)Microsoft の拡張機能の例でします。

Visual Studio 2017 で構築されていますが、出力を Visual Studio 2015 と Visual Studio 2017 の両方で実行する VSIX するだけの場合を参照し、[拡張機能の移行のドキュメント](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)です。

>**注:**が変更されたのため Visual Studio のバージョン間で、1 つのバージョンで正常に実行されるものは機能しません別です。 確認しますアクセスしようとしている機能は、両方のバージョンで使用できる、拡張機能には予期しない結果。

次に、VSIX をラウンドト リップさせるには、このドキュメントで完了する手順の概要を示します。

1. 正しい NuGet パッケージをインポートします。
2. 拡張機能マニフェストを更新します。
    * インストール先
    * 必須コンポーネント
3. CSProj を更新します。
    * 更新`<MinimumVisualStudioVersion>`です。
    * 追加、`<VsixType>`プロパティです。
    * デバッグのプロパティを追加`($DevEnvDir)`3 回です。
    * ビルド ツールとターゲットをインポートするための条件を追加します。

4. ビルドし、テスト

## <a name="environment-setup"></a>環境の設定

このドキュメントでは、コンピューターにインストールされている、次があることを前提としています。

* インストールされている VS SDK と visual Studio 2015
* インストールされている機能拡張のワークロードでの visual Studio 2017

## <a name="recommended-approach"></a>推奨される方法

Visual Studio 2017 ではなく、Visual Studio 2015 でこのアップグレードを開始することをお勧めします。 Visual Studio 2015 での開発の主な利点が、Visual Studio 2015 では使用できないアセンブリが含まれていないことを確認してください。 Visual Studio 2017 で開発する場合は、Visual Studio 2017 にのみ存在するアセンブリの依存関係を導入する可能性がありますリスクがあります。

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Project.json への参照がないことを確認します。

このドキュメントの後半には、*.csproj ファイル内の条件付きのインポート ステートメントを挿入します。  これは、project.json に、NuGet の参照が格納されている場合に機能しません。 そのため、すべての NuGet 参照 packages.config ファイルを移動することをお勧めします。
場合は、プロジェクトには、project.json ファイルが含まれています。

* Project.json に参照メモに取ります。
* ソリューション エクスプ ローラーからプロジェクトから、project.json ファイルを削除します。
    * これでは、project.json ファイルを削除し、プロジェクトから削除します。
* NuGet の参照がプロジェクトに再度追加します。
    * ソリューションを右クリックし、選択**Manage NuGet Packages for Solution しています.**
    * Visual Studio が自動的に packages.config ファイルを作成します。

>**注:**を右クリックして追加する必要がある場合は、プロジェクトには、EnvDTE パッケージが含まれている、**参照**を選択すると**参照の追加**と適切な参照を追加します。  NuGet パッケージを使用すると、プロジェクトをビルドするときにエラーが作成する可能性があります。

## <a name="adding-appropriate-build-tools"></a>適切なビルド ツールの追加

必要がありますを確認するためにビルドし、適切にデバッグすることがあるビルド ツールを追加します。 マイクロソフトと呼ばれるこの Microsoft.VisualStudio.Sdk.BuildTasks のアセンブリを作成しました。

をビルドし、Visual Studio 2015 と 2017 の両方で VSIXv3 を展開するには、次の NuGet パッケージが必要になります。

Version | ビルド ツール
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

これを行うには。

* Microsoft.VisualStudio.Sdk.BuildTasks.14.0 NuGet パッケージをプロジェクトに追加します。
* プロジェクトに Microsoft.VSSDK.BuildTools が含まれていない場合は、それを追加します。
* Microsoft.VSSDK.BuildTools バージョンが 15.x であることを確認またはそれ以上です。

## <a name="update-extension-manifest"></a>拡張機能マニフェストを更新します。

### <a name="1-installation-targets"></a>1.インストール先

Visual Studio を VSIX を作成するための対象バージョンを確認する必要があります。  通常、これらの参照は、バージョン 14.0 (Visual Studio 2015) または 15.0 (Visual Studio 2017) のバージョンのいずれかです。  ここでは両方のバージョンを対象とする必要がありますので、両方の拡張機能のインストールは、VSIX を作成することができます。  以前のバージョン番号を設定して行う、VSIX をビルドして 14.0 より前のバージョンでインストールする場合は、このただし、10.0 およびそれ以前のバージョンは現在サポートされていません。

* Visual Studio では、source.extension.vsixmanifest ファイルを開きます。
* 開く、**インストールの対象**タブです。
* 変更、**バージョン範囲**に [14.0、16.0)。  ' [' を越えて 14.0 およびすべてのバージョンは、Visual Studio に指示します。  ')' Visual Studio 15.0 バージョン 16.0 を含まないが、までのすべてのバージョンを含めるように指示します。
* すべての変更を保存して Visual Studio のすべてのインスタンスを閉じます。

![ターゲットのインストールの画像](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2.Extension.vsixmanifest ファイルの前提条件を追加します。

前提条件は、Visual Studio 2017 と新しい機能です。  この場合、Visual Studio のコア エディターを必要前提条件として。 Visual Studio 2015 VSIX デザイナーは、新しい処理しないため`Prerequisites` セクションで、XML コードに手動でのこの部分を編集する必要があります。  または、Visual Studio 2017 を開き、前提条件を挿入する、更新されたマニフェスト デザイナーを使用します。

手動でこの操作を行います。

* ファイル エクスプ ローラーでプロジェクト ディレクトリに移動します。
* 開く、`extension.vsixmanifest`ファイル テキスト エディターを使用します。
* 次のタグを追加します。

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* ファイルを保存して閉じます。

>**注:**これを実現する Visual Studio 2017 で VSIX デザイナーで選択すると、Visual Studio 2017 のすべてのバージョンと互換性があることを確認する前提条件のバージョンを手動で編集する必要があります。  デザイナーは、現在のバージョンの Visual Studio (たとえば、15.0.26208.0) として、最小バージョンを挿入するためです。  ただし、他のユーザーは、以前のバージョンがある可能性があります、ために、手動で編集するこの 15.0 にします。

この時点で、マニフェスト ファイルは次のようになります。

![前提条件の例](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>プロジェクト ファイル (myproject.csproj) の変更します。

この手順を行うときに開いて変更した .csproj への参照を強くお勧めします。  例をいくつか見つかります[ここ](https://github.com/Microsoft/VSSDK-Extensibility-Samples)です。  任意拡張のサンプルを選択、参照の .csproj ファイルを検索して、次の手順を実行します。

* ファイル エクスプ ローラーでプロジェクト ディレクトリに移動します。
* テキスト エディターで myproject.csproj ファイルを開きます。

### <a name="1-update-the-minimumvisualstudioversion"></a>1.更新プログラム、MinimumVisualStudioVersion

* 最小の visual studio のバージョンを設定`$(VisualStudioVersion)`し、その条件付きステートメントを追加します。  存在しない場合は、これらのタグを追加します。  タグが次に示す設定を確認します。

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2.VsixType プロパティを追加します。

* 次のタグを追加`<VsixType>v3</VsixType>`プロパティ グループにします。

>**注:**これを追加することをお勧めの下、`<OutputType></OutputType>`タグ。

### <a name="3-add-the-debugging-properties"></a>3.デバッグのプロパティを追加します。

* 次のプロパティ グループを追加します。

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* いずれかの .csproj ファイルから、次のすべてのインスタンスを削除します。 csproj.user ファイル。

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4.ビルド ツールのインポートに条件を追加します。

* その他の条件付きステートメントを追加、 `<import>` Microsoft.VSSDK.BuildTools 参照を持つタグ。  これには、挿入`'$(VisualStudioVersion)' != '14.0' And`条件ステートメントの前にします。  これらのステートメントはのヘッダーとフッター、csproj ファイルに表示されます。

例:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* その他の条件付きステートメントを追加、 `<import>` Microsoft.VisualStudio.Sdk.BuildTasks.14.0 のタグ。  これには、挿入`'$(VisualStudioVersion)' == '14.0' And`条件ステートメントの前にします。 これらのステートメントはのヘッダーとフッター、csproj ファイルに表示されます。

例:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* その他の条件付きステートメントを追加、 `<Error>` Microsoft.VSSDK.BuildTools 参照を持つタグ。  これには、挿入`'$(VisualStudioVersion)' != '14.0' And`条件ステートメントの前にします。 これらのステートメントは、csproj ファイルのフッターに表示されます。

例:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* その他の条件付きステートメントを追加、 `<Error>` Microsoft.VisualStudio.Sdk.BuildTasks.14.0 のタグ。  これには、挿入`'$(VisualStudioVersion)' == '14.0' And`条件ステートメントの前にします。 これらのステートメントは、csproj ファイルのフッターに表示されます。

例:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Csproj ファイルを保存して閉じます。

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 と Visual Studio 2017 で拡張機能のインストールをテストします。

この時点では、プロジェクトは、Visual Studio 2015 と Visual Studio 2017 の両方でインストールできる VSIXv3 をビルドできる状態にする必要があります。

* Visual Studio 2015 でプロジェクトを開きます
* プロジェクトをビルドし、確認を VSIX が正しくビルドの出力
* プロジェクトのディレクトリに移動します。
* 開く、箱]-> [デバッグ フォルダー
* VSIX ファイルをダブルクリックし、Visual Studio 2015 と Visual Studio 2017 で、拡張機能のインストール
* 拡張機能と、「インストール済み」のセクションで更新プログラム]-> [ツールの拡張機能を表示できることを確認します。
* それが動作するかを確認する拡張機能を使用して実行しようとしました

![VSIX の検索](media/finding-a-VSIX-example.png)

>**注:**プロジェクトが Visual Studio をシャット ダウン メッセージ「ファイルを開く」強制的にハングした場合は、プロジェクト ディレクトリに移動し、非表示のフォルダーを表示する .vs フォルダーを削除します。
