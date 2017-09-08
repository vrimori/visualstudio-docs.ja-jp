---
title: "Live Unit Testing に関する FAQ | Microsoft Docs"
ms.date: 2017-08-15
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
ms.assetid: 61baf3bb-646f-4c5a-b7c0-a6bdff68f21c
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c6a2c3b313aca87a77f7ad5b12a3d99c82c042b2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing についてよく寄せられる質問

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3 の Live Unit Testing では、何が新しくなりましたか? 

**回答:**

- .NET Core/.NET Standard 対応になったことと、パフォーマンスが向上したことが主な 2 つの変更点です。 はじめて Live Unit Testing でテストを完全ビルドして実行したときは、大幅に高速化したことに驚くでしょう。 その後、同じソリューションで Live Unit Testing をもう一度開始したときも、大幅なパフォーマンスの向上を実感できるはずです。 Live Unit Testing で生成されたデータを永続化し、最新状態チェックでは可能な限りそのデータを再利用するようにしました。 以上の主な変更点の他に、Live Unit Testing には次のような変更点があります。 

  - テスト メソッドと通常のメソッドを区別するために、新しいビーカー アイコンが使われます。 ビーカーが空の場合、特定のテストが Live Unit Testing に含まれていないことを意味します。 

  - Live Unit Testing のカバレッジ アイコンのポップアップ UI ウィンドウからテスト メソッドをクリックすると、UI ウィンドウ内でそのコンテキストからテストをデバッグできます。コード エディターを終了する必要がありません。 これは特に、失敗したテストを確認するときに便利です。  

  - [ツール]/[オプション]/[Live Unit Testing]/[全般] に、構成可能なオプションがいくつか追加されました。 Live Unit Testing に使用されるメモリに上限を設定できます。 オープン ソリューションのために、Live Unit Testing の永続的データのファイル パスも指定できます。 

  - [テスト]/[Live Unit Testing] のメニュー バーに、メニュー項目がいくつか追加されました。 **[Reset Clean]\(クリーンのリセット\)** は、永続的データを削除して再生成します。 **[オプション]** は、[ツール]/[オプション]/[Live Unit Testing]/[全般] に移動します。
  
  - 次の属性をソース コードに指定することで、対象のテスト メソッドを Live Unit Testing から除外できるようになりました。
    - xUnit の場合: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
    - NUnit の場合: `[Category("SkipWhenLiveUnitTesting")]`
    - MSTest の場合: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="does-live-unit-testing-work-with-net-core"></a>Live Unit Testing は .NET Core で動作しますか?  

**回答:**

はい。 Live Unit Testing は、.NET Core と .NET Framework で動作します。 .NET Core のサポートは、Visual Studio 2017 バージョン 15.3 で最近追加されました。 .NET Core に Live Unit Testing サポートが必要であれば、このバージョンの Visual Studio にアップグレードしてください。 

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>Live Unit Testing を有効にしても動作しないのはなぜですか? 

**回答:** 

**[出力ウィンドウ]** に (Live Unit Testing ドロップダウンを選んだとき)、Live Unit Testing が動作しない理由が表示されているはずです。 Live Unit Testing は、次のいずれかの理由で動作しない可能性があります。 

- ソリューションのプロジェクトによって参照されている NuGet パッケージが復元されていない、Live Unit Testing は動作しません。 Live Unit Testing を有効にする前に、ソリューションの明示的なビルドを行うか、またはソリューションで NuGet パッケージを復元することにより、この問題は解決するはずです。 

