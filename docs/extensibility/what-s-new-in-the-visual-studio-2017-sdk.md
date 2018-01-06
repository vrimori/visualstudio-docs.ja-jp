---
title: "どのような &#39; Visual Studio 2017 SDK の |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f6b27e60f1cc47b236ed2d3516313537a6121be5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>どのような &#39; s New in Visual Studio 2017 SDK

Visual Studio SDK では、Visual Studio 2017 の新規および更新の機能が次があります。

## <a name="vsix-v3-format"></a>VSIX v3 形式

Visual Studio 2017 の新しい軽量のインストールをサポートするためには、VSIX 拡張機能マニフェスト形式がバージョン 3 (VSIX v3) に更新されました。

新しい形式では、サポートがあります。

* 検出され、VSIXInstaller によってインストールの前提条件を明示的に宣言します。
* 拡張機能のインストールで Ngen'ing アセンブリ。
* 通常の拡張機能のルートの外部の資産をインストールします。

これらの変更方法については、次のトピックを参照してください。

* [2017 年 1 の拡張機能への変更](breaking-changes-2017.md)
* [VSIX v3 での Ngen のサポート](ngen-support.md)
* [拡張機能フォルダー外でのインストール](set-install-root.md)
* [よく寄せられる質問の Visual Studio 2017 機能拡張](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Visual Studio 2017 に移行する機能拡張プロジェクト

Visual Studio 2017 に、機能拡張プロジェクトおよび独自の VSIX マニフェストを更新する方法については、次を参照してください。[する方法: Visual Studio 2017 を機能拡張プロジェクトを移行](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)です。

## <a name="custom-project-and-item-templates"></a>カスタム プロジェクトと項目テンプレート

Visual Studio 2017 以降、カスタム プロジェクトと項目テンプレートのスキャンが不要になった実行されます。 代わりに、拡張機能では、これらのテンプレートのインストール場所を記述するテンプレート マニフェスト ファイルを提供する必要があります。 Visual Studio 2017 を使用するには、VSIX 拡張機能を更新します。 MSI を使用して、拡張機能を展開する場合は、テンプレート マニフェスト ファイルを手動で生成する必要があります。 詳細については、次を参照してください。[をアップグレードするカスタムのプロジェクトと項目テンプレート Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)です。 テンプレート マニフェスト スキーマについては、「 [Visual Studio テンプレート マニフェスト スキーマ リファレンス](../extensibility/visual-studio-template-manifest-schema-reference.md)です。

## <a name="updated-extension-performance-guidelines"></a>更新された拡張機能のパフォーマンスに関するガイドライン

新しい[する方法: 拡張機能のパフォーマンスの診断](how-to-diagnose-extension-performance.md)トピックの「[を管理する Vspackage](managing-vspackages.md)を検出して、Visual Studio 拡張機能への影響を分析する方法を示します。 スタートアップとソリューションを読み込む時間。
