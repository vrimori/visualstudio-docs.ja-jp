---
title: Live Unit Testing に関する FAQ
ms.date: 2017-10-03
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: d98c0c14146fe69a04c2ebe3e715fd42167180b8
ms.sourcegitcommit: e04e52bddf81239ad346efb4797f52e38de5cb98
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43054514"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing についてよく寄せられる質問

## <a name="latest-features"></a>最新の機能
**Live Unit Testing は、定期的に改善と機能強化が行われています。最新の機能と機能強化に関する情報を確認するにはどうすればよいですか?**

Live Visual Studio 2017 バージョン 15.3 以降で Live Unit Testing に対して加えられた新機能と機能強化を確認するには、「[What's New in Live Unit Testing](live-unit-testing-whats-new.md)」 (Live Unit Testing の新機能) を参照してください。

## <a name="supported-frameworks-and-versions"></a>サポートされるフレームワークとバージョン
**Live Unit Testing でサポートされているテスト フレームワークは何ですか? また、サポートされている最小バージョンはいくつですか?**

Live Unit Testing は、次の表に示されている 3 つの一般的な単体テスト フレームワークで動作します。 アダプターやフレームワークのサポートされる最小バージョンも表に示されています。 単体テスト フレームワークはすべて NuGet.org から入手できます。

<table>
<tr>
   <th>テスト フレームワーク</th>
   <th>Visual Studio アダプターの最小バージョン</th>
   <th>フレームワークの最小バージョン</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio バージョン 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter バージョン 3.5.1</td>
   <td>NUnit バージョン 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

`Microsoft.VisualStudio.QualityTools.UnitTestFramework` を参照する以前の MSTest に基づくテスト プロジェクトを使用しており、新しい MSTest NuGet パッケージへの移行を希望されない場合は、Visual Studio 2017 バージョン 15.4 にアップグレードしてください。

場合によっては、Live Unit Testing を動作させるため、ソリューションのプロジェクトによって参照されている NuGet パッケージの明示的な復元が必要になります。 Live Unit Testing を有効にする前に、ソリューションの明示的なビルドを行うか (Visual Studio の最上位メニューから **[ビルド]** の **[ソリューションのリビルド]** を選択します)、ソリューションを右クリックして **[NuGet パッケージの復元]** を選択することでパッケージを復元できます。

## <a name="net-core-support"></a>.NET Core サポート
**Live Unit Testing は .NET Core で動作しますか?**

はい。 Live Unit Testing は、.NET Core と .NET Framework で動作します。 .NET Core のサポートは、Visual Studio 2017 バージョン 15.3 で最近追加されました。 .NET Core に Live Unit Testing サポートが必要であれば、このバージョンの Visual Studio にアップグレードします。

## <a name="configuration"></a>構成
**Live Unit Testing を有効にしても動作しないのはなぜですか?**

**[出力ウィンドウ]** に (Live Unit Testing ドロップダウンを選んだとき)、Live Unit Testing が動作しない理由が表示されているはずです。 Live Unit Testing は、次のいずれかの理由で動作しない可能性があります。

- ソリューションのプロジェクトによって参照されている NuGet パッケージが復元されていない、Live Unit Testing は動作しません。 Live Unit Testing を有効にする前に、ソリューションの明示的なビルドを行うか、ソリューションで NuGet パッケージを復元することにより、この問題は解決するはずです。

- MSTest ベースのテストをプロジェクトで使っている場合、`Microsoft.VisualStudio.QualityTools.UnitTestFramework` への参照を削除し、最新の MSTest NuGet パッケージ `MSTest.TestAdapter` (1.1.11 以降のバージョンが必要) および `MSTest.TestFramework` (1.1.11 以降のバージョンが必要) への参照を追加してあることを確認します。 詳しくは、[Visual Studio 2017 での Live Unit Testing](live-unit-testing.md#supported-test-frameworks)に関する記事の「サポートされるテスト フレームワーク」セクションをご覧ください。

- ソリューションの少なくとも 1 つのプロジェクトに、NuGet の参照、または xUnit、NUnit、MSTest のいずれかのテスト フレームワークへの直接参照が存在する必要があります。 このプロジェクトは、対応する Visual Studio テスト アダプター NuGet パッケージを参照する必要もあります。 Visual Studio テスト アダプターは、*.runsettings* ファイルから参照することもできます。 *.runsettings* ファイルには、次の例のようなエントリが必要です。

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>アップグレード後の正しくないカバレッジ
**Visual Studio プロジェクトで参照されているテスト アダプターをサポートされているバージョンにアップグレードした後、Live Unit Testing に正しくないカバレッジが表示されるのはなぜですか?**

- ソリューションの複数のプロジェクトが NuGet テスト アダプター パッケージを参照している場合は、それぞれをサポートされるバージョンにアップグレードする必要があります。

- テスト アダプター パッケージからインポートされた MSBuild の *.props* ファイルも正しく更新されていることを確認してください。 インポートの NuGet パッケージのバージョン/パスを確認します。通常これは、次のように、プロジェクト ファイルの上部近くに表示されます。

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>ビルドのカスタマイズ
**Live Unit Testing のビルドをカスタマイズできますか?**

"標準の" インストルメント化されていないビルドには必要ないインストルメンテーション (Live Unit Testing) 用にビルドするためのカスタム手順がソリューションに必要な場合は、`BuildingForLiveUnitTesting` プロパティを調べてビルド前/後のカスタム手順を行うコードを、プロジェクトまたは *.targets* ファイルに追加できます。 また、このプロジェクト プロパティに基づいて、Live Unit Testing のビルドから特定のビルド手順 (パッケージの発行や生成など) を削除したり、Live Unit Testing にビルド手順 (前提条件のコピーなど) を追加したりすることもできます。 このプロパティに基づいてビルドをカスタマイズしても、標準のビルドは変更されず、Live Unit Testing のビルドのみが影響を受けます。

たとえば、標準のビルドの間に NuGet パッケージを生成するターゲットがあるものとします。 おそらく、編集のたびに NuGet パッケージを生成する必要はありません。 そのような場合、次のようにして、Live Unit Testing のビルドでそのターゲットを無効にできます。  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>&lt;OutputPath&gt; または &lt;OutDir&gt; に関するエラー メッセージ
**Live Unit Testing がソリューションのビルドを試みると、次のようなエラー メッセージが表示されるのはなぜですか? "...appears to unconditionally set `<OutputPath>` or `<OutDir>`.Live Unit Testing will not execute tests from the output assembly" (... が <OutputPath> または <OutDir> を無条件に設定したようです。Live Unit Testing は出力アセンブリからテストを実行しません)**

このエラーは、ソリューションのビルド プロセスが `<OutputPath>` または `<OutDir>` を無条件にオーバーライドして `<BaseOutputPath>` のサブディレクトリではないようにした場合に、発生する可能性があります。 このような場合、Live Unit Testing もこれらの値をオーバーライドしてビルド成果物が `<BaseOutputPath>` の下のフォルダーにドロップされるため、Live Unit Testing は動作しなくなります。 標準ビルドでビルド成果物が格納される場所をオーバーライドする必要がある場合は、`<BaseOutputPath>` を基にして条件付きで `<OutputPath>` をオーバーライドしてください。

たとえば、次のように `<OutputPath>` をオーバーライドするものとします。

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

これは、次の XML で置き換えることができます。

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

## <a name="set-the-location-of-build-artifacts"></a>ビルド成果物の場所の設定
**Live Unit Testing のビルド成果物を、*.vs* フォルダーの下の既定の場所ではない特定の場所に格納する必要があります。どうすれば変更できますか?**

`LiveUnitTesting_BuildRoot` ユーザー レベル環境変数を、Live Unit Testing のビルド成果物を格納するパスに設定します。 

## <a name="test-explorer-vs-live-unit-testing-test-runs"></a>テスト エクスプローラーとLive Unit Testing のテストの実行 
**[テスト エクスプローラー] ウィンドウと Live Unit Testing では、テストの実行方法はどのように違いますか?**

いくつか違いがあります。

- **[テスト エクスプローラー]** ウィンドウからテストを実行またはデバッグすると標準バイナリが実行されますが、Live Unit Testing ではインストルメント化されたバイナリが実行されます。 インストルメント化されたバイナリをデバッグする場合、テスト メソッドに [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) メソッドの呼び出しを追加し、そのメソッドが実行されると常にデバッガーが起動されるようにすることで (Live Unit Testing によって実行される場合を含みます)、インストルメント化されたバイナリをアタッチしてデバッグできます。 しかし、ほとんどのユーザー シナリオについてインストルメンテーションが透過的で、インストルメント化されたバイナリをデバッグする必要がないようにするのが理想的です。

- Live Unit Testing ではテストを実行するための新しいアプリケーション ドメインは作成されませんが、**[テスト エクスプローラー]** ウィンドウから実行されたテストでは新しいアプリケーション ドメインが作成されます。

- Live Unit Testing では各テスト アセンブリが順番に実行されるのに対し、**[テストを並列で実行する]** ボタンを選んで **[テスト エクスプローラー]** ウィンドウから複数のテストを実行した場合は、並列に実行されます。

- Live Unit Testing でのテストの探索と実行にはバージョン 2 の `TestPlatform` が使われますが、**[テスト エクスプローラー]** ウィンドウではバージョン 1 が使われます。 ただし、ほとんどの場合違いはわかりません。

- 現在、**テスト エクスプローラー**は既定ではシングルスレッド アパートメント (STA) でテストを実行するのに対し、Live Unit Testing はマルチスレッド アパートメント (MTA) でテストを実行します。 Live Unit Testing において MSTest テストを STA で実行するには、テスト メソッドまたはそれを含むクラスを、`MSTest.STAExtensions 1.0.3-beta` NuGet パッケージに含まれる `<STATestMethod>` または `<STATestClass>` 属性で修飾します。 NUnit の場合はテスト メソッドを `<RequiresThread(ApartmentState.STA)>` 属性で修飾し、xUnit の場合は `<STAFact>` 属性で修飾します。

## <a name="exclude-tests"></a>テストの除外
**Live Unit Testing からテストを除外するにはどうすればよいですか?**

ユーザー固有の設定については、「[Visual Studio 2017 での Live Unit Testing](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods)」記事の「テスト プロジェクトとテスト メソッドを含めるか除外する」セクションをご覧ください。 テストを含めるまたは除外すると、特定の編集セッションに対して特定のテスト セットを実行したい場合、または個人設定を維持したい場合に便利です。
 
ソリューション固有の設定では、<xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> 属性をプログラムで適用することにより、Live Unit Testing によるインストルメント化からメソッド、プロパティ、クラス、構造体を除外できます。 さらに、プロジェクト ファイルで `<ExcludeFromCodeCoverage>` プロパティを `true` に設定して、プロジェクト全体をインストルメント化から除外することもできます。 それでも Live Unit Testing はインストルメント化されていないテストを実行しますが、カバレッジは視覚化されません。

`Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` が現在のアプリケーション ドメインに読み込まれているかどうかを確認し、理由に基づいてテストを無効にすることもできます。 たとえば、xUnit では次のような処理を行うことができます。

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

## <a name="win32-pe-headers"></a>Win32 PE ヘッダー
**Live Unit Testing によってビルドされたインストルメント化されたアセンブリでは Win32 PE ヘッダーが異なるのはなぜですか?**

この問題は解消されており、Visual Studio 2017 バージョン 15.3 では発生しません。 このバージョンの Visual Studio にアップグレードしてください。

以前のバージョンの Visual Studio 2017 の場合、Live Unit Testing のビルドで次の Win32 PE ヘッダー データの埋め込みが失敗する既知のバグがあります。

- ファイル バージョン (コードで @System.Reflection.AssemblyFileVersionAttribute によって指定)。

- Win32 アイコン (コマンド ラインで `/win32icon:` によって指定)。

- Win32 マニフェスト (コマンド ラインで `/win32manifest:` によって指定)。

これらの値に依存するテストは、Live Unit Testing で実行すると失敗する場合があります。

## <a name="continuous-builds"></a>連続的なビルド
**編集を行わなかった場合でも Live Unit Testing で常にソリューションがビルドされるのはなぜですか?**

編集を行っていなくても、ソリューションのビルド プロセスによってソリューション自体の一部であるソース コードが生成され、ビルド ターゲット ファイルにおいて適切な入力と出力が指定されていない場合は、ソリューションがビルドされる場合があります。 MSBuild が適切な最新状態チェックを実行し、新しいビルドが必要かどうかを判断できるように、ターゲットに入力と出力のリストを提供する必要があります。

Live Unit Testing は、ソース ファイルが変更されたことを検出すると常に、ビルドを開始します。 ソリューションのビルドでソース ファイルが生成されるので、Live Unit Testing は無限ビルド ループになります。 ただし、Live Unit Testing が (前のビルドで新しく生成されたソース ファイルを検出した後) 2 回目のビルドを開始するときに、ターゲットの入力と出力を調べる場合は、入力と出力のチェックですべてが最新であることが示されるため、ビルド ループから抜け出します。  

## <a name="lightweight-solution-load"></a>ライトウェイト ソリューション ロード
**ライトウェイト ソリューション ロード機能では Live Unit Testing はどのように動作しますか?**

Live Unit Testing は現在のところ、ライトウェイト ソリューション ロード機能とうまく連動しません。 テスト プロジェクトを少なくとも 1 つ読み込まないと作動しません。 プロジェクトを読み込むまで正常に作動しない理由は、Live Unit Testing は 1 つ以上のテスト プロジェクトを利用しなければ、読み込まれるテスト アダプター (MSTest、xUnit、NUnit) を参照できないことにあります。

> [!NOTE]
> Visual Studio 2017 バージョン 15.5 以降では、ライトウェイト ソリューション ロードを使用できなくなりました。 Visual Studio 2017 バージョン 15.5 以降の場合、マネージド コードを含む大規模なソリューションで、ライトウェイト ソリューション ロードなしでも以前よりはるかに速く読み込むことができます。

## <a name="new-process-coverage"></a>新しいプロセスのカバレッジ
**Live Unit Testing がテストによって作成された新しいプロセスからカバレッジをキャプチャしないのはなぜですか?**

これは既知の問題であり、Visual Studio 2017 の今後の更新プログラムで修正されるはずです。

## <a name="including-or-excluding-tests-not-working"></a>テストの追加または除外が機能しない
**Live Test セットにテストを含めたり、セットからテストを除外した後、何も行われないのはなぜですか?**

この問題は解消されており、Visual Studio 2017 バージョン 15.3 では発生しません。 このバージョンの Visual Studio にアップグレードしてください。

この問題は、以前のバージョンの Visual Studio 2017 で確認されています。 この問題を回避するには、テストを含めたり除外したりした後、任意のファイルを編集する必要があります。 

## <a name="editor-icons"></a>エディターのアイコン
**出力ウィンドウのメッセージでは Live Unit Testing が実行しているようなのに、エディターにアイコンが表示されないのはなぜですか?**

Live Unit Testing が動作しているアセンブリが何らかの理由でインストルメント化されていない場合に、エディターにアイコンが表示されない場合があります。 たとえば、Live Unit Testing は `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` を設定するプロジェクトと互換性がありません。 この場合、Live Unit Testing を動作させるには、ビルド プロセスを更新してこの設定を削除する、または `true` に変更する必要があります。 

## <a name="capture-logs"></a>ログのキャプチャ
**ファイル バグ レポートに詳細なログを収集するにはどうすればよいですか?**

詳細なログを収集するにはいくつかの方法があります。

- **[ツール]** > **[オプション]** > **[Live Unit Testing]** の順に移動し、ログ オプションを **[詳細]** に変更します。 詳細ログにより、より詳細なログが **[出力]** ウィンドウに表示されます。

- `LiveUnitTesting_BuildLog` ユーザー環境変数に、MSBuild ログのキャプチャに使うファイルの名前を設定します。 このようにすると、Live Unit Testing のビルドからの詳細な MSBuild ログ メッセージを、そのファイルから取得できます。

- `LiveUnitTesting_TestPlatformLog` ユーザー環境変数を `1` に設定して、テスト プラットフォームのログをキャプチャします。 このようにすると、Live Unit Testing の実行からの詳細なテスト プラットフォームのログ メッセージを `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` から取得できます。

- `VS_UTE_DIAGNOSTICS` という名前のユーザー レベル環境変数を作成し、1 (または任意の値) に設定して、Visual Studio を再起動します。 Visual Studio の **[出力 - テスト]** タブに多くのログが表示されるようになります。

## <a name="see-also"></a>関連項目

- [ライブ単体テスト](live-unit-testing.md)
