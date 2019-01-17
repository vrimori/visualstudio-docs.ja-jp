---
title: 既存のアプリケーションの MSBuild 15 への更新 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0487ee8cdbb89b7c781cb13225d209d840eda134
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836872"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>既存のアプリケーションを MSBuild 15 用に更新する

15.0 より前のバージョンの MSBuild では、MSBuild はグローバル アセンブリ キャッシュ (GAC) から読み込まれ、MSBuild の拡張機能はレジストリにインストールされました。 これにより、すべてのアプリケーションは同じバージョンの MSBuild を使用し、同じツールセットにアクセスできましたが、異なるバージョンの Visual Studio を side-by-side インストールすることはできませんでした。

より速くて小さい side-by-side インストールをサポートするため、Visual Studio 2017 では、MSBuild は GAC に配置されず、レジストリは変更されなくなりました。 残念ながら、これは、MSBuild API を使ってプロジェクトを評価またはビルドしたいアプリケーションは、Visual Studio のインストールに暗黙的に依存できないことを意味します。

## <a name="use-msbuild-from-visual-studio"></a>Visual Studio から MSBuild を使用する

アプリケーションからのプログラムによるビルドを、Visual Studio または *MSBuild.exe* 内で実行されるビルドと一致させるには、Visual Studio から MSBuild アセンブリを読み込み、Visual Studio 内で使用可能な SDK を使用します。 Microsoft.Build.Locator NuGet パッケージは、このプロセスを簡略化します。

## <a name="use-microsoftbuildlocator"></a>Microsoft.Build.Locator を使用する

アプリケーションと共に *Microsoft.Build.Locator.dll* を再配布する場合は、他の MSBuild アセンブリを配布する必要はありません。

MSBuild 15 およびロケーター API を使用するようにプロジェクトを更新するには、以下で説明するいくつかの変更をプロジェクトで行う必要があります。 プロジェクトの更新に必要な変更の例については、[MSBuildLocator リポジトリのプロジェクトの例に対して行われたコミット](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15)をご覧ください。

### <a name="change-msbuild-references"></a>MSBuild の参照を変更する

MSBuild が中央の場所から確実に読み込まれるようにするには、アプリケーションと共にそのアセンブリを配布してはなりません。

中央の場所から MSBuild が読み込まれないようにするためにプロジェクトを変更するメカニズムは、MSBuild を参照する方法によって異なります。

#### <a name="use-nuget-packages-preferred"></a>NuGet パッケージを使用する (推奨)

以下の手順では、[PackageReference スタイルの NuGet の参照](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files)を使用しているものとします。

NuGet パッケージから MSBuild アセンブリを参照するようにプロジェクト ファイルを変更します。 `ExcludeAssets=runtime` を指定して、アセンブリはビルド時にのみ必要であり、出力ディレクトリにコピーしてはならないことを、NuGet に伝えます。

MSBuild パッケージのメジャー バージョンとマイナー バージョンは、サポートする予定の Visual Studio の最小バージョン以下でなければなりません。 任意のバージョンの Visual Studio 2017 をサポートする場合は、パッケージ バージョン `15.1.548` を参照します。

たとえば、次の XML を使用できます。

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>拡張機能アセンブリを使用する

NuGet パッケージを使用できない場合は、Visual Studio と共に配布される MSBuild アセンブリを参照することができます。 MSBuild を直接参照する場合は、`Copy Local` を `False` に設定することで、MSBuild が出力ディレクトリにコピーされないようにします。 プロジェクト ファイルで、この設定は次のコードのようになります。

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>バインド リダイレクト

Microsoft.Build.Locator パッケージを参照すると、アプリケーションは、MSBuild アセンブリのすべてのバージョンで必要なバージョン `15.1.0.0` へのバインド リダイレクトを自動的に使用するようになります。

### <a name="ensure-output-is-clean"></a>出力をクリーンにする

プロジェクトをビルドし、出力ディレクトリを調べて、出力ディレクトリに *Microsoft.Build.\*.dll* アセンブリ (次の手順で追加される *Microsoft.Build.Locator.dll* 以外) が含まれないことを確認します。

### <a name="add-package-reference"></a>パッケージ参照を追加する

NuGet パッケージの参照を [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/) に追加します。

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>MSBuild を呼び出す前にインスタンスを登録する

MSBuild を使用するメソッドを呼び出す前に、ロケーター API への呼び出しを追加します。

Locator API に呼び出しを追加する最も簡単な方法は、

```csharp
MSBuildLocator.RegisterDefaults();
```

上の呼び出しをアプリケーションのスタートアップ コードに追加します。

MSBuild の読み込みを細かく制御したい場合は、`MSBuildLocator.RegisterInstance()` に渡す `MSBuildLocator.QueryVisualStudioInstances()` の結果を手動で選択できますが、これは通常であれば必要ありません。
