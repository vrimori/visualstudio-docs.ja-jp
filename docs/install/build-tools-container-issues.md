---
title: コンテナーの既知の問題
description: Windows コンテナーに Visual Studio Build Tools 2017 をインストールするときに発生する可能性がある既知の問題について説明します。
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d817b7d45c23e813a8d3f80e2b74ea860bb8a3cf
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307766"
---
# <a name="known-issues-for-containers"></a>コンテナーの既知の問題

Docker コンテナーに Visual Studio をインストールする場合、いくつかの問題があります。

## <a name="windows-container"></a>Windows コンテナー

Windows コンテナーに Visual Studio Build Tools 2017 をインストールすると、以下の既知の問題が発生します。

* イメージ microsoft/windowsservercore:10.0.14393.1593 に基づいて Visual Studio をコンテナーにインストールできません。 10.0.14393 より前または後の Windows バージョンでタグ付けされたイメージでは動作します。
* 10.0.14393 以前の Windows SDK バージョンをインストールすることはできません。 一部のパッケージはインストールに失敗し、そのようなパッケージに依存するワークロードは動作しません。
* イメージを構築するときに `-m 2GB` (またはそれ以上) を渡します。 一部のワークロードではインストール時の既定の 1 GB よりも多くのメモリを必要とします。
* Docker で既定の 20 GB よりも多くのディスクを使用するように構成します。
* コマンド ラインで `--norestart` を渡します。 現時点では、コンテナー内から Windows コンテナーを再起動しようとすると、ホストに `ERROR_TOO_MANY_OPEN_FILES` が返されます。
* microsoft/windowsservercore に直接基づくイメージの場合は、.NET Framework が正しくインストールされない可能性があり、インストール エラーは示されていません。 インストールが完了した後、マネージド コードが実行しない可能性があります。 代わりに、イメージを [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) 以降に基づくようにします。 たとえば、MSBuild でビルドすると、次のようなエラーが表示される可能性があります。

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): エラー MSB6003:指定されたタスク実行可能ファイル "csc.exe" を実行できませんでした。 ファイルまたはアセンブリ 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'、またはその依存関係の 1 つが読み込めませんでした。 指定されたファイルが見つかりません。

* Visual Studio 2017 バージョン 15.8 以前 (すべての製品) を、mcr<span></span>.microsoft.com/windows/servercore:1809 以降にインストールすることはできません。 詳細については、「 https://aka.ms/setup/containers/servercore1809」を参照してください。

## <a name="build-tools-container"></a>ビルド ツール コンテナー

ビルド ツール コンテナーを使用すると、以下の既知の問題が発生する場合があります。 問題が修正されているどうか、その他の既知の問題があるかどうかについては、 https://developercommunity.visualstudio.com を参照してください。

* IntelliTrace はコンテナー内の[一部のシナリオ](https://github.com/Microsoft/vstest/issues/940)では動作しない場合があります。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [コンテナーにビルド ツールをインストールする](build-tools-container.md)
* [コンテナーの高度な例](advanced-build-tools-container.md)
* [Visual Studio Build Tools 2017 のワークロード ID とコンポーネント ID](workload-component-id-vs-build-tools.md)
