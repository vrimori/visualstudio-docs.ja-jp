---
title: MSBuild 15 の新機能 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a8eae3b6131ca147149324477119df1be55ba35
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154019"
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15 の新機能

MSBuild は現在 [.NET Core SDK](https://www.microsoft.com/net/download/core) の一部として利用でき、Windows、macOS、Linux で .NET Core プロジェクトをビルドできます。

## <a name="changed-path"></a>変更されたパス

 MSBuild は Visual Studio の各バージョンのフォルダーにインストールされます。 例: *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*。 次の PowerShell モジュールを使用して MSBuild を検索することもできます: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell)。

 MSBuild は、グローバル アセンブリ キャッシュにインストールされなくなりました。 MSBuild をプログラムで参照するには、NuGet パッケージを使用します。

## <a name="changed-properties"></a>変更されたプロパティ

 新しいバージョン番号に伴い、次の MSBuild プロパティが更新されました。

- `MSBuildToolsVersion`: このバージョンのツールでは 15.0 になります。 アセンブリのバージョンは 15.1.0.0 です。

- `MSBuildToolsPath`: 固定の場所はなくなりました。 既定では、Visual Studio のインストール場所に相対的な *MSBuild\15.0\Bin* フォルダーにありますが、Visual Studio のインストール場所はインストール時に変更できます。

- `ToolsVersion`: 値はレジストリで設定されなくなりました。

- `SDK35ToolsPath` と `SDK40ToolsPath`: これらのプロパティは、このバージョンの Visual Studio に含まれている .NET Framework SDK を指しています (たとえば、4.X ツールの場合は 10.0A など)。

## <a name="updates"></a>更新
- [Project 要素](../msbuild/project-element-msbuild.md)には新しい `SDK` 属性があります。 `Xmlns` 属性も省略できます。 `SDK` 属性の詳細については、「[方法: MSBuild プロジェクト SDK の参照](../msbuild/how-to-use-project-sdk.md)」、「[パッケージ、メタパッケージ、フレームワーク](/dotnet/core/packages)」および「[.NET Core の csproj 形式に追加されたもの](/dotnet/core/tools/csproj)」を参照してください。
- ターゲットの外部の [Item 要素](../msbuild/item-element-msbuild.md)には新しい `Update` 属性があります。 また、`Remove` 属性に対する制限も排除されました。
- *Directory.Build.props* は、ディレクトリの下のプロジェクトをカスタマイズできるようにする、ユーザー定義のファイルです。 `ImportDirectoryBuildTargets` プロパティを **false** に設定しない限り、このファイルは *Microsoft.Common.props* から自動的にインポートされます。 *Directory.Build.targets* は *Microsoft.Common.targets* によってインポートされます。
- 現行の属性リストと競合しない名前のメタデータを任意で属性として表現できます。 詳しくは、「[Item 要素](../msbuild/item-element-msbuild.md)」をご覧ください。

## <a name="new-property-functions"></a>新しいプロパティ関数

- `EnsureTrailingSlash` は、まだ存在しない場合に末尾のスラッシュをパスに追加します。
- `NormalizePath` はパス要素を結合し、出力文字列に現在のオペレーティング システムの適切なディレクトリ区切り文字が含まれることを確認します。
- `NormalizeDirectory` はパス要素を結合し、末尾のスラッシュを確認し、出力文字列に現在のオペレーティング システムの適切なディレクトリ区切り文字が含まれることを確認します。
- `GetPathOfFileAbove` は、直前のファイルのパスを返します。 その機能は `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />` の呼び出しと同じです

## <a name="see-also"></a>関連項目
[MSBuild](../msbuild/msbuild.md)
