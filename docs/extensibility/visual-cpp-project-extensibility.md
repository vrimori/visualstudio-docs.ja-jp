---
title: ビジュアルの C++ プロジェクト機能拡張
ms.date: 01/25/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e38ff6cf2912ccc18c27f517a35c7a543325a8eb
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232053"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio の C++ プロジェクト システムの機能拡張とツールセットの統合

*Visual C プロジェクト システム*.vcxproj ファイルを使用します。 基にして、 [Visual Studio 共通プロジェクト システム (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)し、その他新しいツールセット、ビルドのアーキテクチャおよびターゲット プラットフォームの簡単な統合のポイントを C++ 固有の機能拡張を提供します。 

## <a name="c-msbuild-targets-structure"></a>C++ の MSBuild ターゲットの構造体

すべての .vcxproj ファイルでは、これらのファイルをインポートします。

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

これらのファイルの定義はほとんど単独でします。 代わりに、これらのプロパティ値に基づくその他のファイルをインポートします。

- `$(ApplicationType)`

   次に例を示します。Windows ストア、Android、Linux

- `$(ApplicationTypeRevision)`

   これは、必要があります形式 major.minor[.build[.revision の有効なバージョン文字列、]。

   次に例を示します。1.0, 10.0.0.0

- `$(Platform)`

   ビルドのアーキテクチャでは、歴史的な理由から"Platform"という名前です。

   次に例を示します。Win32、x86、x64、ARM   

- `$(PlatformToolset)`

   例: v140、v141、v141_xp、llvm

これらのプロパティ値の下のフォルダー名を指定する、`$(VCTargetsPath)`ルート フォルダー。

> `$(VCTargetsPath)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;*アプリケーションの種類*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*プラットフォーム*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  
> &nbsp;&nbsp;&nbsp;&nbsp;プラットフォーム\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(際に使用される`$(ApplicationType)`が空で、Windows デスクトップ プロジェクト)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  

### <a name="add-a-new-platform-toolset"></a>新しいプラットフォーム ツールセットを追加します。

新しいツールセット、たとえば、"MyToolset"既存の Win32 プラットフォームを追加するには、作成、 *MyToolset*の下のフォルダー `$(VCTargetsPath)` *\\プラットフォーム\\Win32\\PlatformToolsets\\*、作成と*Toolset.props*と*Toolset.targets*内のファイル。

下には、各フォルダー名*PlatformToolsets*に表示されます、**プロジェクトのプロパティ**として、使用可能なダイアログ**プラットフォーム ツールセット**指定されたプラットフォームの次のように。

![プロジェクト プロパティ ページ ダイアログ ボックスで、プラットフォーム ツールセット プロパティ](media/vc-project-extensibility-platform-toolset-property.png "プロジェクト プロパティ ページ ダイアログ ボックスで、プラットフォーム ツールセットのプロパティ")

同様の作成*MyToolset*フォルダーと*Toolset.props*と*Toolset.targets*このツールセットがサポートする各プラットフォームの既存のフォルダー内のファイル。

### <a name="add-a-new-platform"></a>新しいプラットフォームを追加します。

、たとえば、"MyPlatform"と、新しいプラットフォームを追加するには作成、 *MyPlatform*の下のフォルダー `$(VCTargetsPath)` *\\プラットフォーム\\*、作成と*Platform.default.props*、 *Platform.props*、および*Platform.targets*内のファイル。 作成することも、 `$(VCTargetsPath)` *\\プラットフォーム\\*<strong><em>MyPlatform</em></strong>*\\PlatformToolsets\\*フォルダー、少なくとも 1 つのツールセットを作成します。

下にあるすべてのフォルダー名、*プラットフォーム*フォルダーごとに`$(ApplicationType)`と`$(ApplicationTypeRevision)`として利用可能な IDE に表示されます**プラットフォーム**プロジェクトを選択します。

![新しいプロジェクト プラットフォームのダイアログ ボックスで新しいプラットフォームの選択](media/vc-project-extensibility-new-project-platform.png "新しいプロジェクト プラットフォームのダイアログ ボックスで、新しいプラットフォームの選択")

### <a name="add-a-new-application-type"></a>新しいアプリケーションの種類を追加します。

新しいアプリケーションの種類を追加するには、作成、 *MyApplicationType*の下のフォルダー `$(VCTargetsPath)` *\\アプリケーションの種類\\*を作成し、 *Defaults.props*ファイル。 少なくとも 1 つのリビジョンは、アプリケーションの種類に必要なこれも作成、 `$(VCTargetsPath)` *\\アプリケーションの種類\\MyApplicationType\\1.0*フォルダーを作成し、 *Defaults.props*ファイル。 作成する必要があります、 `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\プラットフォーム*フォルダーには少なくとも 1 つのプラットフォームを作成します。

`$(ApplicationType)` `$(ApplicationTypeRevision)`ユーザー インターフェイスでプロパティは表示されません。 プロジェクト テンプレートで定義されていて、プロジェクトの作成後に変更することはできません。


## <a name="the-vcxproj-import-tree"></a>.Vcxproj インポート ツリー

Microsoft C のプロパティとターゲット ファイルのインポートの簡略化されたツリーは、ようになります。

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*既定*\\\*.*プロパティ*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*アプリケーションの種類*\\`$(ApplicationType)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*アプリケーションの種類*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*アプリケーションの種類*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*プラットフォーム*\\ `$(Platform)` \\ *Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*既定*\\\*.*プロパティ*  

Windows デスクトップ プロジェクトを定義しない`$(ApplicationType)`のみをインポートするため、

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*既定*\\\*.*プロパティ*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*プラットフォーム*\\`$(Platform)`\\*Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*既定*\\\*.*プロパティ*  

使用して、`$(_PlatformFolder)`を保持するプロパティ、`$(Platform)`プラットフォーム フォルダーの場所。 このプロパティは、します。 

> `$(VCTargetsPath)`\\*プラットフォーム*\\`$(Platform)`

Windows デスクトップ アプリ、および 

> `$(VCTargetsPath)`\\*アプリケーションの種類*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*プラットフォーム*\\`$(Platform)`

その他すべての

プロパティ ファイルは、この順序でインポートされます。

> `$(VCTargetsPath)`\\*Microsoft.Cpp.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*.*プロパティ*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*.*プロパティ*  

ターゲット ファイルは、この順序でインポートされます。

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*.*ターゲット*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.target*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*.*ターゲット*  

いくつかのツールセットの既定のプロパティを定義する必要がある場合は、適切な ImportBefore および ImportAfter フォルダーにファイルを追加できます。

## <a name="author-toolsetprops-and-toolsettargets-files"></a>作成者 Toolset.props と Toolset.targets ファイル

*Toolset.props*と*Toolset.targets*ファイルがこのツールセットを使用すると、ビルド中に起きたことに対してフル コントロールがあります。 使用可能なデバッガー、一部の IDE ユーザー インターフェイスのコンテンツなどを制御することも、**プロパティ ページ**ダイアログ、およびプロジェクトの動作の他の一部の側面です。

ツールセットには、ビルド プロセス全体をオーバーライドできます、通常なら、ツールセットを変更または追加のいくつかのビルド手順、または既存のビルド プロセスの一部として別のビルド ツールを使用します。 この目標を実現するには、さまざまな、ツールセットをインポートできる共通のプロパティとターゲット ファイルがあります。 目的に応じて、ツールセットには、これらのファイルをインポートまたは例として使用すると便利可能性があります。

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   このファイルは、ネイティブ ビルド プロセスの主要な部分を定義しもインポートします。

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Microsoft コンパイラを使用すると、Windows をターゲットのツールセットの既定値を設定します。

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   このファイルは、Windows SDK の場所を決定し、Windows を対象とするアプリの重要なプロパティを定義します。

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>既定値は、C++ のビルド プロセスのツールセット固有のターゲットを統合します。 

C++ のビルド プロセスの既定で定義している*Microsoft.CppCommon.targets*します。 ターゲットがありますが、特定のビルド ツールを呼び出さないでください。メイン ビルド手順、その順序と依存関係を指定します。

C++ のビルドには、次のターゲットで表されている 3 つの主な手順があります。

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

各ビルド ステップが個別に実行される可能性があります、ために、1 つの手順で実行されているターゲットは、さまざまな手順の一部として実行されるターゲットで定義されたプロパティと項目グループを使用できません。 この区分は、パフォーマンスの最適化を特定のビルドにできます。 既定では使用されませんが、まだこの分離を優先することをお勧めできました。

内の各ステップで実行するターゲットは、これらのプロパティによって制御されます。

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

各ステップでは前に、と後のプロパティもあります。 

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

参照してください、 *Microsoft.CppBuild.targets*例については、各ステップに含まれているターゲットのファイル。

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

など、目的のターゲットを確認すると`_ClCompile`、自体によって直接は何もしませんが、代わりになど、他のターゲットに依存、わかります`ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` 空のターゲットとしてツールに固有のターゲットが定義されている他のビルドと*Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

`ClCompile`ターゲットが空の場合、ツールセットでオーバーライドしない限り、実際のビルド アクションは実行されません。 ツールセットのターゲットをオーバーライドできます、`ClCompile`ターゲット、つまり、含めることができる別`ClCompile`定義をインポートした後*Microsoft.CppBuild.targets*: 

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Visual Studio は、クロス プラットフォームのサポートを実装する前に作成された、名前とは異なり、`ClCompile`ターゲットは CL.exe を呼び出す必要はありません。 適切な MSBuild タスクを使用しても、Clang、gcc、または他のコンパイラを呼び出すことができます。

`ClCompile`ターゲットを除くすべての依存関係のない、`SelectClCompile`ターゲットでは、IDE で作業を 1 つのファイルのコンパイル コマンドに必要です。

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>ツールセットのターゲットで使用する MSBuild タスク

実際のビルド ツールを起動するには、ターゲットを MSBuild タスクを呼び出す必要があります。 基本的ながある[Exec タスク](../msbuild/exec-task.md)を実行するコマンドラインを指定することができます。 ただし、通常、ビルド ツールでは、多くのオプション、入力があります。 インクリメンタル ビルドを追跡するため、それらに対する特別なタスクを持つ方が合理的に出力します。 たとえば、`CL`タスク CL.exe スイッチの MSBuild プロパティに変換、応答ファイルに書き込みますおよび CL.exe を呼び出します。 また、以降のインクリメンタル ビルドのすべての入力と出力ファイルを追跡します。 詳細については、次を参照してください。[インクリメンタル ビルドと最新チェック](#incremental-build-and-up-to-date-check)します。

Microsoft.Cpp.Common.Tasks.dll は、これらのタスクを実装します。

- `BSCMake`

- `CL`

- `ClangCompile` (clang gcc スイッチ)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (Exec が入力と出力の追跡、)

- `SetEnv`

- `GetOutOfDateItems`

ツールがある場合、既存のツールと同じアクションを実行して (clang cl および CL は、次の操作) と同様のコマンド ライン スイッチが、それらの両方に対して同じタスクを使用することができます。

ビルド ツールの新しいタスクを作成する必要がある場合は、次のオプションから選択できます。

1. まれには、このタスクを使用する場合、またはビルドの問題、数秒でない場合は、MSBuild 'inline' のタスクを使用することができます。

   - Xaml タスク (カスタム ビルド規則)

     Xaml タスクの宣言の 1 つ例は、次を参照してください`$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*、およびその使用法を参照してください。 `$(VCTargetsPath)` \\ 。*BuildCustomizations*\\*masm.targets*します。

   - [コードのタスク](../msbuild/msbuild-inline-tasks.md)

1. タスクのパフォーマンスが向上するか、またはより複雑な機能が必要なだけの場合は、通常の MSBuild を使用して[タスクの作成](../msbuild/task-writing.md)プロセス。

   すべての入力とツールの出力にある場合、ツールのコマンド ラインでとして、 `CL`、 `MIDL`、および`RC`、場合によっては、自動入力と出力ファイルの追跡と .tlog ファイルを作成する場合は、タスクを派生させて、から`Microsoft.Build.CPPTasks.TrackedVCToolTask`クラス。 現在のところ、ベースのドキュメントは[ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)クラス、例やの詳細については、ドキュメントがない、`TrackedVCToolTask`クラス。 これは、興味のあるが場合、音声要求に追加で[developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html)します。

## <a name="incremental-builds-and-up-to-date-checks"></a>インクリメンタル ビルドと最新状態チェック

既定の MSBuild のインクリメンタル ビルドの使用を対象と`Inputs`と`Outputs`属性。 それらを指定する場合、MSBuild は、すべての出力より新しいタイムスタンプを持つ、入力のいずれかの場合にのみ、ターゲットを呼び出します。 ソース ファイルが多くの場合、含めるまたはその他のファイルをインポートし、ビルド ツールの生成ツール オプションによって別の出力、ため、すべての可能な入力を指定するが難しいと、MSBuild ターゲットを出力します。

この問題を管理するには、C++ のビルドはインクリメンタル ビルドをサポートするために、さまざまな方法を使用します。 ほとんどのターゲットは、入力と出力を指定して、その結果、ビルド時に常に実行しないでください。 ターゲットによって呼び出されるタスクすべてに関する情報が入力されに出力を書き込む*tlog* .tlog 拡張子を持つファイル。 変更され、再構築する必要がある内容を確認する .tlog ファイルは以降のビルドで使用と最新の状態。 IDE の既定のビルド最新チェックの唯一のソースがも .tlog ファイル。

ネイティブ ツールのタスクをすべての入力と出力を確認するには、tracker.exe を使用して、 [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) MSBuild によって提供されるクラス。

Microsoft.Build.CPPTasks.Common.dll 定義、`TrackedVCToolTask`パブリックの抽象基本クラス。 ほとんどのネイティブ ツール タスクは、このクラスから派生されます。

Visual Studio 2017 update 15.8 以降を使えば、 `GetOutOfDateItems` .tlog ファイルは、既知の入力と出力のカスタム ターゲットを生成する Microsoft.Cpp.Common.Tasks.dll で実装されたタスク。
使用して作成する代わりに、`WriteLinesToFile`タスク。 参照してください、`_WriteMasmTlogs`ターゲット`$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*など。

## <a name="tlog-files"></a>.tlog ファイル。

.Tlog ファイルの 3 つの種類があります:*読み取り*、*書き込み*、および*コマンド ライン*します。 読み取りと書き込みの .tlog ファイルは、インクリメンタル ビルドと IDE の最新の状態チェックに使用されます。 コマンド ライン .tlog ファイルは、インクリメンタル ビルドでのみ使用されます。

MSBuild では、読み取りと書き込み .tlog ファイル。 これらのヘルパー クラスを提供します。

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[している FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata)読み書きの両方にアクセスし、.tlog ファイルの書き込みと出力がない場合や、出力よりも新しい入力を識別するクラスを使用できます。 最新の状態の確認に使用されます。

コマンド ライン .tlog ファイルには、ビルドで使用されるコマンドラインに関する情報が含まれます。 内部の形式が生成する MSBuild タスクによって決まりますが、最新ではないチェックは、インクリメンタル ビルドにのみ使用されます。


### <a name="read-tlog-format"></a>読み取り .tlog 形式

*読み取り*.tlog ファイル。 (\*. read.\*します。tlog) ソース ファイルとその依存関係に関する情報が含まれます。

カレット (**^**)、行の先頭に 1 つまたは複数のソースを示します。 同じ依存関係を共有するソースは、縦棒で区切られます (**\|**)。

依存関係ファイルは、ソースは、それぞれ独自の行の後に一覧表示されます。 すべてのファイル名は、完全なパスです。

たとえば、プロジェクトのソースにあるは*f:\\テスト\\ConsoleApplication1\\ConsoleApplication1*します。 場合、ソース ファイル*Class1.cpp*、これらが含まれています。

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

次に、 *CL.read.1.tlog*ファイルには、2 つの依存関係はその後にソース ファイルが含まれています。

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

ファイル名を大文字で記述する必要はありませんが、いくつかのツールの利便性です。

### <a name="write-tlog-format"></a>.Tlog 形式を記述します。

*書き込み*.tlog (\*.write。\*します。tlog) ファイルは、ソースと出力を接続します。

カレット (**^**)、行の先頭に 1 つまたは複数のソースを示します。 複数のソースは、縦棒で区切られます (**\|**)。

ソースからビルドされた出力ファイルが、ソースは、それぞれ独自の行の後に表示されます。 すべてのファイル名は、完全なパスである必要があります。

たとえば、追加のソース ファイルがある単純な ConsoleApplication プロジェクト*Class1.cpp*、 *link.write.1.tlog*ファイルを含めることができます。

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>デザイン時のビルド

IDE では、.vcxproj プロジェクトは、プロジェクトから追加情報を取得し、出力ファイルを再生成する一連の MSBuild ターゲットを使用します。 これらのターゲットの一部は、デザイン時のビルドで使用してのみが、それらの多くは、定期的なビルドとデザイン時ビルドの両方で使用されています。

デザイン時ビルドについての CPS ドキュメントを参照して[デザイン時ビルド](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)します。 このドキュメントでは、Visual C プロジェクトに適用可能な部分的のみです。

`CompileDesignTime`と`Compile`デザイン時に記載されているターゲットが実行しない .vcxproj プロジェクトのドキュメントをビルドします。 Visual C .vcxproj プロジェクトでは、IntelliSense の情報を取得するのに別のデザイン時のターゲットを使用します。

### <a name="design-time-targets-for-intellisense-information"></a>IntelliSense の情報のデザイン時のターゲット

.Vcxproj プロジェクトで使用されるデザイン時のターゲットが定義されている`$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*します。

`GetClCommandLines`ターゲットは IntelliSense のコンパイラ オプションを収集します。

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` デザイン時の初期化をビルドするターゲット、デザイン時に必要なだけです。 特に、これらのターゲットには、パフォーマンスを向上させるために定期的なビルド機能の一部が無効にします。

- `ComputeCompileInputsTargets` – 対象セットにコンパイラ オプションおよび項目を変更します。 これらのターゲットは、デザイン時および定期的なビルドで実行します。

ターゲットの呼び出し、 `CLCommandLine` IntelliSense で使用するコマンド ラインを作成するタスク。 もう一度、名前とは異なり、だけでなく、CL オプション、Clang と gcc オプションもを処理ができます。 コンパイラ スイッチの種類はによって制御されます、`ClangMode`プロパティ。

コマンド ラインが現時点では、によって生成された、`CLCommandLine`タスクが IntelliSense エンジンを解析するが容易になるために、(Clang モード) であっても CL スイッチが常にで使用します。

コンパイル前に実行されます定期的または、デザイン時かどうかを確認するには中断されませんターゲットを追加する場合、デザイン時はビルドまたはパフォーマンスに影響します。 ターゲットをテストする最も簡単な方法では、開発者コマンド プロンプトを開き、このコマンドを実行します。

> msbuild/p:SolutionDir =*ソリューション-ディレクトリ-と-末尾の円記号*;構成デバッグ; を =プラットフォーム Win32; を =BuildingInsideVisualStudio = true; DesignTimebuild = true/t:\_PerfIntellisenseInfo/v:d/fl/fileloggerparameters:PerformanceSummary \*.vcxproj

このコマンドは、詳細なビルド ログを生成*msbuild.log になります*最後に、パフォーマンスのターゲットとタスクの概要を持ちます。

使用することを確認`Condition ="'$(DesignTimeBuild)' != 'true'"`定期的なビルドとデザイン時ビルドのではなく意味がないすべての操作にします。

### <a name="design-time-targets-that-generate-sources"></a>デザイン時のターゲットのソースを生成します。

*この機能は、デスクトップのネイティブ プロジェクトの既定では無効になり、キャッシュされたプロジェクトでは現在サポートされていません*します。

場合`GeneratorTarget`プロジェクト項目のメタデータが定義されている、ターゲットの実行が自動的には両方が、プロジェクトが読み込まれるときに、ソース ファイルが変更されたとき。

たとえばを自動的に生成 .cpp または .h、.xaml ファイルからファイル、 `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\ *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets*ファイルは、これらを定義エンティティ:

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

使用する`Task.HostObject`するソース ファイルの保存されていないコンテンツを取得するには、ターゲットとタスクとして登録する必要があります[MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) pkgdef 内の特定のプロジェクト。

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual Studio IDE でビジュアルの C++ プロジェクトの機能拡張

Visual C プロジェクト システムがに基づいて、 [VS プロジェクト システム](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)、し、その機能拡張ポイントが使用されます。 ただし、プロジェクト階層の実装は、Visual C に固有、CPS に基づいていない、階層の機能拡張プロジェクト項目に制限されています。

### <a name="project-property-pages"></a>プロジェクト プロパティ ページ

一般的な設計については、次を参照してください。[プラットフォームの拡張性 - パート 1](https://blogs.msdn.microsoft.com/vsproject/2009/06/09/platform-extensibility-part-1/)と[プラットフォームの拡張性 - パート 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/)します。

簡単に言えば、プロパティ ページを参照してください、**プロジェクトのプロパティ**C++ プロジェクトのダイアログが定めた*ルール*ファイル。 ルール ファイルには、一連のプロパティ ページでは、表示し、プロジェクトに保存する必要があり、どのファイルのプロパティを指定します。 ルール ファイルは、Xaml 形式を使用する .xml ファイルです。 シリアル化に使用する型が記載されて[Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes)します。 プロジェクト内のルール ファイルの使用に関する詳細については、次を参照してください。[プロパティ ページの XML ルール ファイル](/cpp/ide/property-page-xml-files)します。

ルール ファイルに追加する必要があります、`PropertyPageSchema`項目グループ。

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` メタデータは、ルール可視性、規則の種類によっても制御し、これらの値のいずれかの制限します。

> `Project` | `File` | `PropertySheet`

CPS は、コンテキストの種類の他の値をサポートしていますが、Visual C プロジェクトで使用されていません。

ルールは、1 つ以上のコンテキストで表示するか場合、は、セミコロンを使用して (**;**) を次に示すようにコンテキストの値を区切ります。

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>規則形式および主な型

規則形式では単純ですが、ため、このセクションには、ルールがユーザー インターフェイスで検索する方法に影響を与える属性のみについて説明します。

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate`属性でルールを表示する方法を定義、**プロパティ ページ**ダイアログ。 属性は、これらの値の 1 つがあります。


| 属性 | 説明 |
|------------| - |
| `generic` | すべてのプロパティがカテゴリの見出しの下の 1 つのページに表示されます。<br/>ルールが表示されていることができます`Project`と`PropertySheet`、コンテキストがない`File`します。<br/><br/> 例:`$(VCTargetsPath)`\\*1033*\\*general.xml* |
| `tool` | カテゴリは、サブページとして表示されます。<br/>このルールはすべてのコンテキストで表示できます: `Project`、`PropertySheet`と`File`します。<br/>プロジェクトに項目がある場合にのみ、ルールがプロジェクトのプロパティに表示される、`ItemType`で定義されている`Rule.DataSource`にルールの名前が含まれていなければ、`ProjectTools`項目グループ。<br/><br/>例:`$(VCTargetsPath)`\\*1033*\\*clang.xml* |
| `debugger` | [デバッグ] ページの一部として、ページが表示されます。<br/>カテゴリは現在は無視されます。<br/>ルールの名前はデバッグ ランチャー MEF オブジェクトの一致する必要があります`ExportDebugger`属性。<br/><br/>例:`$(VCTargetsPath)`\\*1033*\\*debugger\_local\_windows.xml* |
| *custom* | カスタム テンプレートです。 テンプレートの名前に一致する必要があります、`ExportPropertyPageUIFactoryProvider`の属性、 `PropertyPageUIFactoryProvider` MEF オブジェクト。 参照してください**Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**します。<br/><br/> 例:`$(VCTargetsPath)`\\*1033*\\*userMacros.xml* |

ルールは、プロパティ グリッド ベースのテンプレートのいずれかを使用している場合は、そのプロパティのこれらの拡張ポイントを使用できます。

- [プロパティの値エディター](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [値プロバイダーの動的な列挙型](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>ルールを拡張します。

(つまり、非表示にする) を追加または削除する必要がありますを既存の規則を使用する場合、いくつかのプロパティを作成できます、 [Extension ルール](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md)します。

#### <a name="override-a-rule"></a>ルールを上書き

おそらく 1 つだけ、またはその一部を置換するが、ほとんどのプロジェクトの既定の規則を使用する、ツールセットが必要です。 たとえば、異なるコンパイラ スイッチを表示する C/C++ 規則を変更するとします。 同じ名前の新しいルールを提供し、既存のルールとして表示名とに組み込みます、`PropertyPageSchema`既定 cpp のターゲットのインポート後に項目グループ。 名前が指定された 1 つのルールは、プロジェクトで使用してに含まれる最後の 1 つ、`PropertyPageSchema`グループ wins の項目。

#### <a name="project-items"></a>プロジェクト項目

*ことが ProjectItemsSchema.xml*ファイルを定義、`ContentType`と`ItemType`、プロジェクト項目として扱われる項目の値を定義します`FileExtension`要素に新しいファイルを追加する項目グループを決定します。

既定の ProjectItemsSchema ファイルがある`$(VCTargetsPath)` \\ *1033*\\*ことが ProjectItemsSchema.xml*します。 これを拡張するなど、新しい名前を持つスキーマ ファイルを作成する必要があります*MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

次のターゲット ファイルで次のように追加します。

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

例:`$(VCTargetsPath)`\\*BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>デバッガー

Visual Studio でデバッグ サービスでは、デバッグ エンジンの機能拡張をサポートします。 詳細については、これらのサンプルを参照してください。

- [MIEngine、lldb デバッグをサポートするオープン ソース プロジェクト](https://github.com/Microsoft/MIEngine)

- [Visual Studio デバッグ エンジンのサンプル](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

実装する必要があります、デバッグ セッションのデバッグ エンジンとその他のプロパティを指定するを[デバッグ ランチャー](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) 、MEF コンポーネントを追加し、`debugger`ルール。 例については、次を参照してください。、 `$(VCTargetsPath)` \\1033\\デバッガー\_ローカル\_windows.xml ファイル。

### <a name="deploy"></a>デプロイ

.vcxproj プロジェクトの Visual Studio プロジェクト システムの機能拡張を使用して、[プロバイダーのデプロイ](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md)します。

### <a name="build-up-to-date-check"></a>ビルドの最新のチェック

既定では、ビルドの最新の状態チェックには、内に作成する .tlog と書き込み .tlog ファイル。 読み取りが必要です、`$(TlogLocation)`フォルダーのすべてのビルド入力と出力のビルド中にします。

カスタムの最新の状態チェックを使用するには。

1. 追加することで、既定の最新の状態チェックを無効にする、`NoVCDefaultBuildUpToDateCheckProvider`機能、 *Toolset.targets*ファイル。

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. 独自に実装[IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md)します。

## <a name="project-upgrade"></a>プロジェクトのアップグレード

### <a name="default-vcxproj-project-upgrader"></a>既定 .vcxproj プロジェクト アップグレード プログラム

.Vcxproj プロジェクト アップグレード プログラムの既定の変更、 `PlatformToolset`、 `ApplicationTypeRevision`、MSBuild ツールセットのバージョンと .Net framework です。 最後の 2 つは、常に、Visual Studio のバージョンの既定値に変更しますが、`PlatformToolset`と`ApplicationTypeRevision`MSBuild の特殊なプロパティで制御できます。

アップグレード プログラムでは、これらの条件を使用して、かどうか、プロジェクトをアップグレードできるかどうかを決定します。

1. 定義するプロジェクトの`ApplicationType`と`ApplicationTypeRevision`、現在のプランより上位のバージョン番号を持つフォルダーがあります。

1. プロパティ`_UpgradePlatformToolsetFor_<safe_toolset_name>`現在のツールセットが定義されていると、その値が現在のツールセットを等しくします。

   これらのプロパティ名で *\<safe_toolset_name >* アンダー スコアに置き換え英数字以外のすべての文字とツールセットの名前を表します (**\_**)。

含まれているプロジェクトをアップグレードするには、*ソリューションの再ターゲット*します。 詳細については、次を参照してください。 [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2)します。

プロジェクトの名前を装飾するなら**ソリューション エクスプ ローラー**プロジェクトは、特定のツールセットを使用して、ときに定義、`_PlatformToolsetShortNameFor_<safe_toolset_name>`プロパティ。

例については`_UpgradePlatformToolsetFor_<safe_toolset_name>`と`_PlatformToolsetShortNameFor_<safe_toolset_name>`プロパティの定義を参照してください、 *Microsoft.Cpp.Default.props*ファイル。 使用状況の例については、次を参照してください。、 `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets*ファイル。

### <a name="custom-project-upgrader"></a>カスタム プロジェクト アップグレード プログラム

カスタム プロジェクトのアップグレード プログラム オブジェクトを使用するには、次に示すように MEF コンポーネントを実装します。

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

コードは、インポートし、既定 .vcxproj upgrader オブジェクトを呼び出すことができます。

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` 定義されている*Microsoft.VisualStudio.ProjectSystem.VS.dll*と似ています`IVsRetargetProjectAsync`します。

定義、`VCProjectUpgraderObjectName`プロパティをアップグレード プログラムのカスタム オブジェクトを使用するプロジェクト システムに指示します。

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>プロジェクトのアップグレードを無効にします。

プロジェクトのアップグレードを無効にするを`NoUpgrade`値。

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>プロジェクトのキャッシュと機能拡張

Visual Studio 2017 で大規模な C++ のソリューションを使用する場合は、パフォーマンスを向上させるために、[プロジェクト キャッシュ](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-solution-load-with-vs-15/)が導入されました。 プロジェクトのデータを設定し、MSBuild または CPS プロジェクトをメモリに読み込むことがなくプロジェクトを読み込むために使用し、SQLite データベースとして実装されます。

CPS オブジェクトをキャッシュから読み込まれている .vcxproj プロジェクトの表示がないため、拡張機能の MEF コンポーネントをインポート`UnconfiguredProject`または`ConfiguredProject`を作成できません。 拡張機能をサポートするには、Visual Studio プロジェクトを使用して (または使用する可能性があります) MEF 拡張機能かどうかを検出すると、プロジェクトのキャッシュは使用されません。

このプロジェクトの種類が常に完全に読み込まと、メモリ、CPS オブジェクトがあるため、それらのすべての MEF 拡張機能を作成します。

- スタートアップ プロジェクト

- つまり、カスタム プロジェクト アップグレード プログラムのあるプロジェクトの場合を定義、`VCProjectUpgraderObjectName`プロパティ

- プロジェクトがデスクトップの Windows をターゲットにしないのでは、これらの定義、`ApplicationType`プロパティ

- .Vcxitems プロジェクトのインポート、これらを参照する項目プロジェクト (.vcxitems) およびすべてのプロジェクトを共有します。

いずれの条件が検出された場合は、プロジェクトのキャッシュが作成されます。 キャッシュが回答するために必要な MSBuild プロジェクトからのすべてのデータを含む`get`でクエリが実行`VCProjectEngine`インターフェイス。 これは MSBuild プロパティにあるすべての変更を意味し、ターゲット ファイル レベルの拡張機能ではキャッシュから読み込まれているプロジェクトで機能します。

## <a name="shipping-your-extension"></a>拡張機能を配布

VSIX ファイルを作成する方法については、次を参照してください。 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)します。 たとえば、特別なインストール場所にファイルを追加して、下のファイルを追加する方法について`$(VCTargetsPath)`を参照してください[拡張機能フォルダー外でのインストール](../extensibility/set-install-root.md)します。

## <a name="additional-resources"></a>その他の技術情報

Microsoft ビルド システム ([MSBuild](../msbuild/msbuild.md)) ビルド エンジンと拡張可能な XML ベース形式のプロジェクト ファイルを提供します。 理解しておく必要があります basic [MSBuild の概念](../msbuild/msbuild-concepts.md)方法を使用して[Visual C の MSBuild](/cpp/build/msbuild-visual-cpp-overview)プロジェクト システムの Visual C を拡張するには動作します。

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) 拡張機能の CPS と Visual C プロジェクト システムで使用される Api を提供します。 CPS で MEF を使用する方法の概要については、次を参照してください。 [CPS と MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef)で、 [MEF の概要については VSProjectSystem](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md)します。

ビルド ステップまたは新しいファイルの種類を追加する既存のビルド システムをカスタマイズできます。 詳細については、次を参照してください。 [MSBuild (Visual c) の概要](/cpp/build/msbuild-visual-cpp-overview)と[プロジェクト プロパティの操作](/cpp/ide/working-with-project-properties)します。
