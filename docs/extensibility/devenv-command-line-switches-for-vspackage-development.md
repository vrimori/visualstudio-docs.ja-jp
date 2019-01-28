---
title: VSPackage 開発の Devenv コマンド ライン スイッチ |Microsoft Docs
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89114689f933f3b09aac1d7ffcec109e81f631ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970553"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 開発の Devenv コマンド ライン スイッチ

Visual Studio により、開発者は実行時に、コマンドラインからタスクを自動化する`devenv.exe`、Visual Studio IDE を起動するファイル。  

 タスクは次のとおりです。  

- IDE の外部から定義済みの構成でアプリケーションを展開します。  

- 自動的にプリセットを使用してプロジェクトをビルドする設定を作成するかのデバッグ構成。  

- IDE の外部からすべての特定の構成で IDE を読み込んでいます。 起動すると、IDE をカスタマイズすることもできます。  

## <a name="guidelines-for-switches"></a>スイッチのガイドライン

Visual Studio のドキュメントには、ユーザー レベルがについて説明します`devenv`コマンド ライン スイッチ。 詳細については、次を参照してください。 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)します。 `devenv`ツールには、VSPackage の開発、展開、およびデバッグで便利な追加のコマンド ライン スイッチもサポートしています。  

| コマンド ライン スイッチ | 説明 |
|---------------------| - |
| `/ResetSkipPkgs` | 問題の Vspackage の読み込みを回避するために必要な Visual Studio を起動し、ユーザーによって追加されているすべてのスキップ読み込みオプションをクリアします。 SkipLoading タグの存在は、VSPackage の読み込みを無効にします。 VSPackage の読み込みを再度有効にタグをクリアします。<br /><br /> このスイッチは引数を取りません。 |
| `/RootSuffix` | 別の場所を使用して Visual Studio を起動します。 Visual Studio SDK インストーラーによって作成されたショートカットでは、次のコマンドを実行します。<br /><br /> `devenv /RootSuffix exp`<br /><br /> この場合、`exp`特定のサフィックスを使用する位置を識別します (たとえば、`10.0Exp`の代わりに`10.0`)。 実験用インスタンスを使用してコードを記述する Visual Studio のインスタンスから個別に VSPackage をデバッグすることができます。<br /><br /> このスイッチは、VSRegEx.exe を使用して作成した場所を識別する任意の文字列を実行できます。 詳細については、次を参照してください。 [、実験用インスタンス](../extensibility/the-experimental-instance.md)します。 |
| `/SafeMode` | 既定の IDE とサービスのみを読み込み、セーフ モードでは、Visual Studio を起動します。 `/SafeMode`スイッチすべて vspackage サード パーティ製を読み込み、Visual Studio の起動時、実行を安定したことを確認します。<br /><br /> このスイッチは引数を取りません。 |
| `/Setup` | Visual Studio でメニューのツールバー、およびコマンド グループの使用可能なすべての VSPackages を記述したリソース メタデータのマージを強制します。 このコマンドは、管理者としてのみ実行できます。 <br /><br /> このスイッチは引数を取りません。 `devenv /Setup` コマンドは、一般的にインストール処理の最後の手順として提示されます。 使用、`/Setup`スイッチは、IDE を起動しません。|
| `/Splash` | 画面で、通常どおりと、メッセージが表示されますが、主要な IDE を表示する前にボックスに、Visual Studio のスプラッシュを示しています。 メッセージ ボックスを使用して、(たとえば、VSPackage の製品 アイコンをチェックする場合)、スプラッシュ スクリーンを調査できます。<br /><br /> このスイッチは引数を取りません。 |

## <a name="see-also"></a>関連項目

- [コマンド ライン スイッチを追加します。](../extensibility/adding-command-line-switches.md)
- [Devenv コマンドライン スイッチ](../ide/reference/devenv-command-line-switches.md)