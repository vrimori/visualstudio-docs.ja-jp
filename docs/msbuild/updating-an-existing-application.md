# <a name="updating-an-existing-application-for-msbuild-15"></a>MSBuild 15 用に既存のアプリケーションを更新する

15.0 より前のバージョンの MSBuild では、MSBuild はグローバル アセンブリ キャッシュ (GAC) から読み込まれ、MSBuild の拡張機能はレジストリにインストールされました。 これにより、すべてのアプリケーションは同じバージョンの MSBuild を使用し、同じツールセットにアクセスできましたが、異なるバージョンの Visual Studio を side-by-side インストールすることはできませんでした。

より速くて小さい side-by-side インストールをサポートするため、Visual Studio 2017 では、MSBuild は GAC に配置されず、レジストリは変更されなくなりました。 残念ながら、これは、MSBuild API を使ってプロジェクトを評価またはビルドしたいアプリケーションは、Visual Studio のインストールに暗黙的に依存できないことを意味します。

## <a name="using-msbuild-from-visual-studio"></a>Visual Studio からの MSBuild の使用

アプリケーションからのプログラムによるビルドを、Visual Studio または MSBuild.exe 内で実行されるビルドと一致させるには、Visual Studio から MSBuild アセンブリを読み込み、Visual Studio 内で使用可能な SDK を使用します。 Microsoft.Build.Locator NuGet パッケージを使うと、これを簡略化できます。

## <a name="using-microsoftbuildlocator"></a>Microsoft.Build.Locator の使用

アプリケーションと共に `Microsoft.Build.Locator.dll` を再配布する場合は、他の MSBuild アセンブリを配布する必要はありません。

MSBuild 15 およびロケーター API を使用するようにプロジェクトを更新するには、以下で説明するいくつかの変更をプロジェクトで行う必要があります。 プロジェクトの更新に必要な変更の例については、[MSBuildLocator リポジトリのプロジェクトの例に対して行われたコミット](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15)をご覧ください。

### <a name="change-msbuild-references"></a>MSBuild の参照を変更する

MSBuild が中央の場所から確実に読み込まれるようにするには、アプリケーションと共にそのアセンブリを配布してはなりません。

中央の場所から MSBuild が読み込まれないようにするためにプロジェクトを変更するメカニズムは、MSBuild を参照する方法によって異なります。

#### <a name="using-nuget-packages-preferred"></a>NuGet パッケージの使用 (推奨)

以下の手順では、[`PackageReference` スタイルの NuGet の参照](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files)を使用しているものとします。

NuGet パッケージから MSBuild アセンブリを参照するようにプロジェクト ファイルを変更します。 `ExcludeAssets=runtime` を指定して、アセンブリはビルド時にのみ必要であり、出力ディレクトリにコピーしてはならないことを、NuGet に伝えます。

MSBuild パッケージのメジャー バージョンとマイナー バージョンは、サポートする予定の Visual Studio の最小バージョン以下でなければなりません。 任意のバージョンの Visual Studio 2017 をサポートする場合は、パッケージ バージョン `15.1.548` を参照します。

たとえば、次の XML を使用できます。

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="using-extension-assemblies"></a>拡張機能アセンブリの使用

NuGet パッケージを使用できない場合は、Visual Studio と共に配布される MSBuild アセンブリを参照することができます。 MSBuild を直接参照する場合は、`Copy Local` を `False` に設定することで、MSBuild が出力ディレクトリにコピーされないようにします。 プロジェクト ファイルでは次のようになります。

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>バインド リダイレクト

Microsoft.Build.Locator パッケージを参照すると、アプリケーションは自動的に、MSBuild アセンブリのすべてのバージョンで必要なバージョン `15.1.0.0` へのバインド リダイレクトを使用するようになります。

### <a name="ensure-output-clean"></a>出力をクリーンにする

プロジェクトをビルドし、出力ディレクトリを調べて、出力ディレクトリに `Microsoft.Build.*.dll` アセンブリ (次の手順で追加される `Microsoft.Build.Locator.dll` 以外) が含まれないことを確認します。

### <a name="add-package-reference"></a>パッケージ参照を追加する

NuGet パッケージの参照を [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/) に追加します。

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>MSBuild を呼び出す前にインスタンスを登録する

MSBuild を使用するメソッドを呼び出す前に、ロケーター API への呼び出しを追加します。

これを行う最も簡単な方法:

```c#
MSBuildLocator.RegisterDefaults();
```

上の呼び出しをアプリケーションのスタートアップ コードに追加します。

MSBuild の読み込みを細かく制御したい場合は、`MSBuildLocator.RegisterInstance()` に渡す `MSBuildLocator.QueryVisualStudioInstances()` の結果を手動で選択できますが、これは通常であれば必要ありません。
