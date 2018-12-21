---
title: Devenv コマンド ライン スイッチ
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bf255a0e4eb622cb81718ddfc30d5b568bad2c2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063397"
---
# <a name="devenv-command-line-switches"></a>Devenv コマンドライン スイッチ

Devenv を使用すると、コマンド ラインから統合開発環境 (IDE: Integrated Development Environment) のさまざまなオプションを設定したり、プロジェクトをビルド、デバッグ、および配置したりすることができます。 これらのスイッチを使用して、スクリプトや .bat ファイル (夜間用のビルド スクリプトなど) から IDE を実行したり、特定の構成で IDE を起動したりします。

> [!NOTE]
> ビルド関連のタスクでは、devenv の代わりに MSBuild を使用することをお勧めします。 詳細については、「[MSBuild コマンド ライン リファレンス](../../msbuild/msbuild-command-line-reference.md)」を参照してください。

## <a name="devenv-switch-syntax"></a>Devenv のスイッチの構文

`devenv` で始まるコマンドは `devenv.com` ユーティリティによって処理されます。このユーティリティは、`stdout` や `stderr` のような標準のシステム ストリーム経由で出力を配信します。 このユーティリティは出力をキャプチャする際に、txt ファイルなどの適切な入出力先を判断します。

一方、`devenv.exe` で始まるコマンドも同じスイッチを使うことができますが、`devenv.com` ユーティリティはバイパスされます。 `devenv.exe` を使用すると、コンソールの出力表示が直接的に禁止されます。

`devenv` スイッチの構文規則は、他の DOS コマンド ライン ユーティリティのものとよく似ています。 すべての `devenv` スイッチと引数に適用される構文規則は以下のとおりです。

- `devenv` で始まるコマンド。

- スイッチは大文字と小文字を区別しません。

- ソリューションまたはプロジェクトを指定するとき、最初の引数はソリューション ファイルまたはプロジェクト ファイルの名前 (ファイル パスを含む) です。

- 最初の引数がソリューションでもプロジェクトでもないファイルの場合、そのファイルが IDE の新しいインスタンスで適切なエディターを使用して開かれます。

- ソリューション ファイル名の代わりにプロジェクト ファイル名を入力すると、`devenv` コマンドは、プロジェクト フォルダーの親フォルダーで同じ名前が付いているソリューション ファイルを検索します。 たとえば、`devenv myproject1.vbproj /build` というコマンドは、親フォルダーで "myproject1.sln" という名前のソリューション ファイルを検索します。

    > [!NOTE]
    > このプロジェクトを参照するソリューション ファイルは、親フォルダーの中に 1 つだけ置かれている必要があります。 親フォルダーにこのプロジェクトを参照するソリューション ファイルがない場合、また親フォルダーにこのソリューション ファイルが 2 つ以上ある場合は、一時ソリューション ファイルが作成されます。

- ファイル パスやファイル名にスペースが含まれる場合は、二重引用符 ("") で囲む必要があります。 たとえば、"c:\project a\\" と指定します。

- 1 行に複数のスイッチや引数を入力する場合は、空白文字 1 つで区切ります。 たとえば、**devenv /log output.txt** というコマンドは、IDE を開き、そのセッションのすべてのログ情報を output.txt に出力します。

- `devenv` コマンドではパターン一致構文を使用できません。

## <a name="devenv-switches"></a>Devenv のスイッチ

次の表のコマンド ライン スイッチを使用すると、IDE が表示され、説明されているタスクが実行されます。

