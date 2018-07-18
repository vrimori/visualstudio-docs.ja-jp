---
title: Visual Studio の検索 |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/21/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed6125c69b9068ebfb3d776ccbefaf88043f83a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138614"
---
# <a name="locating-visual-studio"></a>Visual Studio の検索

Visual Studio 2017 から始めて、同じバージョンまたは偶数のエディションの複数のインスタンスをインストールできます。 これは、以前のインストールを維持しながら、プライマリの開発用コンピューターの新しい機能をプレビューする場合に便利です。 これらの変更のためインスタンスを検索する際、1 つの環境の変数またはレジストリの値はありません。 代わりに、使用することができます、 [COM クエリ API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx)拡張機能に関連する条件に基づいてインスタンスを検索します。

これは、ネイティブおよびマネージ コードの使用可能な NuGet パッケージを高速、読み取り専用の API です。

| コード | Package |
| ---- | --- |
| ネイティブ | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| マネージ | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

指定されたパスまたは現在のプロセスでは、1 つのインスタンスを検索したり、すべてのインスタンスを列挙できます。 参照してください[サンプル](https://github.com/Microsoft/vs-setup-samples)Visual Studio を検索する方法の例については完了します。

## <a name="tools"></a>ツール

ビルド環境、PowerShell スクリプト、インストーラー、およびより多くのシナリオでは、Visual Studio およびその他のツールを検索、オープン ソース ツールを直接使用したり、独自のスクリプトと共に再配布の数があります。

| プロジェクト | 説明 |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | 単一ファイル リリースまたはプレリリース版、製品がインストールされている場合、およびどのワークロードがインストールされているなどの条件を満たすインスタンスを検索するネイティブ実行可能ファイル。 以下の情報が返されますを Visual Studio 2017 以降も 2010 以降、Visual Studio の検索もサポートします。 参照してください、 [wiki](https://github.com/Microsoft/vswhere/wiki)例についてはします。 |
| [VSSetup コマンドレット](https://github.com/Microsoft/vssetup.powershell) | サポートされている PowerShell コマンドレットと同じ条件に基づいてインスタンスを検索に使用できるオブジェクトとしての豊富な情報を返す 2.0 と新しい_vswhere_インスタンスに関するさらに多くのプロパティを検出するとします。 参照してください、 [wiki](https://github.com/Microsoft/vssetup.powershell/wiki)例についてはします。 |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | 自動的に検出_VSIXInstaller_インストールをコマンドラインに渡しますと、 _*.vsix_ファイル。 これは、クエリ Api の直接サポートはありません。 インストーラーに役に立ちます。 参照してください、 [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki)例についてはします。 |

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 セットアップへの変更](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