- MSTest ベースのテストをプロジェクトで使っている場合、`Microsoft.VisualStudio.QualityTools.UnitTestFramework` への参照を削除し、最新の MSTest NuGet パッケージ `MSTest.TestAdapter` (1.1.11 以降のバージョンが必要) および `MSTest.TestFramework` (1.1.11 以降のバージョンが必要) への参照を追加してあることを確認します。 詳しくは、「[Visual Studio 2017 での Live Unit Testing](live-unit-testing.md#supported-test-frameworks)」トピックの「サポートされるテスト フレームワーク」セクションをご覧ください。
 
- ソリューションの少なくとも 1 つのプロジェクトに、NuGet の参照、または xUnit、NUnit、MSTest のいずれかのテスト フレームワークへの直接参照が存在する必要があります。 このプロジェクトは、対応する Visual Studio テスト アダプター NuGet パッケージを参照する必要もあります。 Visual Studio テスト アダプターは、`.runsettings` ファイルから参照することもできます。 `.runsettings` ファイルには、次のようなエントリが必要です。 

   ```xml
    <RunSettings> 
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration> 
    </RunSettings> 
   ``` 

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>Visual Studio プロジェクトで参照されているテスト アダプターをサポートされているバージョンにアップグレードした後、Live Unit Testing に正しくないカバレッジが表示されるのはなぜですか?

**回答:**

- ソリューションの複数のプロジェクトが NuGet テスト アダプター パッケージを参照している場合は、それぞれをサポートされるバージョンにアップグレードする必要があります。

- テスト アダプター パッケージからインポートされた MSBuild の .props ファイルも正しく更新されていることを確認してください。 インポートの NuGet パッケージのバージョン/パスを確認します。通常これは、次のように、プロジェクト ファイルの上部近くに表示されます。

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>Live Unit Testing のビルドをカスタマイズできますか? 

**回答:**

"標準の" インストルメント化されていないビルドには必要ないインストルメンテーション (Live Unit Testing) 用にビルドするためのカスタム手順がソリューションに必要な場合は、`BuildingForLiveUnitTesting` プロパティを調べてビルド前/後のカスタム手順を実行するコードを、プロジェクトまたは .targets ファイルに追加できます。 また、このプロジェクト プロパティに基づいて、Live Unit Testing のビルドから特定のビルド手順 (パッケージの発行や生成など) を削除したり、Live Unit Testing にビルド手順 (前提条件のコピーなど) を追加したりすることもできます。 これにより標準のビルドは変更されず、Live Unit Testing のビルドのみが影響を受けます。 

たとえば、標準のビルドの間に NuGet パッケージを生成するターゲットがあるものとします。 おそらく、編集のたびに NuGet パッケージを生成する必要はありません。 そのような場合、次のようにして、Live Unit Testing のビルドでそのターゲットを無効にできます。   

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'"> 
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/> 
</Target> 
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>&lt;OutputPath&gt; または &lt;OutDir&gt; に関するエラー メッセージ

**Live Unit Testing がソリューションのビルドを試みると、次のようなエラー メッセージが表示されるのはなぜですか? "...appears to unconditionally set `<OutputPath>` or `<OutDir>`.Live Unit Testing will not execute tests from the output assembly" (... が <OutputPath> または <OutDir> を無条件に設定したようです。Live Unit Testing は出力アセンブリからテストを実行しません)**

**回答:**

このエラーは、ソリューションのビルド プロセスが `<OutputPath>` または `<OutDir>` を無条件にオーバーライドして `<BaseOutputPath>` のサブディレクトリではないようにした場合に、発生する可能性があります。 このような場合、Live Unit Testing もこれらをオーバーライドしてビルド成果物を `<BaseOutputPath>` の下のフォルダーに格納するため、Live Unit Testing は動作しなくなります。 標準ビルドでビルド成果物が格納される場所をオーバーライドする必要がある場合は、`<BaseOutputPath>` を基にして条件付きで `<OutputPath>` をオーバーライドしてください。 

たとえば、次のように `<OutputPath>` をオーバーライドするものとします。 

```xml 
<Project> 
  <PropertyGroup> 
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath> 
  </PropertyGroup> 
</Project> 
```

これは、次のように置き換えることができます。 

```xml 
<Project> 
  <PropertyGroup> 
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath> 
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath> 
  </PropertyGroup> 
</Project> 
```
 
これにより、`<OutputPath>` は `<BaseOutputPath>` フォルダー内に存在するようになります。 
 
ビルド プロセスで `<OutDir>` を直接オーバーライドしないでください。ビルド成果物を特定の場所に格納するには、代わりに `<OutputPath>` をオーバーライドします。
  
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>Live Unit Testing のビルド成果物の場所の設定

**Live Unit Testing のビルド成果物を、`.vs` フォルダーの下の既定の場所ではない特定の場所に格納する必要があります。どうすれば変更できますか?**
 
**回答:**

`LiveUnitTesting_BuildRoot` ユーザー レベル環境変数を、Live Unit Testing のビルド成果物を格納するパスに設定します。  

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>[テスト エクスプローラー] ウィンドウと Live Unit Testing では、テストの実行方法はどのように違いますか? 

**回答:**

いくつか違いがあります。 

- [テスト エクスプローラー] ウィンドウからテストを実行またはデバッグすると標準バイナリが実行されますが、Live Unit Testing ではインストルメント化されたバイナリが実行されます。 インストルメント化されたバイナリをデバッグする場合、テスト メソッドに [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) メソッドの呼び出しを追加し、そのメソッドが実行されると常にデバッガーが起動されるようにすることで (Live Unit Testing によって実行される場合を含みます)、インストルメント化されたバイナリをアタッチしてデバッグできます。 しかし、ほとんどのユーザー シナリオについてインストルメンテーションが透過的で、インストルメント化されたバイナリをデバッグする必要がないようにするのが理想的です。 

- Live Unit Testing ではテストを実行するための新しいアプリケーション ドメインは作成されませんが、[テスト エクスプローラー] ウィンドウから実行されたテストでは新しいアプリケーション ドメインが作成されます。 

- Live Unit Testing では各テスト アセンブリが順番に実行されるのに対し、**[テストを並列で実行する]** ボタンを選んで [テスト エクスプローラー] ウィンドウから複数のテストを実行した場合は、並列に実行されます。 

- Live Unit Testing でのテストの探索と実行にはバージョン 2 の `TestPlatform` が使われますが、[テスト エクスプローラー] ウィンドウではバージョン 1 が使われます。 ただし、ほとんどの場合違いはわかりません。  

- 現在、テスト エクスプローラーは既定ではシングルスレッド アパートメント (STA) でテストを実行するのに対し、Live Unit Testing はマルチスレッド アパートメント (MTA) でテストを実行します。 Live Unit Testing において MSTest テストを STA で実行するには、テスト メソッドまたはそれを含むクラスを、`MSTest.STAExtensions 1.0.3-beta` NuGet パッケージに含まれる `<STATestMethod>` または `<STATestClass>` 属性で修飾します。 NUnit の場合はテスト メソッドを `<RequiresThread(ApartmentState.STA)>` 属性で修飾し、xUnit の場合は `<STAFact>` 属性で修飾します。
 
## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>Live Unit Testing からテストを除外するにはどうすればよいですか?

**回答:**

ユーザー固有の設定については、「[Visual Studio 2017 での Live Unit Testing](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods)」トピックの「テスト プロジェクトとテスト メソッドを含めるか除外する」セクションをご覧ください。 これは、特定の編集セッションに対して特定のテスト セットを実行したい場合、または個人設定を維持したい場合に非常に便利です。
  
ソリューション固有の設定では、<xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> 属性をプログラムで適用することにより、Live Unit Testing によるインストルメント化からメソッド、プロパティ、クラス、構造体を除外できます。 さらに、プロジェクト ファイルで `<ExcludeFromCodeCoverage>` プロパティを `true` に設定して、プロジェクト全体をインストルメント化から除外することもできます。 それでも Live Unit Testing はインストルメント化されていないテストを実行しますが、カバレッジは視覚化されません。

`Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` が現在のアプリケーション ドメインに読み込まれているかどうかを確認し、それに基づいてテストを無効にすることもできます。 たとえば、xUnit では次のような処理を行うことができます。

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name == 
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>Live Unit Testing によってビルドされたインストルメント化されたアセンブリでは Win32 PE ヘッダーが異なるのはなぜですか? 

**回答:**

この問題は解消されており、Visual Studio 2017 バージョン 15.3 では発生しません。 このバージョンの Visual Studio にアップグレードしてください。

以前のバージョンの Visual Studio 2017 の場合、Live Unit Testing のビルドで次の Win32 PE ヘッダー データの埋め込みが失敗する既知のバグがあります。 

- ファイル バージョン (コードで @System.Reflection.AssemblyFileVersionAttribute によって指定)。 

- Win32 アイコン (コマンド ラインで `/win32icon:` によって指定)。 

- Win32 マニフェスト (コマンド ラインで `/win32manifest:` によって指定)。 

これらの値に依存するテストは、Live Unit Testing で実行すると失敗する場合があります。

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>編集を行わなかった場合でも Live Unit Testing で常にソリューションがビルドされるのはなぜですか? 

**回答:**

この現象は、ソリューションのビルド プロセスによってソリューション自体の一部であるソース コードが生成され、ビルド ターゲット ファイルにおいて適切な入力と出力が指定されていない場合に、発生する可能性があります。 MSBuild が適切な最新状態チェックを実行し、新しいビルドが必要かどうかを判断できるように、ターゲットに入力と出力のリストを提供する必要があります。 

Live Unit Testing は、ソース ファイルが変更されたことを検出すると常に、ビルドを開始します。 ソリューションのビルドでソース ファイルが生成されるので、Live Unit Testing は無限ビルド ループになります。 ただし、Live Unit Testing が (前のビルドで新しく生成されたソース ファイルを検出した後) 2 回目のビルドを開始するときに、ターゲットの入力と出力を調べる場合は、入力と出力のチェックですべてが最新であることが示されるため、ループから抜け出します。   

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>ライトウェイト ソリューション ロード機能では Live Unit Testing はどのように動作しますか? 

**回答:**

Live Unit Testing は現在のところ、ライトウェイト ソリューション ロード機能とうまく連動しません。 テスト プロジェクトを少なくとも 1 つ読み込まないと作動しません。 プロジェクトを読み込むまで正常に作動しない理由は、現在のところ、Live Unit Testing は 1 つ以上のテスト プロジェクトを利用しなければ、読み込まれるテスト アダプター (MSTest、xUnit、NUnit) を参照できないことにあります。
 
## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>Live Unit Testing がテストによって作成された新しいプロセスからカバレッジをキャプチャしないのはなぜですか?
 
**回答:**

これは既知の問題であり、Visual Studio 2017 の今後の更新プログラムで修正されるはずです。 

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>Live Test セットにテストを含めたり、セットからテストを除外した後、何も行われないのはなぜですか? 

**回答:**

この問題は解消されており、Visual Studio 2017 バージョン 15.3 では発生しません。 このバージョンの Visual Studio にアップグレードしてください。 

この問題は、以前のバージョンの Visual Studio 2017 で確認されています。 この問題を回避するには、テストを含めたり除外したりした後、任意のファイルを編集する必要があります。  

## <a name="live-unit-testing-and-editor-icons"></a>Live Unit Testing とエディターのアイコン 

**出力ウィンドウのメッセージでは Live Unit Testing が実行しているようなのに、エディターにアイコンが表示されないのはなぜですか?** 

**回答:**

この現象は、Live Unit Testing が動作しているアセンブリが何らかの理由でインストルメント化されていない場合に発生します。 たとえば、Live Unit Testing は `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` を設定するプロジェクトと互換性がありません。 この場合、Live Unit Testing を動作させるには、ビルド プロセスを更新してこの設定を削除する、または `true` に変更する必要があります。  

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>ファイル バグ レポートに詳細なログを収集するにはどうすればよいですか? 

**回答:**

詳細なログを収集するにはいくつかの方法があります。 

- **[ツール]**、**[オプション]**、**[Live Unit Testing]** の順に移動し、ログ オプションを **[詳細]** に変更します。 こうすると、より詳細なログが出力ウィンドウに表示されます。 

- `LiveUnitTesting_BuildLog` ユーザー環境変数に、MSBuild ログのキャプチャに使うファイルの名前を設定します。 このようにすると、Live Unit Testing のビルドからの詳細な MSBuild ログ メッセージを、そのファイルから取得できます。

- `LiveUnitTesting_TestPlatformLog` ユーザー環境変数を `1` に設定して、テスト プラットフォームのログをキャプチャします。 このようにすると、Live Unit Testing の実行からの詳細なテスト プラットフォームのログ メッセージを `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` から取得できます。

- `VS_UTE_DIAGNOSTICS` という名前のユーザー レベル環境変数を作成し、1 (または任意の値) に設定して、Visual Studio を再起動します。 Visual Studio の **[出力 - テスト]** タブに多くのログが表示されるようになります。 
  
## <a name="see-also"></a>関連項目

[ライブ単体テスト](live-unit-testing.md)
 