|コマンド ライン スイッチ|説明|
| - |-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|IDE を起動し、指定したコマンドを実行します。|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|C++ の実行可能ファイルをデバッガーの制御下に読み込みます。 このスイッチは、Visual Basic または C# の実行可能ファイルには使用できません。 詳細については、「[デバッガーでプロセスを自動的に開始する](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger)」を参照してください。|
|[/LCID または /l](../../ide/reference/lcid-devenv-exe.md)|IDE の既定の言語を設定します。 指定した言語が Visual Studio インストールに含まれていない場合、この設定は無視されます。|
|[/Log](../../ide/reference/log-devenv-exe.md)|Visual Studio を起動し、ログ ファイルにすべてのアクティビティを記録します。|
|[/Run または /r](../../ide/reference/run-devenv-exe.md)|指定したソリューションをコンパイルして実行します。|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|指定したソリューションをコンパイルして実行します。ソリューションの実行時には IDE を最小化し、ソリューションの実行終了後に IDE を終了します。|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|IDE で C++ のコンパイルをする場合に、**[オプション]** ダイアログ ボックスの **[プロジェクト]** オプションの [VC++ ディレクトリ] セクションで指定した設定ではなく、PATH、INCLUDE、および LIB の各環境変数を使用します。 このスイッチは、**C++ によるデスクトップ開発**ワークロードと共にインストールされます。 詳細については、[コマンド ライン ビルドのパスと環境変数の設定](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds)に関するページを参照してください。|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|指定したファイルを、このアプリケーションの実行中のインスタンスで開きます。 実行中のインスタンスがない場合は、簡略化されたウィンドウ レイアウトで新しいインスタンスを起動します。|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|Visual Studio をセーフ モードで起動し、既定の環境とサービス、および出荷バージョンのサードパーティ パッケージだけを読み込みます。|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|問題のある VSPackage が読み込まれないようにユーザーが VSPackages に追加した SkipLoading タグをすべて消去します。|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|使用できるすべての VSPackages にある、メニュー、ツール バー、およびコマンド グループを記述したリソース メタデータが Visual Studio により強制的にマージされます。 このコマンドの実行は、管理者として行う必要があります。|

次のコマンド ライン スイッチでは、IDE が表示されません。

|コマンド ライン スイッチ|説明|
| - |-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Devenv のスイッチのヘルプを **[コマンド プロンプト]** ウィンドウ内に表示します。<br /><br /> `devenv /?`|
|[/Build](../../ide/reference/build-devenv-exe.md)|指定のソリューションの構成に従って、指定のソリューションまたはプロジェクトをビルドします。<br /><br /> `devenv myproj.csproj /build`|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|ビルド コマンドによって作成されたすべてのファイルを、ソース ファイルに影響を与えずに削除します。<br /><br /> `devenv myproj.csproj /clean`|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|ソリューションの構成に従って、ソリューションを配置に必要なファイルと共にビルドします。<br /><br /> `devenv myproj.csproj /deploy`|
|[/Diff](../../ide/reference/diff.md)|2 つのファイルを比較します。 4 つのパラメーター、SourceFile、TargetFile、SourceDisplayName (省略可能)、TargetDisplayName (省略可能) を受け取ります。|
|[/Out](../../ide/reference/out-devenv-exe.md)|ビルド時のエラーを受け取るファイルを指定できます。<br /><br /> `devenv myproj.csproj /build /out log.txt`|
|[/Project](../../ide/reference/project-devenv-exe.md)|ビルド、消去、または配置するプロジェクトを指定します。 このスイッチは、/build、/rebuild、/clean、または /deploy スイッチを指定した場合にだけ使用できます。|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|ビルドまたは配置するプロジェクト構成を指定します。 このスイッチは、/project スイッチを指定した場合だけに使用できます。|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|指定のソリューションの構成に従って、指定のソリューションまたはプロジェクトを消去してからビルドします。|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Visual Studio の既定の設定を復元します。 指定の .vssettings ファイルに準じた設定にリセットすることもできます。|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|指定されたソリューション ファイルとそのすべてのプロジェクト ファイル、または指定されたプロジェクト ファイルを、そのファイルに対応する現在の Visual Studio の形式にアップグレードします。|

## <a name="see-also"></a>関連項目

* [[全般]、[環境]、[オプション] ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)
