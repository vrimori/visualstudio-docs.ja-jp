---
title: どのような&#39;、Visual Studio 2017 SDK の新 |Microsoft Docs
ms.custom: ''
ms.date: 10/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f2a003bc19764aa07262552d3f0cc41316835b6
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566909"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>どのような&#39;s、Visual Studio 2017 SDK の新機能

Visual Studio SDK では、Visual Studio 2017 の新規および更新の機能が次があります。

## <a name="vsix-v3-format"></a>VSIX v3 形式

Visual Studio 2017 の新しい軽量インストールをサポートするためには、VSIX 拡張機能マニフェスト形式がバージョン 3 (VSIX v3) に更新されました。

新しい形式はサポートしています。

* 検出され、VSIXInstaller によってインストールの前提条件を明示的に宣言します。
* 拡張機能のインストール上のアセンブリを Ngen します。
* 通常の拡張機能のルート以外の資産をインストールします。

これらの変更の詳細については、次のトピックを参照してください。

* [2017 の拡張機能への変更](breaking-changes-2017.md)
* [VSIX v3 での Ngen のサポート](ngen-support.md)
* [拡張機能フォルダー外にインストールします。](set-install-root.md)
* [よく寄せられる質問の Visual Studio 2017 の機能拡張](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>拡張機能プロジェクトを Visual Studio 2017 に移行します。

Visual Studio 2017 の機能拡張プロジェクトと独自の VSIX マニフェストを更新する方法については、次を参照してください。[方法: 機能拡張プロジェクトを Visual Studio 2017 に移行](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)します。

## <a name="custom-project-and-item-templates"></a>カスタム プロジェクトと項目テンプレート

Visual Studio 2017 以降、カスタム プロジェクトと項目テンプレートのスキャンは不要になった実行されます。 代わりに、拡張機能では、これらのテンプレートのインストール場所を記述するテンプレート マニフェスト ファイルを提供する必要があります。 Visual Studio 2017 を使用して、VSIX 拡張機能を更新することができます。 MSI を使用して、拡張機能をデプロイする場合は、手動でテンプレート マニフェスト ファイルを生成する必要があります。 詳細については、次を参照してください。[カスタム プロジェクトと項目テンプレートを Visual Studio 2017 のアップグレード](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)します。 テンプレート マニフェスト スキーマについては[Visual Studio テンプレート マニフェスト スキーマ参照](../extensibility/visual-studio-template-manifest-schema-reference.md)します。

## <a name="updated-extension-performance-guidelines"></a>更新された拡張機能のパフォーマンスに関するガイドライン

新しいがある[方法: 拡張機能のパフォーマンス診断](how-to-diagnose-extension-performance.md)記事[管理 Vspackage](managing-vspackages.md)を検出し、Visual Studio 拡張機能への影響を分析する方法について説明起動とソリューション読み込み時間。
